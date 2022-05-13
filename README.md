<h1 align="center">
C# Code Conventions for Yambar Projects
</h1>

Based on [ppy](https://github.com/ppy) code rules in all our C# projects so we can write and read good code.

You can copy the [EditorConfig file](rules/csharp.editorconfig) and paste it into your project.

## Roslyn Naming Styles

### `PascalCase` for public and protected members
```ini
dotnet_naming_style.pascalcase.capitalization = pascal_case
dotnet_naming_symbols.public_members.applicable_accessibilities = public,internal,protected,protected_internal,private_protected
dotnet_naming_symbols.public_members.applicable_kinds = property,method,field,event
dotnet_naming_rule.public_members_pascalcase.severity = error
dotnet_naming_rule.public_members_pascalcase.symbols = public_members
dotnet_naming_rule.public_members_pascalcase.style = pascalcase
```

#### Usage:

```cs
// For fields/properties:
public string Name;

public string Yambar { get; set; }

protected string SuperProtected;

protected string SuperYambar { get; set; }

// For methods:
public string GetAwesomeString()
    => "yo! yambar string";

protected void TheyCannotCatchUs()
{
    // ...
}
```

### `camelCase` for private members
```ini
dotnet_naming_style.camelcase.capitalization = camel_case

dotnet_naming_symbols.private_members.applicable_accessibilities = private
dotnet_naming_symbols.private_members.applicable_kinds = property,method,field,event
dotnet_naming_rule.private_members_camelcase.severity = warning
dotnet_naming_rule.private_members_camelcase.symbols = private_members
dotnet_naming_rule.private_members_camelcase.style = camelcase

dotnet_naming_symbols.local_function.applicable_kinds = local_function
dotnet_naming_rule.local_function_camelcase.severity = warning
dotnet_naming_rule.local_function_camelcase.symbols = local_function
dotnet_naming_rule.local_function_camelcase.style = camelcase
```

#### Usage:
```cs
private string eweOwo;

private void onVelocityChange(ValueChangedEvent<float> e)
{
    // ...
}
```

### `all_lower` for private and local constants/static readonlys
```ini
dotnet_naming_style.all_lower.capitalization = all_lower
dotnet_naming_style.all_lower.word_separator = _

dotnet_naming_symbols.private_constants.applicable_accessibilities = private
dotnet_naming_symbols.private_constants.required_modifiers = const
dotnet_naming_symbols.private_constants.applicable_kinds = field
dotnet_naming_rule.private_const_all_lower.severity = warning
dotnet_naming_rule.private_const_all_lower.symbols = private_constants
dotnet_naming_rule.private_const_all_lower.style = all_lower

dotnet_naming_symbols.private_static_readonly.applicable_accessibilities = private
dotnet_naming_symbols.private_static_readonly.required_modifiers = static,readonly
dotnet_naming_symbols.private_static_readonly.applicable_kinds = field
dotnet_naming_rule.private_static_readonly_all_lower.severity = warning
dotnet_naming_rule.private_static_readonly_all_lower.symbols = private_static_readonly
dotnet_naming_rule.private_static_readonly_all_lower.style = all_lower

dotnet_naming_symbols.local_constants.applicable_kinds = local
dotnet_naming_symbols.local_constants.required_modifiers = const
dotnet_naming_rule.local_const_all_lower.severity = warning
dotnet_naming_rule.local_const_all_lower.symbols = local_constants
dotnet_naming_rule.local_const_all_lower.style = all_lower
```

#### Usage:
```cs
private readonly string super_duper_readonly_string = "yambar??";

private const string why_me = "safe string weeee";
```

### `ALL_UPPER` for non private constants/static readonlys
```ini
dotnet_naming_style.all_upper.capitalization = all_upper
dotnet_naming_style.all_upper.word_separator = _

dotnet_naming_symbols.public_constants.applicable_accessibilities = public,internal,protected,protected_internal,private_protected
dotnet_naming_symbols.public_constants.required_modifiers = const
dotnet_naming_symbols.public_constants.applicable_kinds = field
dotnet_naming_rule.public_const_all_upper.severity = warning
dotnet_naming_rule.public_const_all_upper.symbols = public_constants
dotnet_naming_rule.public_const_all_upper.style = all_upper

dotnet_naming_symbols.public_static_readonly.applicable_accessibilities = public,internal,protected,protected_internal,private_protected
dotnet_naming_symbols.public_static_readonly.required_modifiers = static,readonly
dotnet_naming_symbols.public_static_readonly.applicable_kinds = field
dotnet_naming_rule.public_static_readonly_all_upper.severity = warning
dotnet_naming_rule.public_static_readonly_all_upper.symbols = public_static_readonly
dotnet_naming_rule.public_static_readonly_all_upper.style = all_upper
```

#### Usage:

```cs
public readonly float PI_F = 3.14f;
public const double PI_D = 3.14d;
```

### Roslyn Formatting Options

#### Indentation Options
```ini
csharp_indent_case_contents = true
csharp_indent_case_contents_when_block = false
csharp_indent_labels = one_less_than_current
csharp_indent_switch_labels = true
```

#### New Line Options
```ini
csharp_new_line_before_catch = true
csharp_new_line_before_else = true
csharp_new_line_before_finally = true
csharp_new_line_before_open_brace = all
csharp_new_line_between_query_expression_clauses = true
```

#### Organize Using Options
```ini
dotnet_sort_system_directives_first = true
```

#### Spacing Options
```ini
csharp_space_after_cast = false
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
```

#### Wrapping Options
```ini
csharp_preserve_single_line_blocks = true
csharp_preserve_single_line_statements = true
```

### Roslyn Language Styles

### `this` Qualification
```ini
dotnet_style_qualification_for_field = false:warning
dotnet_style_qualification_for_property = false:warning
dotnet_style_qualification_for_method = false:warning
dotnet_style_qualification_for_event = false:warning
```

### Type Names
```ini
dotnet_style_predefined_type_for_locals_parameters_members = true:warning
dotnet_style_predefined_type_for_member_access = true:warning
csharp_style_var_when_type_is_apparent = true:none
csharp_style_var_for_built_in_types = true:none
csharp_style_var_elsewhere = true:silent
```

### Modifiers
```ini
dotnet_style_require_accessibility_modifiers = for_non_interface_members:warning
csharp_preferred_modifier_order = public,private,protected,internal,new,abstract,virtual,sealed,override,static,readonly,extern,unsafe,volatile,async:warning
```

### Expression Bodies
```ini
csharp_style_expression_bodied_accessors = true:warning
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_indexers = true:warning
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_operators = true:warning
csharp_style_expression_bodied_properties = true:warning
csharp_style_expression_bodied_local_functions = true:silent
```

### Expression Preferences
```ini
dotnet_style_object_initializer = true:warning
dotnet_style_collection_initializer = true:warning
dotnet_style_prefer_inferred_anonymous_type_member_names = true:warning
dotnet_style_prefer_auto_properties = true:warning
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent
dotnet_style_prefer_compound_assignment = true:warning
```

### Null/Type Check
```ini
dotnet_style_coalesce_expression = true:warning
dotnet_style_null_propagation = true:warning
csharp_style_pattern_matching_over_is_with_cast_check = true:warning
csharp_style_pattern_matching_over_as_with_null_check = true:warning
csharp_style_throw_expression = true:silent
csharp_style_conditional_delegate_call = true:warning
```

### Unused
```ini
dotnet_style_readonly_field = true:silent
dotnet_code_quality_unused_parameters = non_public:silent
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:warning
```

### Variable Declaration
```ini
csharp_style_inlined_variable_declaration = true:warning
csharp_style_deconstructed_variable_declaration = true:warning
```

### C# 7 Features
```ini
dotnet_style_prefer_inferred_tuple_names = true:warning
csharp_prefer_simple_default_expression = true:warning
csharp_style_pattern_local_over_anonymous_function = true:warning
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
```

### C# 8 Features
```ini
csharp_prefer_static_local_function = true:warning
csharp_prefer_simple_using_statement = true:silent
csharp_style_prefer_index_operator = true:warning
csharp_style_prefer_range_operator = true:warning
csharp_style_prefer_switch_expression = false:none
```
