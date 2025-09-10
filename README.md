# Super Field - Tags

A versatile tags input component for Budibase applications with multiple control types, data sources, and display modes.

## 🚀 Features

### Selection Types

- **Multiple Control Types**: Select dropdown, input select, checkboxes, switches, ordered list
- **Single/Multi Selection**: Support for both single and multiple tag selection
- **Array Field Binding**: Dedicated array field for selected values
- **Default Values**: Pre-selected tags
- **Validation**: Comprehensive selection validation

### Data Sources

- **Schema Options**: Tags from data schema
- **Data Queries**: Dynamic tags from data sources with filtering and sorting
- **Custom Options**: Manually defined tag lists
- **Real-time Updates**: Dynamic tag loading and updates
- **Large Datasets**: Efficient handling with pagination and limits

### Display Modes

- **Visual Options**: Text with colors, pill-style, or plain text display
- **Layout Control**: Column or row arrangement for tags
- **Icon Support**: Visual indicators for tags
- **Color Coding**: Color-coded tags for better UX
- **Ordered Lists**: Drag-and-drop reordering for priorities

### User Experience

- **Intuitive Controls**: Familiar selection interfaces
- **Search & Filter**: Quick tag finding in large lists
- **Event Handling**: On change events with selection context
- **Auto-focus**: Automatic focus for data entry
- **Debounced Input**: Performance optimization for large tag sets

### Advanced Features

- **Toggle All**: Select/deselect all tags (switch mode)
- **Reorder Only**: Pure ordering without selection changes
- **Conditional Logic**: Dynamic tags based on other fields
- **Button Integration**: Custom action buttons for tag management
- **Accessibility**: Full keyboard navigation and screen reader support

### Styling & Layout

- **Flexible Positioning**: Label placement tags
- **Field Modes**: Form input or inline editing
- **Size Configuration**: Adjustable component width
- **Theme Integration**: Consistent with Budibase design

## 📝 Usage Instructions

### Basic Setup

1. Add the Super Field - Tags component to your form
2. Choose tags source (schema, data, or custom)
3. Select control type (select, checkboxes, etc.)
4. Configure tag display and validation

### Advanced Configuration

- **Data Binding**: Connect to data sources with filtering
- **Display Modes**: Choose appropriate visual style
- **Validation**: Set selection requirements and limits
- **Events**: Attach actions to selection changes

### Common Use Cases

- **Category Selection**: Product categories or tags
- **Permission Settings**: User role and access selections
- **Survey Questions**: Multiple choice with multiple answers
- **Feature Selection**: Product features or add-ons
- **Priority Ranking**: Ordered preference lists

## 🔧 Configuration Options

| Setting           | Type    | Description                |
| ----------------- | ------- | -------------------------- |
| Field             | Array   | Tags field binding      |
| Label             | String  | Display label text         |
| Placeholder       | String  | Selection guidance text    |
| Default Value     | Array   | Pre-selected tags       |
| Help Text         | String  | Help/instruction text      |
| Validation        | Rules   | Selection validation rules |
| Tags Source    | Select  | Schema/Data/Custom tags |
| Control Type      | Select  | Selection interface type   |
| Direction         | Select  | Column/Row layout          |
| Autofocus         | Boolean | Auto-focus on load         |
| Debounced         | Boolean | Enable input debouncing    |
| Disabled          | Boolean | Disable tag selection   |
| Read Only         | Boolean | Read-only mode             |
| Toggle All        | Boolean | Show select all toggle     |
| Reorder Only      | Boolean | Pure reordering mode       |
| Icon              | Icon    | Visual indicator icon      |
| Field Mode        | Select  | Form or inline input style |
| Label Position    | Select  | Label placement            |
| Size              | Number  | Component width span       |
| Tags View Mode | Select  | Text/Color/Pills display   |

## 📋 Events

### On Change

Triggered when tags are selected or deselected.

**Context:**

- `value`: Array of selected tag values
- `field`: The bound field information

## 🎨 Styling

The component supports advanced styling tags:

- **Tag Display**: Multiple visual styles for tags
- **Layout Control**: Flexible arrangement tags
- **Color Integration**: Theme-consistent color usage
- **Responsive**: Mobile-optimized selection interfaces

## 🔍 Best Practices

- Choose appropriate control type for use case
- Use data sources for dynamic tag lists
- Consider mobile users for touch interfaces
- Provide clear tag labels and descriptions
- Implement validation for required selections
- Test with various tag counts and lengths
