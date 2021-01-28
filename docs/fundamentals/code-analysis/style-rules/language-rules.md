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
# <a name="language-rules"></a><span data-ttu-id="5d709-103">語言規則</span><span class="sxs-lookup"><span data-stu-id="5d709-103">Language rules</span></span>

<span data-ttu-id="5d709-104">程式碼樣式語言規則會影響 .NET 程式設計語言的各種結構，例如修飾詞和括弧的使用方式。</span><span class="sxs-lookup"><span data-stu-id="5d709-104">Code style language rules affect how various constructs of .NET programming languages, for example, modifiers and parentheses, are used.</span></span> <span data-ttu-id="5d709-105">規則分成下列類別：</span><span class="sxs-lookup"><span data-stu-id="5d709-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="5d709-106">[.Net 樣式規則](#net-style-rules)：適用于 c # 和 Visual Basic 的規則。</span><span class="sxs-lookup"><span data-stu-id="5d709-106">[.NET style rules](#net-style-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="5d709-107">這些規則的 EditorConfig 選項名稱會以前置詞開頭 `dotnet_style_` 。</span><span class="sxs-lookup"><span data-stu-id="5d709-107">The EditorConfig option names for these rules start with `dotnet_style_` prefix.</span></span>
- <span data-ttu-id="5d709-108">[C # 樣式規則](#c-style-rules)：僅適用于 c # 語言的規則。</span><span class="sxs-lookup"><span data-stu-id="5d709-108">[C# style rules](#c-style-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="5d709-109">這些規則的 EditorConfig 選項名稱會以前置詞開頭 `csharp_style_` 。</span><span class="sxs-lookup"><span data-stu-id="5d709-109">The EditorConfig option names for these rules start with `csharp_style_` prefix.</span></span>
- <span data-ttu-id="5d709-110">[Visual Basic 樣式規則](#visual-basic-style-rules)：僅限 Visual Bsic 語言特有的規則。</span><span class="sxs-lookup"><span data-stu-id="5d709-110">[Visual Basic style rules](#visual-basic-style-rules): Rules that are specific to Visual Bsic language only.</span></span> <span data-ttu-id="5d709-111">這些規則的 EditorConfig 選項名稱會以前置詞開頭 `visual_basic_style_` 。</span><span class="sxs-lookup"><span data-stu-id="5d709-111">The EditorConfig option names for these rules start with `visual_basic_style_` prefix.</span></span>

## <a name="option-format"></a><span data-ttu-id="5d709-112">選項格式</span><span class="sxs-lookup"><span data-stu-id="5d709-112">Option format</span></span>

<span data-ttu-id="5d709-113">您可以使用下列格式，在 EditorConfig 檔中指定語言規則的選項：</span><span class="sxs-lookup"><span data-stu-id="5d709-113">Options for language rules can be specified in an EditorConfig file with the following format:</span></span>

<span data-ttu-id="5d709-114">`option_name = value` (Visual Studio 2019 16.9 版 Preview 2 和更新版本) </span><span class="sxs-lookup"><span data-stu-id="5d709-114">`option_name = value` (Visual Studio 2019 version 16.9 Preview 2 and later)</span></span>

<span data-ttu-id="5d709-115">或</span><span class="sxs-lookup"><span data-stu-id="5d709-115">or</span></span>

`option_name = value:severity`

- <span data-ttu-id="5d709-116">**值**</span><span class="sxs-lookup"><span data-stu-id="5d709-116">**Value**</span></span>

  <span data-ttu-id="5d709-117">針對每個語言規則，您可以指定一個值來定義偏好樣式的時機或時機。</span><span class="sxs-lookup"><span data-stu-id="5d709-117">For each language rule, you specify a value that defines if or when to prefer the style.</span></span> <span data-ttu-id="5d709-118">許多規則接受的值 `true` (偏好以此樣式) 或 `false` (不偏好使用此樣式) 。</span><span class="sxs-lookup"><span data-stu-id="5d709-118">Many rules accept a value of `true` (prefer this style) or `false` (do not prefer this style).</span></span> <span data-ttu-id="5d709-119">其他規則接受值，例如 `when_on_single_line` 或 `never` 。</span><span class="sxs-lookup"><span data-stu-id="5d709-119">Other rules accept values such as `when_on_single_line` or `never`.</span></span>

- <span data-ttu-id="5d709-120">**嚴重性** (Visual Studio 2019 16.9 版 Preview 2 和更新版本中的選擇性) </span><span class="sxs-lookup"><span data-stu-id="5d709-120">**Severity** (optional in Visual Studio 2019 version 16.9 Preview 2 and later versions)</span></span>

  <span data-ttu-id="5d709-121">規則的第二個部分會指定規則的 [嚴重性層級](../configuration-options.md#severity-level) 。</span><span class="sxs-lookup"><span data-stu-id="5d709-121">The second part of the rule specifies the [severity level](../configuration-options.md#severity-level) for the rule.</span></span> <span data-ttu-id="5d709-122">以這種方式指定時，只會在開發 Ide （例如 Visual Studio）中遵守嚴重性設定。</span><span class="sxs-lookup"><span data-stu-id="5d709-122">When specified in this way, the severity setting is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="5d709-123">在組建期間 *不* 遵守。</span><span class="sxs-lookup"><span data-stu-id="5d709-123">It is *not* respected during build.</span></span>

  <span data-ttu-id="5d709-124">若要在組建階段強制執行程式碼樣式規則，請改為流量分析器的規則識別碼型嚴重性設定語法來設定嚴重性。</span><span class="sxs-lookup"><span data-stu-id="5d709-124">To enforce code style rules at build time, set the severity by using the rule ID-based severity configuration syntax for analyzers instead.</span></span> <span data-ttu-id="5d709-125">語法的格式如下 `dotnet_diagnostic.<rule ID>.severity = <severity>` `dotnet_diagnostic.IDE0040.severity = silent` 。</span><span class="sxs-lookup"><span data-stu-id="5d709-125">The syntax takes the form `dotnet_diagnostic.<rule ID>.severity = <severity>`, for example, `dotnet_diagnostic.IDE0040.severity = silent`.</span></span> <span data-ttu-id="5d709-126">如需詳細資訊，請參閱 [嚴重性層級](../configuration-options.md#severity-level)。</span><span class="sxs-lookup"><span data-stu-id="5d709-126">For more information, see [severity level](../configuration-options.md#severity-level).</span></span>

> [!TIP]
>
> <span data-ttu-id="5d709-127">從 Visual Studio 2019 版本16.3 開始，您可以在發生樣式違規之後，從 [ [快速動作](/visualstudio/ide/quick-actions) ] 燈泡功能表設定程式碼樣式規則。</span><span class="sxs-lookup"><span data-stu-id="5d709-127">Starting in Visual Studio 2019 version 16.3, you can configure code style rules from the [Quick Actions](/visualstudio/ide/quick-actions) light bulb menu after a style violation occurs.</span></span> <span data-ttu-id="5d709-128">如需詳細資訊，請參閱 [在 Visual Studio 中自動設定程式碼樣式](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="5d709-128">For more information, see [Automatically configure code styles in Visual Studio](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).</span></span>

## <a name="net-style-rules"></a><span data-ttu-id="5d709-129">.NET 樣式規則</span><span class="sxs-lookup"><span data-stu-id="5d709-129">.NET style rules</span></span>

<span data-ttu-id="5d709-130">本節中的樣式規則對 C# 和 Visual Basic 都適用。</span><span class="sxs-lookup"><span data-stu-id="5d709-130">The style rules in this section are applicable to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="5d709-131">' this. ' 和 ' Me. ' 限定詞</span><span class="sxs-lookup"><span data-stu-id="5d709-131">'this.' and 'Me.' qualifiers</span></span>](ide0003-ide0009.md)
  - [<span data-ttu-id="5d709-132">dotnet_style_qualification_for_field</span><span class="sxs-lookup"><span data-stu-id="5d709-132">dotnet_style_qualification_for_field</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [<span data-ttu-id="5d709-133">dotnet_style_qualification_for_property</span><span class="sxs-lookup"><span data-stu-id="5d709-133">dotnet_style_qualification_for_property</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [<span data-ttu-id="5d709-134">dotnet_style_qualification_for_method</span><span class="sxs-lookup"><span data-stu-id="5d709-134">dotnet_style_qualification_for_method</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [<span data-ttu-id="5d709-135">dotnet_style_qualification_for_event</span><span class="sxs-lookup"><span data-stu-id="5d709-135">dotnet_style_qualification_for_event</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [<span data-ttu-id="5d709-136">語言關鍵字而非類型參考的架構類型名稱</span><span class="sxs-lookup"><span data-stu-id="5d709-136">Language keywords instead of framework type names for type references</span></span>](ide0049.md)
  - [<span data-ttu-id="5d709-137">dotnet_style_predefined_type_for_locals_parameters_members</span><span class="sxs-lookup"><span data-stu-id="5d709-137">dotnet_style_predefined_type_for_locals_parameters_members</span></span>](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [<span data-ttu-id="5d709-138">dotnet_style_predefined_type_for_member_access</span><span class="sxs-lookup"><span data-stu-id="5d709-138">dotnet_style_predefined_type_for_member_access</span></span>](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [<span data-ttu-id="5d709-139">修飾詞喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-139">Modifier preferences</span></span>](modifier-preferences.md#net-modifier-preferences)
  - [<span data-ttu-id="5d709-140">dotnet_style_require_accessibility_modifiers</span><span class="sxs-lookup"><span data-stu-id="5d709-140">dotnet_style_require_accessibility_modifiers</span></span>](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [<span data-ttu-id="5d709-141">csharp_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="5d709-141">csharp_preferred_modifier_order</span></span>](ide0036.md#csharp_preferred_modifier_order)
  - [<span data-ttu-id="5d709-142">visual_basic_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="5d709-142">visual_basic_preferred_modifier_order</span></span>](ide0036.md#visual_basic_preferred_modifier_order)
  - [<span data-ttu-id="5d709-143">dotnet_style_readonly_field</span><span class="sxs-lookup"><span data-stu-id="5d709-143">dotnet_style_readonly_field</span></span>](ide0044.md#dotnet_style_readonly_field)
- [<span data-ttu-id="5d709-144">括號喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-144">Parentheses preferences</span></span>](ide0047-ide0048.md)
  - [<span data-ttu-id="5d709-145">dotnet_style_parentheses_in_arithmetic_binary_operators</span><span class="sxs-lookup"><span data-stu-id="5d709-145">dotnet_style_parentheses_in_arithmetic_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [<span data-ttu-id="5d709-146">dotnet_style_parentheses_in_relational_binary_operators</span><span class="sxs-lookup"><span data-stu-id="5d709-146">dotnet_style_parentheses_in_relational_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [<span data-ttu-id="5d709-147">dotnet_style_parentheses_in_other_binary_operators</span><span class="sxs-lookup"><span data-stu-id="5d709-147">dotnet_style_parentheses_in_other_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [<span data-ttu-id="5d709-148">dotnet_style_parentheses_in_other_operators</span><span class="sxs-lookup"><span data-stu-id="5d709-148">dotnet_style_parentheses_in_other_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [<span data-ttu-id="5d709-149">運算式層級喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-149">Expression-level preferences</span></span>](expression-level-preferences.md#net-expression-level-preferences)
  - [<span data-ttu-id="5d709-150">dotnet_style_object_initializer</span><span class="sxs-lookup"><span data-stu-id="5d709-150">dotnet_style_object_initializer</span></span>](ide0017.md#dotnet_style_object_initializer)
  - [<span data-ttu-id="5d709-151">dotnet_style_collection_initializer</span><span class="sxs-lookup"><span data-stu-id="5d709-151">dotnet_style_collection_initializer</span></span>](ide0028.md#dotnet_style_collection_initializer)
  - [<span data-ttu-id="5d709-152">dotnet_style_explicit_tuple_names</span><span class="sxs-lookup"><span data-stu-id="5d709-152">dotnet_style_explicit_tuple_names</span></span>](ide0033.md#dotnet_style_explicit_tuple_names)
  - [<span data-ttu-id="5d709-153">dotnet_style_prefer_inferred_tuple_names</span><span class="sxs-lookup"><span data-stu-id="5d709-153">dotnet_style_prefer_inferred_tuple_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [<span data-ttu-id="5d709-154">dotnet_style_prefer_inferred_anonymous_type_member_names</span><span class="sxs-lookup"><span data-stu-id="5d709-154">dotnet_style_prefer_inferred_anonymous_type_member_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [<span data-ttu-id="5d709-155">dotnet_style_prefer_auto_properties</span><span class="sxs-lookup"><span data-stu-id="5d709-155">dotnet_style_prefer_auto_properties</span></span>](ide0032.md#dotnet_style_prefer_auto_properties)
  - [<span data-ttu-id="5d709-156">dotnet_style_prefer_conditional_expression_over_assignment</span><span class="sxs-lookup"><span data-stu-id="5d709-156">dotnet_style_prefer_conditional_expression_over_assignment</span></span>](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [<span data-ttu-id="5d709-157">dotnet_style_prefer_conditional_expression_over_return</span><span class="sxs-lookup"><span data-stu-id="5d709-157">dotnet_style_prefer_conditional_expression_over_return</span></span>](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [<span data-ttu-id="5d709-158">dotnet_style_prefer_compound_assignment</span><span class="sxs-lookup"><span data-stu-id="5d709-158">dotnet_style_prefer_compound_assignment</span></span>](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [<span data-ttu-id="5d709-159">dotnet_style_prefer_simplified_interpolation</span><span class="sxs-lookup"><span data-stu-id="5d709-159">dotnet_style_prefer_simplified_interpolation</span></span>](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [<span data-ttu-id="5d709-160">dotnet_style_prefer_simplified_boolean_expressions</span><span class="sxs-lookup"><span data-stu-id="5d709-160">dotnet_style_prefer_simplified_boolean_expressions</span></span>](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - <span data-ttu-id="5d709-161">[在 switch 語句中加入遺漏的案例](ide0010.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="5d709-161">[Add missing cases to switch statement](ide0010.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="5d709-162">[將匿名型別轉換為元組](ide0050.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="5d709-162">[Convert anonymous type to tuple](ide0050.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="5d709-163">[使用 ' system.string. 組合 '](ide0070.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="5d709-163">[Use 'System.HashCode.Combine'](ide0070.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="5d709-164">[將 ' typeof ' 轉換成 ' nameof '](ide0082.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="5d709-164">[Convert 'typeof' to 'nameof'](ide0082.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="5d709-165">Null 檢查喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-165">Null-checking preferences</span></span>](null-checking-preferences.md#net-null-checking-preferences)
  - [<span data-ttu-id="5d709-166">dotnet_style_coalesce_expression</span><span class="sxs-lookup"><span data-stu-id="5d709-166">dotnet_style_coalesce_expression</span></span>](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [<span data-ttu-id="5d709-167">dotnet_style_null_propagation</span><span class="sxs-lookup"><span data-stu-id="5d709-167">dotnet_style_null_propagation</span></span>](ide0031.md#dotnet_style_null_propagation)
  - [<span data-ttu-id="5d709-168">dotnet_style_prefer_is_null_check_over_reference_equality_method</span><span class="sxs-lookup"><span data-stu-id="5d709-168">dotnet_style_prefer_is_null_check_over_reference_equality_method</span></span>](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [<span data-ttu-id="5d709-169">檔案標頭喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-169">File header preferences</span></span>](ide0073.md)
  - [<span data-ttu-id="5d709-170">file_header_template</span><span class="sxs-lookup"><span data-stu-id="5d709-170">file_header_template</span></span>](ide0073.md#file_header_template)

## <a name="c-style-rules"></a><span data-ttu-id="5d709-171">C # 樣式規則</span><span class="sxs-lookup"><span data-stu-id="5d709-171">C# style rules</span></span>

<span data-ttu-id="5d709-172">本節中的樣式規則只適用于 c # 語言。</span><span class="sxs-lookup"><span data-stu-id="5d709-172">The style rules in this section are applicable to C# language only.</span></span>

- [<span data-ttu-id="5d709-173">' var ' 喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-173">'var' preferences</span></span>](ide0007-ide0008.md)
  - [<span data-ttu-id="5d709-174">csharp_style_var_for_built_in_types</span><span class="sxs-lookup"><span data-stu-id="5d709-174">csharp_style_var_for_built_in_types</span></span>](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [<span data-ttu-id="5d709-175">csharp_style_var_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="5d709-175">csharp_style_var_when_type_is_apparent</span></span>](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [<span data-ttu-id="5d709-176">csharp_style_var_elsewhere</span><span class="sxs-lookup"><span data-stu-id="5d709-176">csharp_style_var_elsewhere</span></span>](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [<span data-ttu-id="5d709-177">運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="5d709-177">Expression-bodied members</span></span>](expression-bodied-members.md)
  - [<span data-ttu-id="5d709-178">csharp_style_expression_bodied_methods</span><span class="sxs-lookup"><span data-stu-id="5d709-178">csharp_style_expression_bodied_methods</span></span>](ide0022.md#csharp_style_expression_bodied_methods)
  - [<span data-ttu-id="5d709-179">csharp_style_expression_bodied_constructors</span><span class="sxs-lookup"><span data-stu-id="5d709-179">csharp_style_expression_bodied_constructors</span></span>](ide0021.md#csharp_style_expression_bodied_constructors)
  - [<span data-ttu-id="5d709-180">csharp_style_expression_bodied_operators</span><span class="sxs-lookup"><span data-stu-id="5d709-180">csharp_style_expression_bodied_operators</span></span>](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [<span data-ttu-id="5d709-181">csharp_style_expression_bodied_properties</span><span class="sxs-lookup"><span data-stu-id="5d709-181">csharp_style_expression_bodied_properties</span></span>](ide0025.md#csharp_style_expression_bodied_properties)
  - [<span data-ttu-id="5d709-182">csharp_style_expression_bodied_indexers</span><span class="sxs-lookup"><span data-stu-id="5d709-182">csharp_style_expression_bodied_indexers</span></span>](ide0026.md#csharp_style_expression_bodied_indexers)
  - [<span data-ttu-id="5d709-183">csharp_style_expression_bodied_accessors</span><span class="sxs-lookup"><span data-stu-id="5d709-183">csharp_style_expression_bodied_accessors</span></span>](ide0027.md#csharp_style_expression_bodied_accessors)
  - [<span data-ttu-id="5d709-184">csharp_style_expression_bodied_lambdas</span><span class="sxs-lookup"><span data-stu-id="5d709-184">csharp_style_expression_bodied_lambdas</span></span>](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [<span data-ttu-id="5d709-185">csharp_style_expression_bodied_local_functions</span><span class="sxs-lookup"><span data-stu-id="5d709-185">csharp_style_expression_bodied_local_functions</span></span>](ide0061.md#csharp_style_expression_bodied_local_functions)
- [<span data-ttu-id="5d709-186">模式比對喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-186">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="5d709-187">csharp_style_pattern_matching_over_is_with_cast_check</span><span class="sxs-lookup"><span data-stu-id="5d709-187">csharp_style_pattern_matching_over_is_with_cast_check</span></span>](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [<span data-ttu-id="5d709-188">csharp_style_pattern_matching_over_as_with_null_check</span><span class="sxs-lookup"><span data-stu-id="5d709-188">csharp_style_pattern_matching_over_as_with_null_check</span></span>](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [<span data-ttu-id="5d709-189">csharp_style_prefer_switch_expression</span><span class="sxs-lookup"><span data-stu-id="5d709-189">csharp_style_prefer_switch_expression</span></span>](ide0066.md#csharp_style_prefer_switch_expression)
  - [<span data-ttu-id="5d709-190">csharp_style_prefer_pattern_matching</span><span class="sxs-lookup"><span data-stu-id="5d709-190">csharp_style_prefer_pattern_matching</span></span>](ide0078.md#csharp_style_prefer_pattern_matching)
  - [<span data-ttu-id="5d709-191">csharp_style_prefer_not_pattern</span><span class="sxs-lookup"><span data-stu-id="5d709-191">csharp_style_prefer_not_pattern</span></span>](ide0083.md#csharp_style_prefer_not_pattern)
- [<span data-ttu-id="5d709-192">運算式層級喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-192">Expression-level preferences</span></span>](expression-level-preferences.md#c-expression-level-preferences)
  - [<span data-ttu-id="5d709-193">csharp_style_inlined_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="5d709-193">csharp_style_inlined_variable_declaration</span></span>](ide0018.md#csharp_style_inlined_variable_declaration)
  - [<span data-ttu-id="5d709-194">csharp_prefer_simple_default_expression</span><span class="sxs-lookup"><span data-stu-id="5d709-194">csharp_prefer_simple_default_expression</span></span>](ide0034.md#csharp_prefer_simple_default_expression)
  - [<span data-ttu-id="5d709-195">csharp_style_pattern_local_over_anonymous_function</span><span class="sxs-lookup"><span data-stu-id="5d709-195">csharp_style_pattern_local_over_anonymous_function</span></span>](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [<span data-ttu-id="5d709-196">csharp_style_deconstructed_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="5d709-196">csharp_style_deconstructed_variable_declaration</span></span>](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [<span data-ttu-id="5d709-197">csharp_style_prefer_index_operator</span><span class="sxs-lookup"><span data-stu-id="5d709-197">csharp_style_prefer_index_operator</span></span>](ide0056.md#csharp_style_prefer_index_operator)
  - [<span data-ttu-id="5d709-198">csharp_style_prefer_range_operator</span><span class="sxs-lookup"><span data-stu-id="5d709-198">csharp_style_prefer_range_operator</span></span>](ide0057.md#csharp_style_prefer_range_operator)
  - [<span data-ttu-id="5d709-199">csharp_style_implicit_object_creation_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="5d709-199">csharp_style_implicit_object_creation_when_type_is_apparent</span></span>](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - <span data-ttu-id="5d709-200">[將遺漏的案例加入至 switch 運算式](ide0072.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="5d709-200">[Add missing cases to switch expression](ide0072.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="5d709-201">"Null" 檢查喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-201">"Null" checking preferences</span></span>](null-checking-preferences.md#c-null-checking-preferences)
  - [<span data-ttu-id="5d709-202">csharp_style_throw_expression</span><span class="sxs-lookup"><span data-stu-id="5d709-202">csharp_style_throw_expression</span></span>](ide0016.md#csharp_style_throw_expression)
  - [<span data-ttu-id="5d709-203">csharp_style_conditional_delegate_call</span><span class="sxs-lookup"><span data-stu-id="5d709-203">csharp_style_conditional_delegate_call</span></span>](ide1005.md#csharp_style_conditional_delegate_call)
- [<span data-ttu-id="5d709-204">程式碼區塊喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-204">Code block preferences</span></span>](code-block-preferences.md)
  - [<span data-ttu-id="5d709-205">csharp_prefer_braces</span><span class="sxs-lookup"><span data-stu-id="5d709-205">csharp_prefer_braces</span></span>](ide0011.md#csharp_prefer_braces)
  - [<span data-ttu-id="5d709-206">csharp_prefer_simple_using_statement</span><span class="sxs-lookup"><span data-stu-id="5d709-206">csharp_prefer_simple_using_statement</span></span>](ide0063.md#csharp_prefer_simple_using_statement)
- [<span data-ttu-id="5d709-207">' using ' 指示詞喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-207">'using' directive preferences</span></span>](ide0065.md)
  - [<span data-ttu-id="5d709-208">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="5d709-208">csharp_using_directive_placement</span></span>](ide0065.md#csharp_using_directive_placement)
- [<span data-ttu-id="5d709-209">修飾詞喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-209">Modifier preferences</span></span>](modifier-preferences.md#c-modifier-preferences)
  - [<span data-ttu-id="5d709-210">csharp_prefer_static_local_function</span><span class="sxs-lookup"><span data-stu-id="5d709-210">csharp_prefer_static_local_function</span></span>](ide0062.md#csharp_prefer_static_local_function)
  - <span data-ttu-id="5d709-211">[將結構欄位設為可寫入](ide0064.md) -此規則沒有程式碼樣式選項。</span><span class="sxs-lookup"><span data-stu-id="5d709-211">[Make struct fields writable](ide0064.md) - This rule has no code style option.</span></span>

## <a name="visual-basic-style-rules"></a><span data-ttu-id="5d709-212">Visual Basic 樣式規則</span><span class="sxs-lookup"><span data-stu-id="5d709-212">Visual Basic style rules</span></span>

<span data-ttu-id="5d709-213">本節中的樣式規則只適用于 Visual Basic 語言。</span><span class="sxs-lookup"><span data-stu-id="5d709-213">The style rules in this section are applicable to Visual Basic language only.</span></span>

- [<span data-ttu-id="5d709-214">模式比對喜好設定</span><span class="sxs-lookup"><span data-stu-id="5d709-214">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="5d709-215">visual_basic_style_prefer_isnot_expression</span><span class="sxs-lookup"><span data-stu-id="5d709-215">visual_basic_style_prefer_isnot_expression</span></span>](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a><span data-ttu-id="5d709-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d709-216">See also</span></span>

- [<span data-ttu-id="5d709-217">不需要的程式碼規則</span><span class="sxs-lookup"><span data-stu-id="5d709-217">Unnecessary code rules</span></span>](unnecessary-code-rules.md)
- [<span data-ttu-id="5d709-218">格式化規則</span><span class="sxs-lookup"><span data-stu-id="5d709-218">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="5d709-219">命名規則</span><span class="sxs-lookup"><span data-stu-id="5d709-219">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="5d709-220">.NET 程式碼樣式規則參考</span><span class="sxs-lookup"><span data-stu-id="5d709-220">.NET code style rules reference</span></span>](index.md)
