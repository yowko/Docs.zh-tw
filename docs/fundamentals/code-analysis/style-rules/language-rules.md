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
ms.openlocfilehash: b77d9aa2a528a6cf540babd5e5acc148e48c489c
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96586675"
---
# <a name="language-rules"></a><span data-ttu-id="6fd61-103">語言規則</span><span class="sxs-lookup"><span data-stu-id="6fd61-103">Language rules</span></span>

<span data-ttu-id="6fd61-104">程式碼樣式語言規則會影響 .NET 程式設計語言的各種結構，例如修飾詞和括弧的使用方式。</span><span class="sxs-lookup"><span data-stu-id="6fd61-104">Code style language rules affect how various constructs of .NET programming languages, for example, modifiers and parentheses, are used.</span></span> <span data-ttu-id="6fd61-105">規則分成下列類別：</span><span class="sxs-lookup"><span data-stu-id="6fd61-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="6fd61-106">[.Net 樣式規則](#net-style-rules)：適用于 c # 和 Visual Basic 的規則。</span><span class="sxs-lookup"><span data-stu-id="6fd61-106">[.NET style rules](#net-style-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="6fd61-107">這些規則的 EditorConfig 選項名稱會以前置詞開頭 `dotnet_style_` 。</span><span class="sxs-lookup"><span data-stu-id="6fd61-107">The EditorConfig option names for these rules start with `dotnet_style_` prefix.</span></span>
- <span data-ttu-id="6fd61-108">[C # 樣式規則](#c-style-rules)：僅適用于 c # 語言的規則。</span><span class="sxs-lookup"><span data-stu-id="6fd61-108">[C# style rules](#c-style-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="6fd61-109">這些規則的 EditorConfig 選項名稱會以前置詞開頭 `csharp_style_` 。</span><span class="sxs-lookup"><span data-stu-id="6fd61-109">The EditorConfig option names for these rules start with `csharp_style_` prefix.</span></span>
- <span data-ttu-id="6fd61-110">[Visual Basic 樣式規則](#visual-basic-style-rules)：僅限 Visual Bsic 語言特有的規則。</span><span class="sxs-lookup"><span data-stu-id="6fd61-110">[Visual Basic style rules](#visual-basic-style-rules): Rules that are specific to Visual Bsic language only.</span></span> <span data-ttu-id="6fd61-111">這些規則的 EditorConfig 選項名稱會以前置詞開頭 `visual_basic_style_` 。</span><span class="sxs-lookup"><span data-stu-id="6fd61-111">The EditorConfig option names for these rules start with `visual_basic_style_` prefix.</span></span>

## <a name="option-format"></a><span data-ttu-id="6fd61-112">選項格式</span><span class="sxs-lookup"><span data-stu-id="6fd61-112">Option format</span></span>

<span data-ttu-id="6fd61-113">您可以使用下列格式，在 EditorConfig 檔中指定語言規則的選項：</span><span class="sxs-lookup"><span data-stu-id="6fd61-113">Options for language rules can be specified in an EditorConfig file with the following format:</span></span>

`option_name = value:severity`

- <span data-ttu-id="6fd61-114">**值**：針對每個語言規則，您可以指定一個值來定義偏好樣式的時機或時機。</span><span class="sxs-lookup"><span data-stu-id="6fd61-114">**Value**: For each language rule, you specify a value that defines if or when to prefer the style.</span></span> <span data-ttu-id="6fd61-115">許多規則接受的值 `true` (偏好以此樣式) 或 `false` (不偏好使用此樣式) 。</span><span class="sxs-lookup"><span data-stu-id="6fd61-115">Many rules accept a value of `true` (prefer this style) or `false` (do not prefer this style).</span></span> <span data-ttu-id="6fd61-116">其他規則接受值，例如 `when_on_single_line` 或 `never` 。</span><span class="sxs-lookup"><span data-stu-id="6fd61-116">Other rules accept values such as `when_on_single_line` or `never`.</span></span>
- <span data-ttu-id="6fd61-117">**嚴重性**：規則的第二個部分會指定規則的 [嚴重性層級](../configuration-options.md#severity-level) 。</span><span class="sxs-lookup"><span data-stu-id="6fd61-117">**Severity**: The second part of the rule specifies the [severity level](../configuration-options.md#severity-level) for the rule.</span></span> <span data-ttu-id="6fd61-118">只有在開發 Ide （例如 Visual Studio）中，才能採用嚴重性規格做為上述選項語法的一部分。</span><span class="sxs-lookup"><span data-stu-id="6fd61-118">Severity specification as part of the above option syntax is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="6fd61-119">C # 或 VB 編譯器無法理解這項設定，因此不會在組建期間遵守。</span><span class="sxs-lookup"><span data-stu-id="6fd61-119">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="6fd61-120">相反地，若要強制執行組建的程式碼樣式規則，您應該流量分析器的規則識別碼型嚴重性設定語法來設定嚴重性。</span><span class="sxs-lookup"><span data-stu-id="6fd61-120">Instead, to enforce code style rules on build, you should set the severity by using the rule ID-based severity configuration syntax for analyzers.</span></span> <span data-ttu-id="6fd61-121">語法的格式如下 `dotnet_diagnostic.<rule ID>.severity = <severity>` `dotnet_diagnostic.IDE0040.severity = silent` 。</span><span class="sxs-lookup"><span data-stu-id="6fd61-121">The syntax takes the form `dotnet_diagnostic.<rule ID>.severity = <severity>`, for example, `dotnet_diagnostic.IDE0040.severity = silent`.</span></span> <span data-ttu-id="6fd61-122">如需詳細資訊，請參閱此 [GitHub 問題](https://github.com/dotnet/roslyn/issues/44201)。</span><span class="sxs-lookup"><span data-stu-id="6fd61-122">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

> [!TIP]
>
> <span data-ttu-id="6fd61-123">從 Visual Studio 2019 版本16.3 開始，您可以在發生樣式違規之後，從 [ [快速動作](/visualstudio/ide/quick-actions) ] 燈泡功能表設定程式碼樣式規則。</span><span class="sxs-lookup"><span data-stu-id="6fd61-123">Starting in Visual Studio 2019 version 16.3, you can configure code style rules from the [Quick Actions](/visualstudio/ide/quick-actions) light bulb menu after a style violation occurs.</span></span> <span data-ttu-id="6fd61-124">如需詳細資訊，請參閱 [在 Visual Studio 中自動設定程式碼樣式](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="6fd61-124">For more information, see [Automatically configure code styles in Visual Studio](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).</span></span>

## <a name="net-style-rules"></a><span data-ttu-id="6fd61-125">.NET 樣式規則</span><span class="sxs-lookup"><span data-stu-id="6fd61-125">.NET style rules</span></span>

<span data-ttu-id="6fd61-126">本節中的樣式規則對 C# 和 Visual Basic 都適用。</span><span class="sxs-lookup"><span data-stu-id="6fd61-126">The style rules in this section are applicable to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="6fd61-127">' this. ' 和 ' Me. ' 限定詞</span><span class="sxs-lookup"><span data-stu-id="6fd61-127">'this.' and 'Me.' qualifiers</span></span>](ide0003-ide0009.md)
  - [<span data-ttu-id="6fd61-128">dotnet_style_qualification_for_field</span><span class="sxs-lookup"><span data-stu-id="6fd61-128">dotnet_style_qualification_for_field</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [<span data-ttu-id="6fd61-129">dotnet_style_qualification_for_property</span><span class="sxs-lookup"><span data-stu-id="6fd61-129">dotnet_style_qualification_for_property</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [<span data-ttu-id="6fd61-130">dotnet_style_qualification_for_method</span><span class="sxs-lookup"><span data-stu-id="6fd61-130">dotnet_style_qualification_for_method</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [<span data-ttu-id="6fd61-131">dotnet_style_qualification_for_event</span><span class="sxs-lookup"><span data-stu-id="6fd61-131">dotnet_style_qualification_for_event</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [<span data-ttu-id="6fd61-132">語言關鍵字而非類型參考的架構類型名稱</span><span class="sxs-lookup"><span data-stu-id="6fd61-132">Language keywords instead of framework type names for type references</span></span>](ide0049.md)
  - [<span data-ttu-id="6fd61-133">dotnet_style_predefined_type_for_locals_parameters_members</span><span class="sxs-lookup"><span data-stu-id="6fd61-133">dotnet_style_predefined_type_for_locals_parameters_members</span></span>](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [<span data-ttu-id="6fd61-134">dotnet_style_predefined_type_for_member_access</span><span class="sxs-lookup"><span data-stu-id="6fd61-134">dotnet_style_predefined_type_for_member_access</span></span>](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [<span data-ttu-id="6fd61-135">修飾詞喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-135">Modifier preferences</span></span>](modifier-preferences.md#net-modifier-preferences)
  - [<span data-ttu-id="6fd61-136">dotnet_style_require_accessibility_modifiers</span><span class="sxs-lookup"><span data-stu-id="6fd61-136">dotnet_style_require_accessibility_modifiers</span></span>](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [<span data-ttu-id="6fd61-137">csharp_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="6fd61-137">csharp_preferred_modifier_order</span></span>](ide0036.md#csharp_preferred_modifier_order)
  - [<span data-ttu-id="6fd61-138">visual_basic_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="6fd61-138">visual_basic_preferred_modifier_order</span></span>](ide0036.md#visual_basic_preferred_modifier_order)
  - [<span data-ttu-id="6fd61-139">dotnet_style_readonly_field</span><span class="sxs-lookup"><span data-stu-id="6fd61-139">dotnet_style_readonly_field</span></span>](ide0044.md#dotnet_style_readonly_field)
- [<span data-ttu-id="6fd61-140">括號喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-140">Parentheses preferences</span></span>](ide0047-ide0048.md)
  - [<span data-ttu-id="6fd61-141">dotnet_style_parentheses_in_arithmetic_binary_operators</span><span class="sxs-lookup"><span data-stu-id="6fd61-141">dotnet_style_parentheses_in_arithmetic_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [<span data-ttu-id="6fd61-142">dotnet_style_parentheses_in_relational_binary_operators</span><span class="sxs-lookup"><span data-stu-id="6fd61-142">dotnet_style_parentheses_in_relational_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [<span data-ttu-id="6fd61-143">dotnet_style_parentheses_in_other_binary_operators</span><span class="sxs-lookup"><span data-stu-id="6fd61-143">dotnet_style_parentheses_in_other_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [<span data-ttu-id="6fd61-144">dotnet_style_parentheses_in_other_operators</span><span class="sxs-lookup"><span data-stu-id="6fd61-144">dotnet_style_parentheses_in_other_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [<span data-ttu-id="6fd61-145">運算式層級喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-145">Expression-level preferences</span></span>](expression-level-preferences.md#net-expression-level-preferences)
  - [<span data-ttu-id="6fd61-146">dotnet_style_object_initializer</span><span class="sxs-lookup"><span data-stu-id="6fd61-146">dotnet_style_object_initializer</span></span>](ide0017.md#dotnet_style_object_initializer)
  - [<span data-ttu-id="6fd61-147">dotnet_style_collection_initializer</span><span class="sxs-lookup"><span data-stu-id="6fd61-147">dotnet_style_collection_initializer</span></span>](ide0028.md#dotnet_style_collection_initializer)
  - [<span data-ttu-id="6fd61-148">dotnet_style_explicit_tuple_names</span><span class="sxs-lookup"><span data-stu-id="6fd61-148">dotnet_style_explicit_tuple_names</span></span>](ide0033.md#dotnet_style_explicit_tuple_names)
  - [<span data-ttu-id="6fd61-149">dotnet_style_prefer_inferred_tuple_names</span><span class="sxs-lookup"><span data-stu-id="6fd61-149">dotnet_style_prefer_inferred_tuple_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [<span data-ttu-id="6fd61-150">dotnet_style_prefer_inferred_anonymous_type_member_names</span><span class="sxs-lookup"><span data-stu-id="6fd61-150">dotnet_style_prefer_inferred_anonymous_type_member_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [<span data-ttu-id="6fd61-151">dotnet_style_prefer_auto_properties</span><span class="sxs-lookup"><span data-stu-id="6fd61-151">dotnet_style_prefer_auto_properties</span></span>](ide0032.md#dotnet_style_prefer_auto_properties)
  - [<span data-ttu-id="6fd61-152">dotnet_style_prefer_conditional_expression_over_assignment</span><span class="sxs-lookup"><span data-stu-id="6fd61-152">dotnet_style_prefer_conditional_expression_over_assignment</span></span>](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [<span data-ttu-id="6fd61-153">dotnet_style_prefer_conditional_expression_over_return</span><span class="sxs-lookup"><span data-stu-id="6fd61-153">dotnet_style_prefer_conditional_expression_over_return</span></span>](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [<span data-ttu-id="6fd61-154">dotnet_style_prefer_compound_assignment</span><span class="sxs-lookup"><span data-stu-id="6fd61-154">dotnet_style_prefer_compound_assignment</span></span>](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [<span data-ttu-id="6fd61-155">dotnet_style_prefer_simplified_interpolation</span><span class="sxs-lookup"><span data-stu-id="6fd61-155">dotnet_style_prefer_simplified_interpolation</span></span>](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [<span data-ttu-id="6fd61-156">dotnet_style_prefer_simplified_boolean_expressions</span><span class="sxs-lookup"><span data-stu-id="6fd61-156">dotnet_style_prefer_simplified_boolean_expressions</span></span>](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - <span data-ttu-id="6fd61-157">[在 switch 語句中加入遺漏的案例](ide0010.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="6fd61-157">[Add missing cases to switch statement](ide0010.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="6fd61-158">[將匿名型別轉換為元組](ide0050.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="6fd61-158">[Convert anonymous type to tuple](ide0050.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="6fd61-159">[使用 ' system.string. 組合 '](ide0070.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="6fd61-159">[Use 'System.HashCode.Combine'](ide0070.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="6fd61-160">[將 ' typeof ' 轉換成 ' nameof '](ide0082.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="6fd61-160">[Convert 'typeof' to 'nameof'](ide0082.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="6fd61-161">Null 檢查喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-161">Null-checking preferences</span></span>](null-checking-preferences.md#net-null-checking-preferences)
  - [<span data-ttu-id="6fd61-162">dotnet_style_coalesce_expression</span><span class="sxs-lookup"><span data-stu-id="6fd61-162">dotnet_style_coalesce_expression</span></span>](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [<span data-ttu-id="6fd61-163">dotnet_style_null_propagation</span><span class="sxs-lookup"><span data-stu-id="6fd61-163">dotnet_style_null_propagation</span></span>](ide0031.md#dotnet_style_null_propagation)
  - [<span data-ttu-id="6fd61-164">dotnet_style_prefer_is_null_check_over_reference_equality_method</span><span class="sxs-lookup"><span data-stu-id="6fd61-164">dotnet_style_prefer_is_null_check_over_reference_equality_method</span></span>](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [<span data-ttu-id="6fd61-165">檔案標頭喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-165">File header preferences</span></span>](ide0073.md)
  - [<span data-ttu-id="6fd61-166">file_header_template</span><span class="sxs-lookup"><span data-stu-id="6fd61-166">file_header_template</span></span>](ide0073.md#file_header_template)

## <a name="c-style-rules"></a><span data-ttu-id="6fd61-167">C # 樣式規則</span><span class="sxs-lookup"><span data-stu-id="6fd61-167">C# style rules</span></span>

<span data-ttu-id="6fd61-168">本節中的樣式規則只適用于 c # 語言。</span><span class="sxs-lookup"><span data-stu-id="6fd61-168">The style rules in this section are applicable to C# language only.</span></span>

- [<span data-ttu-id="6fd61-169">' var ' 喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-169">'var' preferences</span></span>](ide0007-ide0008.md)
  - [<span data-ttu-id="6fd61-170">csharp_style_var_for_built_in_types</span><span class="sxs-lookup"><span data-stu-id="6fd61-170">csharp_style_var_for_built_in_types</span></span>](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [<span data-ttu-id="6fd61-171">csharp_style_var_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="6fd61-171">csharp_style_var_when_type_is_apparent</span></span>](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [<span data-ttu-id="6fd61-172">csharp_style_var_elsewhere</span><span class="sxs-lookup"><span data-stu-id="6fd61-172">csharp_style_var_elsewhere</span></span>](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [<span data-ttu-id="6fd61-173">運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="6fd61-173">Expression-bodied members</span></span>](expression-bodied-members.md)
  - [<span data-ttu-id="6fd61-174">csharp_style_expression_bodied_methods</span><span class="sxs-lookup"><span data-stu-id="6fd61-174">csharp_style_expression_bodied_methods</span></span>](ide0022.md#csharp_style_expression_bodied_methods)
  - [<span data-ttu-id="6fd61-175">csharp_style_expression_bodied_constructors</span><span class="sxs-lookup"><span data-stu-id="6fd61-175">csharp_style_expression_bodied_constructors</span></span>](ide0021.md#csharp_style_expression_bodied_constructors)
  - [<span data-ttu-id="6fd61-176">csharp_style_expression_bodied_operators</span><span class="sxs-lookup"><span data-stu-id="6fd61-176">csharp_style_expression_bodied_operators</span></span>](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [<span data-ttu-id="6fd61-177">csharp_style_expression_bodied_properties</span><span class="sxs-lookup"><span data-stu-id="6fd61-177">csharp_style_expression_bodied_properties</span></span>](ide0025.md#csharp_style_expression_bodied_properties)
  - [<span data-ttu-id="6fd61-178">csharp_style_expression_bodied_indexers</span><span class="sxs-lookup"><span data-stu-id="6fd61-178">csharp_style_expression_bodied_indexers</span></span>](ide0026.md#csharp_style_expression_bodied_indexers)
  - [<span data-ttu-id="6fd61-179">csharp_style_expression_bodied_accessors</span><span class="sxs-lookup"><span data-stu-id="6fd61-179">csharp_style_expression_bodied_accessors</span></span>](ide0027.md#csharp_style_expression_bodied_accessors)
  - [<span data-ttu-id="6fd61-180">csharp_style_expression_bodied_lambdas</span><span class="sxs-lookup"><span data-stu-id="6fd61-180">csharp_style_expression_bodied_lambdas</span></span>](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [<span data-ttu-id="6fd61-181">csharp_style_expression_bodied_local_functions</span><span class="sxs-lookup"><span data-stu-id="6fd61-181">csharp_style_expression_bodied_local_functions</span></span>](ide0061.md#csharp_style_expression_bodied_local_functions)
- [<span data-ttu-id="6fd61-182">模式比對喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-182">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="6fd61-183">csharp_style_pattern_matching_over_is_with_cast_check</span><span class="sxs-lookup"><span data-stu-id="6fd61-183">csharp_style_pattern_matching_over_is_with_cast_check</span></span>](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [<span data-ttu-id="6fd61-184">csharp_style_pattern_matching_over_as_with_null_check</span><span class="sxs-lookup"><span data-stu-id="6fd61-184">csharp_style_pattern_matching_over_as_with_null_check</span></span>](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [<span data-ttu-id="6fd61-185">csharp_style_prefer_switch_expression</span><span class="sxs-lookup"><span data-stu-id="6fd61-185">csharp_style_prefer_switch_expression</span></span>](ide0066.md#csharp_style_prefer_switch_expression)
  - [<span data-ttu-id="6fd61-186">csharp_style_prefer_pattern_matching</span><span class="sxs-lookup"><span data-stu-id="6fd61-186">csharp_style_prefer_pattern_matching</span></span>](ide0078.md#csharp_style_prefer_pattern_matching)
  - [<span data-ttu-id="6fd61-187">csharp_style_prefer_not_pattern</span><span class="sxs-lookup"><span data-stu-id="6fd61-187">csharp_style_prefer_not_pattern</span></span>](ide0083.md#csharp_style_prefer_not_pattern)
- [<span data-ttu-id="6fd61-188">運算式層級喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-188">Expression-level preferences</span></span>](expression-level-preferences.md#c-expression-level-preferences)
  - [<span data-ttu-id="6fd61-189">csharp_style_inlined_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="6fd61-189">csharp_style_inlined_variable_declaration</span></span>](ide0018.md#csharp_style_inlined_variable_declaration)
  - [<span data-ttu-id="6fd61-190">csharp_prefer_simple_default_expression</span><span class="sxs-lookup"><span data-stu-id="6fd61-190">csharp_prefer_simple_default_expression</span></span>](ide0034.md#csharp_prefer_simple_default_expression)
  - [<span data-ttu-id="6fd61-191">csharp_style_pattern_local_over_anonymous_function</span><span class="sxs-lookup"><span data-stu-id="6fd61-191">csharp_style_pattern_local_over_anonymous_function</span></span>](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [<span data-ttu-id="6fd61-192">csharp_style_deconstructed_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="6fd61-192">csharp_style_deconstructed_variable_declaration</span></span>](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [<span data-ttu-id="6fd61-193">csharp_style_prefer_index_operator</span><span class="sxs-lookup"><span data-stu-id="6fd61-193">csharp_style_prefer_index_operator</span></span>](ide0056.md#csharp_style_prefer_index_operator)
  - [<span data-ttu-id="6fd61-194">csharp_style_prefer_range_operator</span><span class="sxs-lookup"><span data-stu-id="6fd61-194">csharp_style_prefer_range_operator</span></span>](ide0057.md#csharp_style_prefer_range_operator)
  - [<span data-ttu-id="6fd61-195">csharp_style_implicit_object_creation_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="6fd61-195">csharp_style_implicit_object_creation_when_type_is_apparent</span></span>](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - <span data-ttu-id="6fd61-196">[將遺漏的案例加入至 switch 運算式](ide0072.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="6fd61-196">[Add missing cases to switch expression](ide0072.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="6fd61-197">"Null" 檢查喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-197">"Null" checking preferences</span></span>](null-checking-preferences.md#c-null-checking-preferences)
  - [<span data-ttu-id="6fd61-198">csharp_style_throw_expression</span><span class="sxs-lookup"><span data-stu-id="6fd61-198">csharp_style_throw_expression</span></span>](ide0016.md#csharp_style_throw_expression)
  - [<span data-ttu-id="6fd61-199">csharp_style_conditional_delegate_call</span><span class="sxs-lookup"><span data-stu-id="6fd61-199">csharp_style_conditional_delegate_call</span></span>](ide1005.md#csharp_style_conditional_delegate_call)
- [<span data-ttu-id="6fd61-200">程式碼區塊喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-200">Code block preferences</span></span>](code-block-preferences.md)
  - [<span data-ttu-id="6fd61-201">csharp_prefer_braces</span><span class="sxs-lookup"><span data-stu-id="6fd61-201">csharp_prefer_braces</span></span>](ide0011.md#csharp_prefer_braces)
  - [<span data-ttu-id="6fd61-202">csharp_prefer_simple_using_statement</span><span class="sxs-lookup"><span data-stu-id="6fd61-202">csharp_prefer_simple_using_statement</span></span>](ide0063.md#csharp_prefer_simple_using_statement)
- [<span data-ttu-id="6fd61-203">' using ' 指示詞喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-203">'using' directive preferences</span></span>](ide0065.md)
  - [<span data-ttu-id="6fd61-204">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="6fd61-204">csharp_using_directive_placement</span></span>](ide0065.md#csharp_using_directive_placement)
- [<span data-ttu-id="6fd61-205">修飾詞喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-205">Modifier preferences</span></span>](modifier-preferences.md#c-modifier-preferences)
  - [<span data-ttu-id="6fd61-206">csharp_prefer_static_local_function</span><span class="sxs-lookup"><span data-stu-id="6fd61-206">csharp_prefer_static_local_function</span></span>](ide0062.md#csharp_prefer_static_local_function)
  - <span data-ttu-id="6fd61-207">[將結構欄位設為可寫入](ide0064.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="6fd61-207">[Make struct fields writable](ide0064.md) - This rule has no code style option.</span></span>

## <a name="visual-basic-style-rules"></a><span data-ttu-id="6fd61-208">Visual Basic 樣式規則</span><span class="sxs-lookup"><span data-stu-id="6fd61-208">Visual Basic style rules</span></span>

<span data-ttu-id="6fd61-209">本節中的樣式規則只適用于 Visual Basic 語言。</span><span class="sxs-lookup"><span data-stu-id="6fd61-209">The style rules in this section are applicable to Visual Basic language only.</span></span>

- [<span data-ttu-id="6fd61-210">模式比對喜好設定</span><span class="sxs-lookup"><span data-stu-id="6fd61-210">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="6fd61-211">visual_basic_style_prefer_isnot_expression</span><span class="sxs-lookup"><span data-stu-id="6fd61-211">visual_basic_style_prefer_isnot_expression</span></span>](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a><span data-ttu-id="6fd61-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fd61-212">See also</span></span>

- [<span data-ttu-id="6fd61-213">不需要的程式碼規則</span><span class="sxs-lookup"><span data-stu-id="6fd61-213">Unnecessary code rules</span></span>](unnecessary-code-rules.md)
- [<span data-ttu-id="6fd61-214">格式化規則</span><span class="sxs-lookup"><span data-stu-id="6fd61-214">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="6fd61-215">命名規則</span><span class="sxs-lookup"><span data-stu-id="6fd61-215">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="6fd61-216">.NET 程式碼樣式規則參考</span><span class="sxs-lookup"><span data-stu-id="6fd61-216">.NET code style rules reference</span></span>](index.md)
