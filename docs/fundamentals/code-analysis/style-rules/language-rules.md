---
title: 程式碼樣式語言規則
description: '深入瞭解使用 c # 和 Visual Basic 語言結構的不同程式碼樣式規則。'
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
- language rules
- EditorConfig language conventions
ms.openlocfilehash: 2aa2261534363f1da6a2109f092e08d210ebd915
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957971"
---
# <a name="language-rules"></a>語言規則

程式碼樣式語言規則會影響 .NET 程式設計語言的各種結構，例如修飾詞和括弧的使用方式。 規則分成下列類別：

- [.Net 樣式規則](#net-style-rules)：適用于 c # 和 Visual Basic 的規則。 這些規則的 EditorConfig 選項名稱會以前置詞開頭 `dotnet_style_` 。
- [C # 樣式規則](#c-style-rules)：僅適用于 c # 語言的規則。 這些規則的 EditorConfig 選項名稱會以前置詞開頭 `csharp_style_` 。
- [Visual Basic 樣式規則](#visual-basic-style-rules)：僅限 Visual Bsic 語言特有的規則。 這些規則的 EditorConfig 選項名稱會以前置詞開頭 `visual_basic_style_` 。

## <a name="option-format"></a>選項格式

您可以使用下列格式，在 EditorConfig 檔中指定語言規則的選項：

`option_name = value` (Visual Studio 2019 16.9 版 Preview 2 和更新版本) 

或

`option_name = value:severity`

- **值**

  針對每個語言規則，您可以指定一個值來定義偏好樣式的時機或時機。 許多規則接受的值 `true` (偏好以此樣式) 或 `false` (不偏好使用此樣式) 。 其他規則接受值，例如 `when_on_single_line` 或 `never` 。

- **嚴重性** (Visual Studio 2019 16.9 版 Preview 2 和更新版本中的選擇性) 

  規則的第二個部分會指定規則的 [嚴重性層級](../configuration-options.md#severity-level) 。 以這種方式指定時，只會在開發 Ide （例如 Visual Studio）中遵守嚴重性設定。 在組建期間 *不* 遵守。

  若要在組建階段強制執行程式碼樣式規則，請改為流量分析器的規則識別碼型嚴重性設定語法來設定嚴重性。 語法的格式如下 `dotnet_diagnostic.<rule ID>.severity = <severity>` `dotnet_diagnostic.IDE0040.severity = silent` 。 如需詳細資訊，請參閱 [嚴重性層級](../configuration-options.md#severity-level)。

> [!TIP]
>
> 從 Visual Studio 2019 版本16.3 開始，您可以在發生樣式違規之後，從 [ [快速動作](/visualstudio/ide/quick-actions) ] 燈泡功能表設定程式碼樣式規則。 如需詳細資訊，請參閱 [在 Visual Studio 中自動設定程式碼樣式](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio)。

## <a name="net-style-rules"></a>.NET 樣式規則

本節中的樣式規則對 C# 和 Visual Basic 都適用。

- [' this. ' 和 ' Me. ' 限定詞](ide0003-ide0009.md)
  - [dotnet_style_qualification_for_field](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [dotnet_style_qualification_for_property](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [dotnet_style_qualification_for_method](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [dotnet_style_qualification_for_event](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [語言關鍵字而非類型參考的架構類型名稱](ide0049.md)
  - [dotnet_style_predefined_type_for_locals_parameters_members](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [dotnet_style_predefined_type_for_member_access](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [修飾詞喜好設定](modifier-preferences.md#net-modifier-preferences)
  - [dotnet_style_require_accessibility_modifiers](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [csharp_preferred_modifier_order](ide0036.md#csharp_preferred_modifier_order)
  - [visual_basic_preferred_modifier_order](ide0036.md#visual_basic_preferred_modifier_order)
  - [dotnet_style_readonly_field](ide0044.md#dotnet_style_readonly_field)
- [括號喜好設定](ide0047-ide0048.md)
  - [dotnet_style_parentheses_in_arithmetic_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [dotnet_style_parentheses_in_relational_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [dotnet_style_parentheses_in_other_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [dotnet_style_parentheses_in_other_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [運算式層級喜好設定](expression-level-preferences.md#net-expression-level-preferences)
  - [dotnet_style_object_initializer](ide0017.md#dotnet_style_object_initializer)
  - [dotnet_style_collection_initializer](ide0028.md#dotnet_style_collection_initializer)
  - [dotnet_style_explicit_tuple_names](ide0033.md#dotnet_style_explicit_tuple_names)
  - [dotnet_style_prefer_inferred_tuple_names](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [dotnet_style_prefer_inferred_anonymous_type_member_names](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [dotnet_style_prefer_auto_properties](ide0032.md#dotnet_style_prefer_auto_properties)
  - [dotnet_style_prefer_conditional_expression_over_assignment](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [dotnet_style_prefer_conditional_expression_over_return](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [dotnet_style_prefer_compound_assignment](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [dotnet_style_prefer_simplified_interpolation](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [dotnet_style_prefer_simplified_boolean_expressions](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - [在 switch 語句中加入遺漏的案例](ide0010.md) -此規則沒有程式碼樣式選項。
  - [將匿名型別轉換為元組](ide0050.md) -此規則沒有程式碼樣式選項。
  - [使用 ' system.string. 組合 '](ide0070.md) -此規則沒有程式碼樣式選項。
  - [將 ' typeof ' 轉換成 ' nameof '](ide0082.md) -此規則沒有程式碼樣式選項。
- [Null 檢查喜好設定](null-checking-preferences.md#net-null-checking-preferences)
  - [dotnet_style_coalesce_expression](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [dotnet_style_null_propagation](ide0031.md#dotnet_style_null_propagation)
  - [dotnet_style_prefer_is_null_check_over_reference_equality_method](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [檔案標頭喜好設定](ide0073.md)
  - [file_header_template](ide0073.md#file_header_template)

## <a name="c-style-rules"></a>C # 樣式規則

本節中的樣式規則只適用于 c # 語言。

- [' var ' 喜好設定](ide0007-ide0008.md)
  - [csharp_style_var_for_built_in_types](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [csharp_style_var_when_type_is_apparent](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [csharp_style_var_elsewhere](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [運算式主體成員](expression-bodied-members.md)
  - [csharp_style_expression_bodied_methods](ide0022.md#csharp_style_expression_bodied_methods)
  - [csharp_style_expression_bodied_constructors](ide0021.md#csharp_style_expression_bodied_constructors)
  - [csharp_style_expression_bodied_operators](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [csharp_style_expression_bodied_properties](ide0025.md#csharp_style_expression_bodied_properties)
  - [csharp_style_expression_bodied_indexers](ide0026.md#csharp_style_expression_bodied_indexers)
  - [csharp_style_expression_bodied_accessors](ide0027.md#csharp_style_expression_bodied_accessors)
  - [csharp_style_expression_bodied_lambdas](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [csharp_style_expression_bodied_local_functions](ide0061.md#csharp_style_expression_bodied_local_functions)
- [模式比對喜好設定](pattern-matching-preferences.md)
  - [csharp_style_pattern_matching_over_is_with_cast_check](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [csharp_style_pattern_matching_over_as_with_null_check](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [csharp_style_prefer_switch_expression](ide0066.md#csharp_style_prefer_switch_expression)
  - [csharp_style_prefer_pattern_matching](ide0078.md#csharp_style_prefer_pattern_matching)
  - [csharp_style_prefer_not_pattern](ide0083.md#csharp_style_prefer_not_pattern)
- [運算式層級喜好設定](expression-level-preferences.md#c-expression-level-preferences)
  - [csharp_style_inlined_variable_declaration](ide0018.md#csharp_style_inlined_variable_declaration)
  - [csharp_prefer_simple_default_expression](ide0034.md#csharp_prefer_simple_default_expression)
  - [csharp_style_pattern_local_over_anonymous_function](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [csharp_style_deconstructed_variable_declaration](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [csharp_style_prefer_index_operator](ide0056.md#csharp_style_prefer_index_operator)
  - [csharp_style_prefer_range_operator](ide0057.md#csharp_style_prefer_range_operator)
  - [csharp_style_implicit_object_creation_when_type_is_apparent](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - [將遺漏的案例加入至 switch 運算式](ide0072.md) -此規則沒有程式碼樣式選項。
- ["Null" 檢查喜好設定](null-checking-preferences.md#c-null-checking-preferences)
  - [csharp_style_throw_expression](ide0016.md#csharp_style_throw_expression)
  - [csharp_style_conditional_delegate_call](ide1005.md#csharp_style_conditional_delegate_call)
- [程式碼區塊喜好設定](code-block-preferences.md)
  - [csharp_prefer_braces](ide0011.md#csharp_prefer_braces)
  - [csharp_prefer_simple_using_statement](ide0063.md#csharp_prefer_simple_using_statement)
- [' using ' 指示詞喜好設定](ide0065.md)
  - [csharp_using_directive_placement](ide0065.md#csharp_using_directive_placement)
- [修飾詞喜好設定](modifier-preferences.md#c-modifier-preferences)
  - [csharp_prefer_static_local_function](ide0062.md#csharp_prefer_static_local_function)
  - [將結構欄位設為可寫入](ide0064.md) -此規則沒有程式碼樣式選項。

## <a name="visual-basic-style-rules"></a>Visual Basic 樣式規則

本節中的樣式規則只適用于 Visual Basic 語言。

- [模式比對喜好設定](pattern-matching-preferences.md)
  - [visual_basic_style_prefer_isnot_expression](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a>另請參閱

- [不需要的程式碼規則](unnecessary-code-rules.md)
- [格式化規則](formatting-rules.md)
- [命名規則](naming-rules.md)
- [.NET 程式碼樣式規則參考](index.md)
