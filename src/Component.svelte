<script>
  import { getContext, onDestroy } from "svelte";
  import { CellTags, SuperField } from "@poirazis/supercomponents-shared";

  const { styleable, Provider, builderStore } = getContext("sdk");
  const component = getContext("component");

  const formContext = getContext("form");
  const formStepContext = getContext("form-step");
  const groupLabelPosition = getContext("field-group");
  const labelWidth = getContext("field-group-label-width");
  const groupColumns = getContext("field-group-columns");
  const groupDisabled = getContext("field-group-disabled");
  const formApi = formContext?.formApi;

  export let field = "Tags Field";
  export let fieldType = "string"; // "string" | "array"
  export let fieldString; // used if fieldType is string
  export let fieldArray; // used if fieldType is array
  export let controlType = "select";
  export let role = "formInput";

  export let label = "Tags Field";
  export let span = 6;
  export let placeholder = "Choose Tags";
  export let defaultValue;
  export let disabled;
  export let readonly;
  export let validation;
  export let invisible = false;
  export let onChange;
  export let debounced;
  export let debounceDelay = 250;
  export let helpText;

  export let icon;
  export let labelPosition = "fieldGroup";
  export let showDirty;
  export let autofocus;

  export let datasource;
  export let limit;
  export let filter;
  export let valueColumn;
  export let optionsViewMode;
  export let suggestions = false;

  let formField;
  let formStep;
  let fieldState;
  let fieldApi;
  let fieldSchema;
  let value;

  $: formStep = formStepContext ? $formStepContext || 1 : 1;
  $: labelPos =
    groupLabelPosition !== undefined && labelPosition == "fieldGroup"
      ? groupLabelPosition
      : labelPosition;

  $: field =
    fieldType === "string" && fieldString
      ? fieldString
      : fieldType === "array" && fieldArray
        ? fieldArray
        : field;

  $: formField = formApi?.registerField(
    field,
    fieldType,
    defaultValue,
    disabled,
    readonly,
    validation,
    formStep
  );

  $: unsubscribe = formField?.subscribe((value) => {
    fieldState = value?.fieldState;
    fieldApi = value?.fieldApi;
    fieldSchema = value?.fieldSchema;
  });

  $: value = sanitizedValue(fieldState?.value);
  $: error = fieldState?.error;

  $: $component.styles = {
    ...$component.styles,
    normal: {
      ...$component.styles.normal,
      display:
        invisible && !$builderStore.inBuilder
          ? "none"
          : $component.styles.normal.display,
      opacity: invisible && $builderStore.inBuilder ? 0.6 : 1,
      "grid-column": groupColumns ? `span ${span}` : "span 1",
    },
  };

  $: cellOptions = {
    disabled: disabled || groupDisabled || fieldState?.disabled,
    readonly: readonly || fieldState?.readonly,
    debounce: debounced ? debounceDelay : false,
    placeholder,
    defaultValue,
    error: fieldState?.error,
    controlType,
    suggestions,
    datasource,
    limit,
    filter,
    valueColumn,
    optionsViewMode,
    role,
    icon,
    showDirty,
  };

  const sanitizedValue = (val) => {
    if (fieldType === "array") {
      if (Array.isArray(val)) return val;
      if (typeof val === "string" && val.trim() !== "")
        return val.split(",").map((v) => v.trim());
      return [];
    } else {
      // fieldType is string
      if (Array.isArray(val)) return val;
      if (typeof val === "string" && val.trim() !== "")
        return val.split(",").map((v) => v.trim());
      return [];
    }
  };

  const handleChange = (newValue) => {
    let before = fieldState?.value;
    let sanitizedValue = newValue.filter(
      (v) => v !== null && v !== undefined && v !== ""
    );

    onChange?.({ value: sanitizedValue });

    fieldApi?.setValue(sanitizedValue);
  };

  onDestroy(() => {
    fieldApi?.deregister();
    unsubscribe?.();
  });
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
<!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
<div use:styleable={$component.styles}>
  <Provider data={{ value }} />
  <SuperField
    multirow={true}
    {labelPos}
    {labelWidth}
    {field}
    {label}
    {error}
    {helpText}
  >
    <CellTags
      {cellOptions}
      {fieldSchema}
      {value}
      {autofocus}
      on:change={(e) => handleChange(e.detail)}
    />
  </SuperField>
</div>
