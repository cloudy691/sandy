---
name: xaml-converter
description: Converts HTML/CSS/React/Tailwind designs into WPF XAML markup. Helps bridge modern web UI designs into native Windows desktop applications. Supports migration from web frameworks (Bootstrap, Material UI, Tailwind) into WPF equivalents.
---

# XAML Converter Skill

Convert modern web UI designs (HTML, CSS, React, Tailwind, Bootstrap) into equivalent WPF XAML markup. Useful when porting web designs to native Windows desktop.

## Conversion Mapping

### Layout

| Web | WPF |
|---|---|
| `<div>` | `<Grid>`, `<StackPanel>`, `<DockPanel>` |
| Flexbox | `<StackPanel Orientation="..."/>` or `<DockPanel>` |
| CSS Grid | `<Grid>` with `RowDefinitions`/`ColumnDefinitions` |
| Position absolute | `<Canvas>` |

### Typography

| Web | WPF |
|---|---|
| `font-size: 16px` | `FontSize="16"` |
| `font-weight: 600` | `FontWeight="SemiBold"` |
| `color: #1a1a1a` | `Foreground="#1a1a1a"` |
| `text-align: center` | `HorizontalAlignment="Center"` |

### Spacing

| Web | WPF |
|---|---|
| `padding: 8px` | `Padding="8"` |
| `margin: 16px` | `Margin="16"` |
| `gap: 8px` | Use Grid spacing or item-by-item margin |

### Borders & Backgrounds

| Web | WPF |
|---|---|
| `border-radius: 4px` | `CornerRadius="4"` |
| `box-shadow: 0 2px 4px rgba(0,0,0,0.1)` | `<Border.Effect><DropShadowEffect BlurRadius="4" ShadowDepth="2" Opacity="0.1"/></Border.Effect>` |
| `background: #f5f5f5` | `Background="#F5F5F5"` |
| Linear gradient | `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1">` |

### Components

| Web | WPF |
|---|---|
| `<button>` | `<Button>` |
| `<input type="text">` | `<TextBox>` |
| `<select>` | `<ComboBox>` |
| `<input type="checkbox">` | `<CheckBox>` |
| `<input type="radio">` | `<RadioButton>` |
| `<textarea>` | `<TextBox AcceptsReturn="True" TextWrapping="Wrap">` |
| `<img>` | `<Image>` |
| Bootstrap card | `<Border CornerRadius="8" Background="..."><Grid>...</Grid></Border>` |

## Common Patterns

### Centered Content

HTML:
```html
<div style="display: flex; justify-content: center; align-items: center; height: 100vh;">
  <div class="card">...</div>
</div>
```

WPF:
```xml
<Grid HorizontalAlignment="Stretch" VerticalAlignment="Stretch">
  <Border HorizontalAlignment="Center" VerticalAlignment="Center"
          Background="White" CornerRadius="8" Padding="24">
    <!-- card content -->
  </Border>
</Grid>
```

### Responsive Grid

HTML:
```html
<div class="grid grid-cols-3 gap-4">
  <div>1</div>
  <div>2</div>
  <div>3</div>
</div>
```

WPF:
```xml
<Grid>
  <Grid.ColumnDefinitions>
    <ColumnDefinition Width="*"/>
    <ColumnDefinition Width="*"/>
    <ColumnDefinition Width="*"/>
  </Grid.ColumnDefinitions>
  <TextBlock Grid.Column="0" Text="1"/>
  <TextBlock Grid.Column="1" Text="2"/>
  <TextBlock Grid.Column="2" Text="3"/>
</Grid>
```

## Conversion Strategy

When given a web design:

1. **Identify components** — buttons, inputs, cards, etc.
2. **Map layout structure** — flexbox → StackPanel, grid → Grid
3. **Convert visual properties** — colors, spacing, typography
4. **Map interactive elements** — onClick → Click event or Command binding
5. **Add MVVM bindings** — replace hardcoded data with ViewModel
6. **Verify accessibility** — ensure AutomationProperties

## Limitations

WPF doesn't have direct equivalents for:
- `position: sticky` (use custom behavior or just regular layout)
- CSS Grid auto-flow (manual placement required)
- Web animations (use WPF Storyboards instead — different API)
- CSS transitions (use `BeginAnimation` or styles with triggers)

Always note in the output where WPF requires manual work to match the web design.
