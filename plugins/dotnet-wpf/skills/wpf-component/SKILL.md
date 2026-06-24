---
name: wpf-component
description: Generates production-ready WPF (Windows Presentation Foundation) UserControls and Windows with XAML + C# code-behind or MVVM pattern. Supports bindings, dependency properties, commands, styles, and accessibility. Outputs complete .NET 8 / WPF components ready to compile.
---

# WPF Component Generator Skill

Generate production-ready WPF UserControls, Windows, and custom controls with XAML and C#. Supports both code-behind and MVVM patterns.

## What to Generate

When asked for a component, output:

1. **XAML file** (`.xaml`) — UI markup
2. **Code-behind** (`.xaml.cs`) OR **ViewModel** (`.cs`) if MVVM
3. **Bindings** to ViewModel properties (for MVVM)
4. **Styles/Resources** if applicable

## Stack Defaults

- **Target Framework**: .NET 8 (or .NET 6+ if specified)
- **Language**: C# (latest features — primary constructors, collection expressions)
- **Pattern**: MVVM with `CommunityToolkit.Mvvm` (ObservableObject, RelayCommand)
- **Theming**: Modern WPF UI (or vanilla if simpler)

## Code Generation Rules

### XAML Standards
- Use proper namespacing (`xmlns:` declarations)
- Grid for layout (avoid StackPanel for top-level — use it only for stacked lists)
- Set `x:Name` for elements referenced in code-behind
- Use static resources for reusable colors, brushes, sizes
- Add comments only when non-obvious
- Always include `mc:Ignorable="d"` and `d:DesignHeight`, `d:DesignWidth`

### Accessibility (UI Automation)
- Add `AutomationProperties.Name` for any element that lacks text
- Add `AutomationProperties.HelpText` for tooltips
- Use proper labels (`Label` for `TextBox`, `Content` for `Button`)
- Support keyboard navigation (TabIndex, KeyboardNavigation.TabNavigation="Cycle")
- Support high contrast via dynamic resource references

### Dependency Properties

For custom controls, declare dependency properties with proper pattern:

```csharp
public static readonly DependencyProperty ValueProperty =
    DependencyProperty.Register(
        nameof(Value),
        typeof(string),
        typeof(MyControl),
        new FrameworkPropertyMetadata(
            string.Empty,
            FrameworkPropertyMetadataOptions.BindsTwoWayByDefault,
            OnValueChanged,
            OnValueCoerce));

public string Value
{
    get => (string)GetValue(ValueProperty);
    set => SetValue(ValueProperty, value);
}
```

### MVVM Pattern with CommunityToolkit.Mvvm

```csharp
public partial class MyViewModel : ObservableObject
{
    [ObservableProperty]
    private string _name = string.Empty;

    [RelayCommand(CanExecute = nameof(CanSave))]
    private void Save()
    {
        // ...
    }

    private bool CanSave() => !string.IsNullOrEmpty(Name);
}
```

## Component Examples

### Generate UserControl

Input: "Create a button with icon and tooltip"

Output structure:
- `MyButton.xaml` + `MyButton.xaml.cs`
- `MyButton.cs` (generic.xaml resource file)

### Generate Window

Input: "Create a settings window with sidebar navigation"

Output structure:
- `SettingsWindow.xaml` + `SettingsWindow.xaml.cs`
- `SettingsViewModel.cs` (MVVM)
- `Views/GeneralView.xaml`, `Views/AdvancedView.xaml` (sidebar pages)

### Generate Custom Control

Input: "Create a custom rating control with stars"

Output structure:
- `RatingControl.cs` (control class with DependencyProperties)
- `Themes/Generic.xaml` (default template)
- Usage example

## MVVM Best Practices to Follow

1. **No code-behind logic** beyond `InitializeComponent()` and view-specific wiring
2. **Commands** for all user actions — never expose methods directly to view
3. **Binding `UpdateSourceTrigger=PropertyChanged`** for instant feedback
4. **Async/await** in commands with proper error handling
5. **INotifyDataErrorInfo** for validation when needed
6. **IoC/DI** for services (use `Microsoft.Extensions.DependencyInjection`)

## Resources

- WPF docs: https://learn.microsoft.com/en-us/dotnet/desktop/wpf/
- MVVM toolkit: https://learn.microsoft.com/en-us/dotnet/communitytoolkit/mvvm/
- Modern WPF UI: https://github.com/ModernWpf-Community/ModernWpf
