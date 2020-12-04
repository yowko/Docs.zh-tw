---
title: 程式碼樣式格式化規則
description: 深入瞭解格式化縮排、空格和新行的程式碼樣式規則。
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE0055
- formatting rules
helpviewer_keywords:
- IDE0055
- formatting code style rules [EditorConfig]
- formatting rules
- EditorConfig formatting conventions
ms.openlocfilehash: 61e6f6a6afdc6aaf9710eef3143af8ae700ef612
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "96586280"
---
# <a name="formatting-rules"></a><span data-ttu-id="71af9-103">格式化規則</span><span class="sxs-lookup"><span data-stu-id="71af9-103">Formatting rules</span></span>

<span data-ttu-id="71af9-104">格式化規則會影響縮排、空格和新行如何在 .NET 程式設計語言結構的周圍對齊。</span><span class="sxs-lookup"><span data-stu-id="71af9-104">Formatting rules affect how indentation, spaces, and new lines are aligned around .NET programming language constructs.</span></span> <span data-ttu-id="71af9-105">規則分成下列類別：</span><span class="sxs-lookup"><span data-stu-id="71af9-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="71af9-106">[.Net 格式化規則](#net-formatting-rules)：適用于 c # 和 Visual Basic 的規則。</span><span class="sxs-lookup"><span data-stu-id="71af9-106">[.NET formatting rules](#net-formatting-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="71af9-107">這些規則的 EditorConfig 選項名稱會以前置詞開頭 `dotnet_` 。</span><span class="sxs-lookup"><span data-stu-id="71af9-107">The EditorConfig option names for these rules start with `dotnet_` prefix.</span></span>
- <span data-ttu-id="71af9-108">[C # 格式化規則](#c-formatting-rules)：僅適用于 c # 語言的規則。</span><span class="sxs-lookup"><span data-stu-id="71af9-108">[C# formatting rules](#c-formatting-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="71af9-109">這些規則的 EditorConfig 選項名稱會以前置詞開頭 `csharp_` 。</span><span class="sxs-lookup"><span data-stu-id="71af9-109">The EditorConfig option names for these rules start with `csharp_` prefix.</span></span>

## <a name="rule-id-ide0055-fix-formatting"></a><span data-ttu-id="71af9-110">規則識別碼： "IDE0055" (修正格式) </span><span class="sxs-lookup"><span data-stu-id="71af9-110">Rule ID: "IDE0055" (Fix formatting)</span></span>

<span data-ttu-id="71af9-111">所有格式化選項都有規則識別碼 `IDE0055` 和標題 `Fix formatting` 。</span><span class="sxs-lookup"><span data-stu-id="71af9-111">All formatting options have rule ID `IDE0055` and title `Fix formatting`.</span></span> <span data-ttu-id="71af9-112">使用下列設定行，在 EditorConfig 檔中設定格式違規的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="71af9-112">Set the severity of a formatting violation in an EditorConfig file using the following configuration line.</span></span>

```ini
dotnet_diagnostic.IDE0055.severity = <severity value>
```

<span data-ttu-id="71af9-113">嚴重性值必須是 `warning` 或 `error` [在組建時強制執行](../overview.md#code-style-analysis)。</span><span class="sxs-lookup"><span data-stu-id="71af9-113">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="71af9-114">如需所有可能的嚴重性值，請參閱 [嚴重性層級](../configuration-options.md#severity-level)。</span><span class="sxs-lookup"><span data-stu-id="71af9-114">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="option-format"></a><span data-ttu-id="71af9-115">選項格式</span><span class="sxs-lookup"><span data-stu-id="71af9-115">Option format</span></span>

<span data-ttu-id="71af9-116">您可以使用下列格式，在 EditorConfig 檔中指定格式化規則的選項：</span><span class="sxs-lookup"><span data-stu-id="71af9-116">Options for formatting rules can be specified in an EditorConfig file with the following format:</span></span>

`rule_name = value`

<span data-ttu-id="71af9-117">對於許多格式來說，您可以針對 `value` 指定 `true` (慣用此樣式) 或 `false` (不喜好此樣式)。</span><span class="sxs-lookup"><span data-stu-id="71af9-117">For many rules, you specify either `true` (prefer this style) or `false` (do not prefer this style) for `value`.</span></span> <span data-ttu-id="71af9-118">針對其他規則，您可以指定像是 `flush_left` 或 `before_and_after` 這樣的值，以描述套用規則的時間與位置。</span><span class="sxs-lookup"><span data-stu-id="71af9-118">For other rules, you specify a value such as `flush_left` or `before_and_after` to describe when and where to apply the rule.</span></span> <span data-ttu-id="71af9-119">您不用指定嚴重性。</span><span class="sxs-lookup"><span data-stu-id="71af9-119">You don't specify a severity.</span></span>

## <a name="net-formatting-rules"></a><span data-ttu-id="71af9-120">.NET 格式化規則</span><span class="sxs-lookup"><span data-stu-id="71af9-120">.NET formatting rules</span></span>

<span data-ttu-id="71af9-121">本節中的格式化規則適用于 c # 和 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="71af9-121">The formatting rules in this section apply to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="71af9-122">召集人 using</span><span class="sxs-lookup"><span data-stu-id="71af9-122">Organize usings</span></span>](#organize-using-directives)
  - <span data-ttu-id="71af9-123">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="71af9-123">dotnet_sort_system_directives_first</span></span>
  - <span data-ttu-id="71af9-124">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="71af9-124">dotnet_separate_import_directive_groups</span></span>

### <a name="organize-using-directives"></a><span data-ttu-id="71af9-125">組織 using 指示詞</span><span class="sxs-lookup"><span data-stu-id="71af9-125">Organize using directives</span></span>

<span data-ttu-id="71af9-126">這些格式化規則是關於 `using` 指示詞和 `Imports` 陳述式的排序和顯示。</span><span class="sxs-lookup"><span data-stu-id="71af9-126">These formatting rules concern the sorting and display of `using` directives and `Imports` statements.</span></span>

<span data-ttu-id="71af9-127">Editorconfig 檔案範例︰</span><span class="sxs-lookup"><span data-stu-id="71af9-127">Example *.editorconfig* file:</span></span>

```ini
# .NET formatting rules
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a><span data-ttu-id="71af9-128">dotnet\_sort\_system\_directives_first</span><span class="sxs-lookup"><span data-stu-id="71af9-128">dotnet\_sort\_system\_directives_first</span></span>

|<span data-ttu-id="71af9-129">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-129">Property</span></span>|<span data-ttu-id="71af9-130">值</span><span class="sxs-lookup"><span data-stu-id="71af9-130">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-131">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-131">**Option name**</span></span> | <span data-ttu-id="71af9-132">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="71af9-132">dotnet_sort_system_directives_first</span></span> |
| <span data-ttu-id="71af9-133">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-133">**Applicable languages**</span></span> | <span data-ttu-id="71af9-134">C# 和 Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71af9-134">C# and Visual Basic</span></span> |
| <span data-ttu-id="71af9-135">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-135">**Introduced version**</span></span> | <span data-ttu-id="71af9-136">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-136">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-137">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-137">**Option values**</span></span> | <span data-ttu-id="71af9-138">`true` -依字母順序排序指示詞 `System.*` `using` ，並將它們放在其他 using 指示詞之前。</span><span class="sxs-lookup"><span data-stu-id="71af9-138">`true` - Sort `System.*` `using` directives alphabetically, and place them before other using directives.</span></span><br /><br /><span data-ttu-id="71af9-139">`false` -請勿將指示詞放置 `System.*` `using` 在其他指示詞之前 `using` 。</span><span class="sxs-lookup"><span data-stu-id="71af9-139">`false` - Do not place `System.*` `using` directives before other `using` directives.</span></span> |

<span data-ttu-id="71af9-140">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-140">Code examples:</span></span>

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnet_separate_import_directive_groups"></a><span data-ttu-id="71af9-141">dotnet\_separate\_import\_directive\_groups</span><span class="sxs-lookup"><span data-stu-id="71af9-141">dotnet\_separate\_import\_directive\_groups</span></span>

|<span data-ttu-id="71af9-142">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-142">Property</span></span>|<span data-ttu-id="71af9-143">值</span><span class="sxs-lookup"><span data-stu-id="71af9-143">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-144">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-144">**Option name**</span></span> | <span data-ttu-id="71af9-145">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="71af9-145">dotnet_separate_import_directive_groups</span></span> |
| <span data-ttu-id="71af9-146">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-146">**Applicable languages**</span></span> | <span data-ttu-id="71af9-147">C# 和 Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71af9-147">C# and Visual Basic</span></span> |
| <span data-ttu-id="71af9-148">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-148">**Introduced version**</span></span> | <span data-ttu-id="71af9-149">Visual Studio 2017 15.5 版</span><span class="sxs-lookup"><span data-stu-id="71af9-149">Visual Studio 2017 version 15.5</span></span> |
| <span data-ttu-id="71af9-150">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-150">**Option values**</span></span> | <span data-ttu-id="71af9-151">`true` - 在 `using` 指示詞群組之間放置空白行。</span><span class="sxs-lookup"><span data-stu-id="71af9-151">`true` - Place a blank line between `using` directive groups.</span></span><br /><br /><span data-ttu-id="71af9-152">`false` - 在 `using` 指示詞群組之間放置空白行。</span><span class="sxs-lookup"><span data-stu-id="71af9-152">`false` - Do not place a blank line between `using` directive groups.</span></span> |

<span data-ttu-id="71af9-153">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-153">Code examples:</span></span>

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-rules"></a><span data-ttu-id="71af9-154">C # 格式化規則</span><span class="sxs-lookup"><span data-stu-id="71af9-154">C# formatting rules</span></span>

<span data-ttu-id="71af9-155">本節中的格式化規則只適用於 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="71af9-155">The formatting rules in this section apply only to C# code.</span></span>

- [<span data-ttu-id="71af9-156">換行選項</span><span class="sxs-lookup"><span data-stu-id="71af9-156">Newline options</span></span>](#new-line-options)
  - <span data-ttu-id="71af9-157">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="71af9-157">csharp_new_line_before_open_brace</span></span>
  - <span data-ttu-id="71af9-158">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="71af9-158">csharp_new_line_before_else</span></span>
  - <span data-ttu-id="71af9-159">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="71af9-159">csharp_new_line_before_catch</span></span>
  - <span data-ttu-id="71af9-160">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="71af9-160">csharp_new_line_before_finally</span></span>
  - <span data-ttu-id="71af9-161">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="71af9-161">csharp_new_line_before_members_in_object_initializers</span></span>
  - <span data-ttu-id="71af9-162">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="71af9-162">csharp_new_line_before_members_in_anonymous_types</span></span>
  - <span data-ttu-id="71af9-163">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="71af9-163">csharp_new_line_between_query_expression_clauses</span></span>
- [<span data-ttu-id="71af9-164">縮排選項</span><span class="sxs-lookup"><span data-stu-id="71af9-164">Indentation options</span></span>](#indentation-options)
  - <span data-ttu-id="71af9-165">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="71af9-165">csharp_indent_case_contents</span></span>
  - <span data-ttu-id="71af9-166">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="71af9-166">csharp_indent_switch_labels</span></span>
  - <span data-ttu-id="71af9-167">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="71af9-167">csharp_indent_labels</span></span>
  - <span data-ttu-id="71af9-168">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="71af9-168">csharp_indent_block_contents</span></span>
  - <span data-ttu-id="71af9-169">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="71af9-169">csharp_indent_braces</span></span>
  - <span data-ttu-id="71af9-170">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="71af9-170">csharp_indent_case_contents_when_block</span></span>
- [<span data-ttu-id="71af9-171">間距選項</span><span class="sxs-lookup"><span data-stu-id="71af9-171">Spacing options</span></span>](#spacing-options)
  - <span data-ttu-id="71af9-172">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="71af9-172">csharp_space_after_cast</span></span>
  - <span data-ttu-id="71af9-173">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="71af9-173">csharp_space_after_keywords_in_control_flow_statements</span></span>
  - <span data-ttu-id="71af9-174">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-174">csharp_space_between_parentheses</span></span>
  - <span data-ttu-id="71af9-175">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="71af9-175">csharp_space_before_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="71af9-176">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="71af9-176">csharp_space_after_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="71af9-177">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="71af9-177">csharp_space_around_binary_operators</span></span>
  - <span data-ttu-id="71af9-178">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-178">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>
  - <span data-ttu-id="71af9-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="71af9-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="71af9-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>
  - <span data-ttu-id="71af9-181">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-181">csharp_space_between_method_call_parameter_list_parentheses</span></span>
  - <span data-ttu-id="71af9-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="71af9-183">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="71af9-183">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>
  - <span data-ttu-id="71af9-184">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="71af9-184">csharp_space_after_comma</span></span>
  - <span data-ttu-id="71af9-185">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="71af9-185">csharp_space_before_comma</span></span>
  - <span data-ttu-id="71af9-186">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="71af9-186">csharp_space_after_dot</span></span>
  - <span data-ttu-id="71af9-187">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="71af9-187">csharp_space_before_dot</span></span>
  - <span data-ttu-id="71af9-188">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="71af9-188">csharp_space_after_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="71af9-189">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="71af9-189">csharp_space_before_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="71af9-190">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="71af9-190">csharp_space_around_declaration_statements</span></span>
  - <span data-ttu-id="71af9-191">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="71af9-191">csharp_space_before_open_square_brackets</span></span>
  - <span data-ttu-id="71af9-192">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="71af9-192">csharp_space_between_empty_square_brackets</span></span>
  - <span data-ttu-id="71af9-193">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="71af9-193">csharp_space_between_square_brackets</span></span>
- [<span data-ttu-id="71af9-194">包裝選項</span><span class="sxs-lookup"><span data-stu-id="71af9-194">Wrap options</span></span>](#wrap-options)
  - <span data-ttu-id="71af9-195">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="71af9-195">csharp_preserve_single_line_statements</span></span>
  - <span data-ttu-id="71af9-196">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="71af9-196">csharp_preserve_single_line_blocks</span></span>
- [<span data-ttu-id="71af9-197">Using 指示詞選項</span><span class="sxs-lookup"><span data-stu-id="71af9-197">Using directive options</span></span>](#using-directive-options)
  - <span data-ttu-id="71af9-198">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="71af9-198">csharp_using_directive_placement</span></span>

### <a name="new-line-options"></a><span data-ttu-id="71af9-199">新行選項</span><span class="sxs-lookup"><span data-stu-id="71af9-199">New-line options</span></span>

<span data-ttu-id="71af9-200">這些格式化規則是關於格式化程式碼新行的使用。</span><span class="sxs-lookup"><span data-stu-id="71af9-200">These formatting rules concern the use of new lines to format code.</span></span>

<span data-ttu-id="71af9-201">Editorconfig 檔案範例︰</span><span class="sxs-lookup"><span data-stu-id="71af9-201">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharp_new_line_before_open_brace"></a><span data-ttu-id="71af9-202">csharp\_new\_line\_before\_open_brace</span><span class="sxs-lookup"><span data-stu-id="71af9-202">csharp\_new\_line\_before\_open_brace</span></span>

<span data-ttu-id="71af9-203">此規則是有關左大括弧 `{` 應該和前面的程式碼放在同一行還是放在新行中。</span><span class="sxs-lookup"><span data-stu-id="71af9-203">This rule concerns whether an open brace `{` should be placed on the same line as the preceding code, or on a new line.</span></span> <span data-ttu-id="71af9-204">針對此規則，您可以指定 [全部]、[無] 或一或多個程式碼項目，例如 **方法** 或 **屬性**，來定義應於何時套用此規則。</span><span class="sxs-lookup"><span data-stu-id="71af9-204">For this rule, you specify **all**, **none**, or one or more code elements such as **methods** or **properties**, to define when this rule should be applied.</span></span> <span data-ttu-id="71af9-205">若要指定多個程式碼項目，請使用逗號 (,) 區隔。</span><span class="sxs-lookup"><span data-stu-id="71af9-205">To specify multiple code elements, separate them with a comma (,).</span></span>

|<span data-ttu-id="71af9-206">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-206">Property</span></span>|<span data-ttu-id="71af9-207">值</span><span class="sxs-lookup"><span data-stu-id="71af9-207">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-208">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-208">**Option name**</span></span> | <span data-ttu-id="71af9-209">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="71af9-209">csharp_new_line_before_open_brace</span></span> |
| <span data-ttu-id="71af9-210">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-210">**Applicable languages**</span></span> | <span data-ttu-id="71af9-211">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-211">C#</span></span> |
| <span data-ttu-id="71af9-212">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-212">**Introduced version**</span></span> | <span data-ttu-id="71af9-213">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-213">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-214">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-214">**Option values**</span></span> | <span data-ttu-id="71af9-215">`all` - 針對所有運算式要求大括弧位於新行上 ("Allman" 樣式)。</span><span class="sxs-lookup"><span data-stu-id="71af9-215">`all` - Require braces to be on a new line for all expressions ("Allman" style).</span></span><br /><br /><span data-ttu-id="71af9-216">`none` - 針對所有運算式要求大括弧位於同一行上 ("K&R")。</span><span class="sxs-lookup"><span data-stu-id="71af9-216">`none` - Require braces to be on the same line for all expressions ("K&R").</span></span><br /><br /><span data-ttu-id="71af9-217">`accessors`、`anonymous_methods`、`anonymous_types`、`control_blocks`、`events`、`indexers`、`lambdas`、`local_functions`、`methods`、`object_collection_array_initializers`、`properties`、`types` - 針對指定的程式碼項目要求大括弧位於新行 ("Allman" 樣式)。</span><span class="sxs-lookup"><span data-stu-id="71af9-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Require braces to be on a new line for the specified code element ("Allman" style).</span></span> |

<span data-ttu-id="71af9-218">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-218">Code examples:</span></span>

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharp_new_line_before_else"></a><span data-ttu-id="71af9-219">csharp\_new\_line\_before_else</span><span class="sxs-lookup"><span data-stu-id="71af9-219">csharp\_new\_line\_before_else</span></span>

|<span data-ttu-id="71af9-220">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-220">Property</span></span>|<span data-ttu-id="71af9-221">值</span><span class="sxs-lookup"><span data-stu-id="71af9-221">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-222">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-222">**Option name**</span></span> | <span data-ttu-id="71af9-223">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="71af9-223">csharp_new_line_before_else</span></span> |
| <span data-ttu-id="71af9-224">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-224">**Applicable languages**</span></span> | <span data-ttu-id="71af9-225">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-225">C#</span></span> |
| <span data-ttu-id="71af9-226">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-226">**Introduced version**</span></span> | <span data-ttu-id="71af9-227">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-227">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-228">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-228">**Option values**</span></span> | <span data-ttu-id="71af9-229">`true` - 將 `else` 陳述式置於新行上。</span><span class="sxs-lookup"><span data-stu-id="71af9-229">`true` - Place `else` statements on a new line.</span></span><br /><br /><span data-ttu-id="71af9-230">`false` - 將 `else` 陳述式置於同一行上。</span><span class="sxs-lookup"><span data-stu-id="71af9-230">`false` - Place `else` statements on the same line.</span></span> |

<span data-ttu-id="71af9-231">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-231">Code examples:</span></span>

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharp_new_line_before_catch"></a><span data-ttu-id="71af9-232">csharp\_new\_line\_before_catch</span><span class="sxs-lookup"><span data-stu-id="71af9-232">csharp\_new\_line\_before_catch</span></span>

|<span data-ttu-id="71af9-233">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-233">Property</span></span>|<span data-ttu-id="71af9-234">值</span><span class="sxs-lookup"><span data-stu-id="71af9-234">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-235">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-235">**Option name**</span></span> | <span data-ttu-id="71af9-236">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="71af9-236">csharp_new_line_before_catch</span></span> |
| <span data-ttu-id="71af9-237">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-237">**Applicable languages**</span></span> | <span data-ttu-id="71af9-238">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-238">C#</span></span> |
| <span data-ttu-id="71af9-239">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-239">**Introduced version**</span></span> | <span data-ttu-id="71af9-240">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-240">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-241">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-241">**Option values**</span></span> | <span data-ttu-id="71af9-242">`true` - 將 `catch` 陳述式置於新行上。</span><span class="sxs-lookup"><span data-stu-id="71af9-242">`true` - Place `catch` statements on a new line.</span></span><br /><br /><span data-ttu-id="71af9-243">`false` - 將 `catch` 陳述式置於同一行上。</span><span class="sxs-lookup"><span data-stu-id="71af9-243">`false` - Place `catch` statements on the same line.</span></span> |

<span data-ttu-id="71af9-244">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-244">Code examples:</span></span>

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharp_new_line_before_finally"></a><span data-ttu-id="71af9-245">csharp\_new\_line\_before_finally</span><span class="sxs-lookup"><span data-stu-id="71af9-245">csharp\_new\_line\_before_finally</span></span>

|<span data-ttu-id="71af9-246">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-246">Property</span></span>|<span data-ttu-id="71af9-247">值</span><span class="sxs-lookup"><span data-stu-id="71af9-247">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-248">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-248">**Option name**</span></span> | <span data-ttu-id="71af9-249">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="71af9-249">csharp_new_line_before_finally</span></span> |
| <span data-ttu-id="71af9-250">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-250">**Applicable languages**</span></span> | <span data-ttu-id="71af9-251">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-251">C#</span></span> |
| <span data-ttu-id="71af9-252">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-252">**Introduced version**</span></span> | <span data-ttu-id="71af9-253">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-253">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-254">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-254">**Option values**</span></span> | <span data-ttu-id="71af9-255">`true` - 要求 `finally` 陳述式位於右大括號之後的新行上。</span><span class="sxs-lookup"><span data-stu-id="71af9-255">`true` - Require `finally` statements to be on a new line after the closing brace.</span></span><br /><br /><span data-ttu-id="71af9-256">`false` - 要求 `finally` 陳述式位於右大括號的同一行上。</span><span class="sxs-lookup"><span data-stu-id="71af9-256">`false` - Require `finally` statements to be on the same line as the closing brace.</span></span> |

<span data-ttu-id="71af9-257">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-257">Code examples:</span></span>

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharp_new_line_before_members_in_object_initializers"></a><span data-ttu-id="71af9-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span><span class="sxs-lookup"><span data-stu-id="71af9-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span></span>

|<span data-ttu-id="71af9-259">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-259">Property</span></span>|<span data-ttu-id="71af9-260">值</span><span class="sxs-lookup"><span data-stu-id="71af9-260">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-261">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-261">**Option name**</span></span> | <span data-ttu-id="71af9-262">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="71af9-262">csharp_new_line_before_members_in_object_initializers</span></span> |
| <span data-ttu-id="71af9-263">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-263">**Applicable languages**</span></span> | <span data-ttu-id="71af9-264">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-264">C#</span></span> |
| <span data-ttu-id="71af9-265">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-265">**Introduced version**</span></span> | <span data-ttu-id="71af9-266">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-266">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-267">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-267">**Option values**</span></span> | <span data-ttu-id="71af9-268">`true` - 要求物件初始設定式的成員位於不同行上</span><span class="sxs-lookup"><span data-stu-id="71af9-268">`true` - Require members of object initializers to be on separate lines</span></span><br /><br /><span data-ttu-id="71af9-269">`false` - 要求物件初始設定式的成員位於同一行上</span><span class="sxs-lookup"><span data-stu-id="71af9-269">`false` - Require members of object initializers to be on the same line</span></span> |

<span data-ttu-id="71af9-270">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-270">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a><span data-ttu-id="71af9-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="71af9-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span></span>

|<span data-ttu-id="71af9-272">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-272">Property</span></span>|<span data-ttu-id="71af9-273">值</span><span class="sxs-lookup"><span data-stu-id="71af9-273">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-274">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-274">**Option name**</span></span> | <span data-ttu-id="71af9-275">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="71af9-275">csharp_new_line_before_members_in_anonymous_types</span></span> |
| <span data-ttu-id="71af9-276">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-276">**Applicable languages**</span></span> | <span data-ttu-id="71af9-277">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-277">C#</span></span> |
| <span data-ttu-id="71af9-278">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-278">**Introduced version**</span></span> | <span data-ttu-id="71af9-279">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-279">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-280">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-280">**Option values**</span></span> | <span data-ttu-id="71af9-281">`true` - 要求匿名類型的成員位於不同行上</span><span class="sxs-lookup"><span data-stu-id="71af9-281">`true` - Require members of anonymous types to be on separate lines</span></span><br /><br /><span data-ttu-id="71af9-282">`false` - 要求匿名類型的成員位於同一行上</span><span class="sxs-lookup"><span data-stu-id="71af9-282">`false` - Require members of anonymous types to be on the same line</span></span> |

<span data-ttu-id="71af9-283">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-283">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_between_query_expression_clauses"></a><span data-ttu-id="71af9-284">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="71af9-284">csharp_new_line_between_query_expression_clauses</span></span>

|<span data-ttu-id="71af9-285">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-285">Property</span></span>|<span data-ttu-id="71af9-286">值</span><span class="sxs-lookup"><span data-stu-id="71af9-286">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-287">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-287">**Option name**</span></span> | <span data-ttu-id="71af9-288">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="71af9-288">csharp_new_line_between_query_expression_clauses</span></span> |
| <span data-ttu-id="71af9-289">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-289">**Applicable languages**</span></span> | <span data-ttu-id="71af9-290">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-290">C#</span></span> |
| <span data-ttu-id="71af9-291">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-291">**Introduced version**</span></span> | <span data-ttu-id="71af9-292">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-292">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-293">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-293">**Option values**</span></span> | <span data-ttu-id="71af9-294">`true` - 要求查詢運算式子句的元素位於不同行上</span><span class="sxs-lookup"><span data-stu-id="71af9-294">`true` - Require elements of query expression clauses to be on separate lines</span></span><br /><br /><span data-ttu-id="71af9-295">`false` - 要求查詢運算式子句的元素位於同一行上</span><span class="sxs-lookup"><span data-stu-id="71af9-295">`false` - Require elements of query expression clauses to be on the same line</span></span> |

<span data-ttu-id="71af9-296">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-296">Code examples:</span></span>

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a><span data-ttu-id="71af9-297">縮排選項</span><span class="sxs-lookup"><span data-stu-id="71af9-297">Indentation options</span></span>

<span data-ttu-id="71af9-298">這些格式化規則是關於格式化程式碼縮排的使用。</span><span class="sxs-lookup"><span data-stu-id="71af9-298">These formatting rules concern the use of indentation to format code.</span></span>

<span data-ttu-id="71af9-299">Editorconfig 檔案範例︰</span><span class="sxs-lookup"><span data-stu-id="71af9-299">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a><span data-ttu-id="71af9-300">csharp\_indent\_case_contents</span><span class="sxs-lookup"><span data-stu-id="71af9-300">csharp\_indent\_case_contents</span></span>

|<span data-ttu-id="71af9-301">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-301">Property</span></span>|<span data-ttu-id="71af9-302">值</span><span class="sxs-lookup"><span data-stu-id="71af9-302">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-303">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-303">**Option name**</span></span> | <span data-ttu-id="71af9-304">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="71af9-304">csharp_indent_case_contents</span></span> |
| <span data-ttu-id="71af9-305">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-305">**Applicable languages**</span></span> | <span data-ttu-id="71af9-306">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-306">C#</span></span> |
| <span data-ttu-id="71af9-307">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-307">**Introduced version**</span></span> | <span data-ttu-id="71af9-308">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-308">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-309">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-309">**Option values**</span></span> | <span data-ttu-id="71af9-310">`true` - 對 `switch` 案例內容進行縮排</span><span class="sxs-lookup"><span data-stu-id="71af9-310">`true` - Indent `switch` case contents</span></span><br /><br /><span data-ttu-id="71af9-311">`false` - 不對 `switch` 案例內容進行縮排</span><span class="sxs-lookup"><span data-stu-id="71af9-311">`false` - Do not indent `switch` case contents</span></span> |

- <span data-ttu-id="71af9-312">當此規則設定為 **true**，為 i。</span><span class="sxs-lookup"><span data-stu-id="71af9-312">When this rule is set to **true**, i.</span></span>
- <span data-ttu-id="71af9-313">當此規則設為 **false** 時，為 d。</span><span class="sxs-lookup"><span data-stu-id="71af9-313">When this rule is set to **false**, d.</span></span>

<span data-ttu-id="71af9-314">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-314">Code examples:</span></span>

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_switch_labels"></a><span data-ttu-id="71af9-315">csharp\_indent\_switch_labels</span><span class="sxs-lookup"><span data-stu-id="71af9-315">csharp\_indent\_switch_labels</span></span>

|<span data-ttu-id="71af9-316">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-316">Property</span></span>|<span data-ttu-id="71af9-317">值</span><span class="sxs-lookup"><span data-stu-id="71af9-317">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-318">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-318">**Option name**</span></span> | <span data-ttu-id="71af9-319">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="71af9-319">csharp_indent_switch_labels</span></span> |
| <span data-ttu-id="71af9-320">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-320">**Applicable languages**</span></span> | <span data-ttu-id="71af9-321">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-321">C#</span></span> |
| <span data-ttu-id="71af9-322">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-322">**Introduced version**</span></span> | <span data-ttu-id="71af9-323">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-323">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-324">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-324">**Option values**</span></span> | <span data-ttu-id="71af9-325">`true` - 縮排 `switch` 標籤</span><span class="sxs-lookup"><span data-stu-id="71af9-325">`true` - Indent `switch` labels</span></span><br /><br /><span data-ttu-id="71af9-326">`false` - 不要縮排 `switch` 標籤</span><span class="sxs-lookup"><span data-stu-id="71af9-326">`false` - Do not indent `switch` labels</span></span> |

<span data-ttu-id="71af9-327">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-327">Code examples:</span></span>

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_labels"></a><span data-ttu-id="71af9-328">csharp\_indent_labels</span><span class="sxs-lookup"><span data-stu-id="71af9-328">csharp\_indent_labels</span></span>

|<span data-ttu-id="71af9-329">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-329">Property</span></span>|<span data-ttu-id="71af9-330">值</span><span class="sxs-lookup"><span data-stu-id="71af9-330">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-331">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-331">**Option name**</span></span> | <span data-ttu-id="71af9-332">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="71af9-332">csharp_indent_labels</span></span> |
| <span data-ttu-id="71af9-333">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-333">**Applicable languages**</span></span> | <span data-ttu-id="71af9-334">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-334">C#</span></span> |
| <span data-ttu-id="71af9-335">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-335">**Introduced version**</span></span> | <span data-ttu-id="71af9-336">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-336">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-337">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-337">**Option values**</span></span> | <span data-ttu-id="71af9-338">`flush_left` - 標籤放在最左邊的資料行</span><span class="sxs-lookup"><span data-stu-id="71af9-338">`flush_left` - Labels are placed at the leftmost column</span></span><br /><br /><span data-ttu-id="71af9-339">`one_less_than_current` - 將標籤置於比目前內容的縮排少一個單位的位置</span><span class="sxs-lookup"><span data-stu-id="71af9-339">`one_less_than_current` - Labels are placed at one less indent to the current context</span></span><br /><br /><span data-ttu-id="71af9-340">`no_change` - 將標籤置於和目前內容相同縮排的位置</span><span class="sxs-lookup"><span data-stu-id="71af9-340">`no_change` - Labels are placed at the same indent as the current context</span></span> |

<span data-ttu-id="71af9-341">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-341">Code examples:</span></span>

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### <a name="csharp_indent_block_contents"></a><span data-ttu-id="71af9-342">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="71af9-342">csharp_indent_block_contents</span></span>

|<span data-ttu-id="71af9-343">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-343">Property</span></span>|<span data-ttu-id="71af9-344">值</span><span class="sxs-lookup"><span data-stu-id="71af9-344">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-345">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-345">**Option name**</span></span> | <span data-ttu-id="71af9-346">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="71af9-346">csharp_indent_block_contents</span></span> |
| <span data-ttu-id="71af9-347">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-347">**Applicable languages**</span></span> | <span data-ttu-id="71af9-348">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-348">C#</span></span> |
| <span data-ttu-id="71af9-349">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-349">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="71af9-350">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-350">Code examples:</span></span>

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a><span data-ttu-id="71af9-351">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="71af9-351">csharp_indent_braces</span></span>

|<span data-ttu-id="71af9-352">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-352">Property</span></span>|<span data-ttu-id="71af9-353">值</span><span class="sxs-lookup"><span data-stu-id="71af9-353">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-354">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-354">**Option name**</span></span> | <span data-ttu-id="71af9-355">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="71af9-355">csharp_indent_braces</span></span> |
| <span data-ttu-id="71af9-356">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-356">**Applicable languages**</span></span> | <span data-ttu-id="71af9-357">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-357">C#</span></span> |
| <span data-ttu-id="71af9-358">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-358">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="71af9-359">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-359">Code examples:</span></span>

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a><span data-ttu-id="71af9-360">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="71af9-360">csharp_indent_case_contents_when_block</span></span>

|<span data-ttu-id="71af9-361">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-361">Property</span></span>|<span data-ttu-id="71af9-362">值</span><span class="sxs-lookup"><span data-stu-id="71af9-362">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-363">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-363">**Option name**</span></span> | <span data-ttu-id="71af9-364">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="71af9-364">csharp_indent_case_contents_when_block</span></span> |
| <span data-ttu-id="71af9-365">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-365">**Applicable languages**</span></span> | <span data-ttu-id="71af9-366">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-366">C#</span></span> |
| <span data-ttu-id="71af9-367">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-367">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="71af9-368">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-368">Code examples:</span></span>

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a><span data-ttu-id="71af9-369">間距選項</span><span class="sxs-lookup"><span data-stu-id="71af9-369">Spacing options</span></span>

<span data-ttu-id="71af9-370">這些格式化規則是關於格式化程式碼空白字元的使用。</span><span class="sxs-lookup"><span data-stu-id="71af9-370">These formatting rules concern the use of space characters to format code.</span></span>

<span data-ttu-id="71af9-371">Editorconfig 檔案範例︰</span><span class="sxs-lookup"><span data-stu-id="71af9-371">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a><span data-ttu-id="71af9-372">csharp\_space\_after_cast</span><span class="sxs-lookup"><span data-stu-id="71af9-372">csharp\_space\_after_cast</span></span>

|<span data-ttu-id="71af9-373">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-373">Property</span></span>|<span data-ttu-id="71af9-374">值</span><span class="sxs-lookup"><span data-stu-id="71af9-374">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-375">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-375">**Option name**</span></span> | <span data-ttu-id="71af9-376">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="71af9-376">csharp_space_after_cast</span></span> |
| <span data-ttu-id="71af9-377">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-377">**Applicable languages**</span></span> | <span data-ttu-id="71af9-378">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-378">C#</span></span> |
| <span data-ttu-id="71af9-379">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-379">**Introduced version**</span></span> | <span data-ttu-id="71af9-380">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-380">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-381">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-381">**Option values**</span></span> | <span data-ttu-id="71af9-382">`true` - 在轉換和值之間放入一個空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-382">`true` - Place a space character between a cast and the value</span></span><br /><br /><span data-ttu-id="71af9-383">`false` - 移除轉換和值之間的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-383">`false` - Remove space between the cast and the value</span></span> |

<span data-ttu-id="71af9-384">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-384">Code examples:</span></span>

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a><span data-ttu-id="71af9-385">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="71af9-385">csharp_space_after_keywords_in_control_flow_statements</span></span>

|<span data-ttu-id="71af9-386">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-386">Property</span></span>|<span data-ttu-id="71af9-387">值</span><span class="sxs-lookup"><span data-stu-id="71af9-387">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-388">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-388">**Option name**</span></span> | <span data-ttu-id="71af9-389">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="71af9-389">csharp_space_after_keywords_in_control_flow_statements</span></span> |
| <span data-ttu-id="71af9-390">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-390">**Applicable languages**</span></span> | <span data-ttu-id="71af9-391">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-391">C#</span></span> |
| <span data-ttu-id="71af9-392">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-392">**Introduced version**</span></span> | <span data-ttu-id="71af9-393">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-393">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-394">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-394">**Option values**</span></span> | <span data-ttu-id="71af9-395">`true` - 在控制流程陳述式中的關鍵字後面放入一個空白字元，例如 `for` 迴圈</span><span class="sxs-lookup"><span data-stu-id="71af9-395">`true` - Place a space character after a keyword in a control flow statement such as a `for` loop</span></span><br /><br /><span data-ttu-id="71af9-396">`false` - 移除控制流程陳述式中關鍵字後面的空格，例如 `for` 迴圈</span><span class="sxs-lookup"><span data-stu-id="71af9-396">`false` - Remove space after a keyword in a control flow statement such as a `for` loop</span></span> |

<span data-ttu-id="71af9-397">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-397">Code examples:</span></span>

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a><span data-ttu-id="71af9-398">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-398">csharp_space_between_parentheses</span></span>

|<span data-ttu-id="71af9-399">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-399">Property</span></span>|<span data-ttu-id="71af9-400">值</span><span class="sxs-lookup"><span data-stu-id="71af9-400">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-401">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-401">**Option name**</span></span> | <span data-ttu-id="71af9-402">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-402">csharp_space_between_parentheses</span></span> |
| <span data-ttu-id="71af9-403">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-403">**Applicable languages**</span></span> | <span data-ttu-id="71af9-404">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-404">C#</span></span> |
| <span data-ttu-id="71af9-405">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-405">**Introduced version**</span></span> | <span data-ttu-id="71af9-406">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-406">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-407">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-407">**Option values**</span></span> | <span data-ttu-id="71af9-408">`control_flow_statements` - 在控制流程陳述式的括號之間加入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-408">`control_flow_statements` - Place space between parentheses of control flow statements</span></span><br /><br /><span data-ttu-id="71af9-409">`expressions` - 在運算式的括號之間加入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-409">`expressions` - Place space between parentheses of expressions</span></span><br /><br /><span data-ttu-id="71af9-410">`type_casts` - 在類型轉換中的括號之間加入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-410">`type_casts` - Place space between parentheses in type casts</span></span> |

<span data-ttu-id="71af9-411">如果您略過此規則，或使用 `control_flow_statements`、`expressions` 或 `type_casts` 以外的值，即不套用設定。</span><span class="sxs-lookup"><span data-stu-id="71af9-411">If you omit this rule or use a value other than `control_flow_statements`, `expressions`, or `type_casts`, the setting is not applied.</span></span>

<span data-ttu-id="71af9-412">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-412">Code examples:</span></span>

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a><span data-ttu-id="71af9-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="71af9-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="71af9-414">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-414">Property</span></span>|<span data-ttu-id="71af9-415">值</span><span class="sxs-lookup"><span data-stu-id="71af9-415">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-416">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-416">**Option name**</span></span> | <span data-ttu-id="71af9-417">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="71af9-417">csharp_space_before_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="71af9-418">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-418">**Applicable languages**</span></span> | <span data-ttu-id="71af9-419">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-419">C#</span></span> |
| <span data-ttu-id="71af9-420">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-420">**Introduced version**</span></span> | <span data-ttu-id="71af9-421">Visual Studio 2017 15.7 版</span><span class="sxs-lookup"><span data-stu-id="71af9-421">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="71af9-422">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-422">**Option values**</span></span> | <span data-ttu-id="71af9-423">`true` - 在型別宣告中基底或介面的冒號之前放入一個空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-423">`true` - Place a space character before the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="71af9-424">`false` - 移除型別宣告中基底或介面內冒號之前的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-424">`false` - Remove space before the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="71af9-425">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-425">Code examples:</span></span>

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a><span data-ttu-id="71af9-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="71af9-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="71af9-427">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-427">Property</span></span>|<span data-ttu-id="71af9-428">值</span><span class="sxs-lookup"><span data-stu-id="71af9-428">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-429">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-429">**Option name**</span></span> | <span data-ttu-id="71af9-430">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="71af9-430">csharp_space_after_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="71af9-431">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-431">**Applicable languages**</span></span> | <span data-ttu-id="71af9-432">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-432">C#</span></span> |
| <span data-ttu-id="71af9-433">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-433">**Introduced version**</span></span> | <span data-ttu-id="71af9-434">Visual Studio 2017 15.7 版</span><span class="sxs-lookup"><span data-stu-id="71af9-434">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="71af9-435">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-435">**Option values**</span></span> | <span data-ttu-id="71af9-436">`true` - 在型別宣告中基底或介面的冒號之後放入一個空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-436">`true` - Place a space character after the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="71af9-437">`false` - 移除型別宣告中基底或介面內冒號之後的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-437">`false` - Remove space after the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="71af9-438">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-438">Code examples:</span></span>

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharp_space_around_binary_operators"></a><span data-ttu-id="71af9-439">csharp\_space\_around\_binary_operators</span><span class="sxs-lookup"><span data-stu-id="71af9-439">csharp\_space\_around\_binary_operators</span></span>

|<span data-ttu-id="71af9-440">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-440">Property</span></span>|<span data-ttu-id="71af9-441">值</span><span class="sxs-lookup"><span data-stu-id="71af9-441">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-442">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-442">**Option name**</span></span> | <span data-ttu-id="71af9-443">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="71af9-443">csharp_space_around_binary_operators</span></span> |
| <span data-ttu-id="71af9-444">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-444">**Applicable languages**</span></span> | <span data-ttu-id="71af9-445">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-445">C#</span></span> |
| <span data-ttu-id="71af9-446">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-446">**Introduced version**</span></span> | <span data-ttu-id="71af9-447">Visual Studio 2017 15.7 版</span><span class="sxs-lookup"><span data-stu-id="71af9-447">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="71af9-448">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-448">**Option values**</span></span> | <span data-ttu-id="71af9-449">`before_and_after` - 在二元運算子前後插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-449">`before_and_after` - Insert space before and after the binary operator</span></span><br /><br /><span data-ttu-id="71af9-450">`none` - 移除二元運算子前後的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-450">`none` - Remove spaces before and after the binary operator</span></span><br /><br /><span data-ttu-id="71af9-451">`ignore` - 忽略二元運算子前後的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-451">`ignore` - Ignore spaces around binary operators</span></span> |

<span data-ttu-id="71af9-452">如果您略過這項規則，或使用 `before_and_after`、`none` 或 `ignore` 以外的值，即不套用設定。</span><span class="sxs-lookup"><span data-stu-id="71af9-452">If you omit this rule, or use a value other than `before_and_after`, `none`, or `ignore`, the setting is not applied.</span></span>

<span data-ttu-id="71af9-453">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-453">Code examples:</span></span>

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a><span data-ttu-id="71af9-454">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-454">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>

|<span data-ttu-id="71af9-455">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-455">Property</span></span>|<span data-ttu-id="71af9-456">值</span><span class="sxs-lookup"><span data-stu-id="71af9-456">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-457">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-457">**Option name**</span></span> | <span data-ttu-id="71af9-458">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-458">csharp_space_between_method_declaration_parameter_list_parentheses</span></span> |
| <span data-ttu-id="71af9-459">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-459">**Applicable languages**</span></span> | <span data-ttu-id="71af9-460">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-460">C#</span></span> |
| <span data-ttu-id="71af9-461">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-461">**Introduced version**</span></span> | <span data-ttu-id="71af9-462">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-462">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-463">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-463">**Option values**</span></span> | <span data-ttu-id="71af9-464">`true` - 在方法宣告參數清單的左括弧後面和右括弧前面加上空格字元</span><span class="sxs-lookup"><span data-stu-id="71af9-464">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span><br /><br /><span data-ttu-id="71af9-465">`false` - 移除方法宣告參數清單的左括弧後面和右括弧前面的空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-465">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span> |

<span data-ttu-id="71af9-466">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-466">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a><span data-ttu-id="71af9-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="71af9-468">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-468">Property</span></span>|<span data-ttu-id="71af9-469">值</span><span class="sxs-lookup"><span data-stu-id="71af9-469">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-470">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-470">**Option name**</span></span> | <span data-ttu-id="71af9-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="71af9-472">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-472">**Applicable languages**</span></span> | <span data-ttu-id="71af9-473">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-473">C#</span></span> |
| <span data-ttu-id="71af9-474">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-474">**Introduced version**</span></span> | <span data-ttu-id="71af9-475">Visual Studio 2017 15.7 版</span><span class="sxs-lookup"><span data-stu-id="71af9-475">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="71af9-476">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-476">**Option values**</span></span> | <span data-ttu-id="71af9-477">`true` - 在方法宣告的空白參數清單括弧內插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-477">`true` - Insert space within empty parameter list parentheses for a method declaration</span></span><br /><br /><span data-ttu-id="71af9-478">`false` - 將方法宣告的空白參數清單括弧內的空格移除</span><span class="sxs-lookup"><span data-stu-id="71af9-478">`false` - Remove space within empty parameter list parentheses for a method declaration</span></span> |

<span data-ttu-id="71af9-479">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-479">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a><span data-ttu-id="71af9-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="71af9-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>

|<span data-ttu-id="71af9-481">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-481">Property</span></span>|<span data-ttu-id="71af9-482">值</span><span class="sxs-lookup"><span data-stu-id="71af9-482">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-483">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-483">**Option name**</span></span> | <span data-ttu-id="71af9-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="71af9-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span> |
| <span data-ttu-id="71af9-485">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-485">**Applicable languages**</span></span> | <span data-ttu-id="71af9-486">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-486">C#</span></span> |
| <span data-ttu-id="71af9-487">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-487">**Option values**</span></span> | <span data-ttu-id="71af9-488">`true` - 在方法名稱與方法宣告的左括弧之間放入一個空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-488">`true` - Place a space character between the method name and opening parenthesis in the method declaration</span></span><br /><br /><span data-ttu-id="71af9-489">`false` - 移除方法名稱與方法宣告左括弧之間的空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-489">`false` - Remove space characters between the method name and opening parenthesis in the method declaration</span></span> |

<span data-ttu-id="71af9-490">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-490">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a><span data-ttu-id="71af9-491">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-491">csharp_space_between_method_call_parameter_list_parentheses</span></span>

|<span data-ttu-id="71af9-492">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-492">Property</span></span>|<span data-ttu-id="71af9-493">值</span><span class="sxs-lookup"><span data-stu-id="71af9-493">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-494">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-494">**Option name**</span></span> | <span data-ttu-id="71af9-495">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-495">csharp_space_between_method_call_parameter_list_parentheses</span></span> |
| <span data-ttu-id="71af9-496">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-496">**Applicable languages**</span></span> | <span data-ttu-id="71af9-497">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-497">C#</span></span> |
| <span data-ttu-id="71af9-498">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-498">**Introduced version**</span></span> | <span data-ttu-id="71af9-499">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-499">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-500">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-500">**Option values**</span></span> | <span data-ttu-id="71af9-501">`true` - 在方法呼叫的左括弧後面和右括弧前面加上空格字元</span><span class="sxs-lookup"><span data-stu-id="71af9-501">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method call</span></span><br /><br /><span data-ttu-id="71af9-502">`false` - 移除方法呼叫的左括弧後面和右括弧前面的空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-502">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method call</span></span> |

<span data-ttu-id="71af9-503">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-503">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a><span data-ttu-id="71af9-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="71af9-505">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-505">Property</span></span>|<span data-ttu-id="71af9-506">值</span><span class="sxs-lookup"><span data-stu-id="71af9-506">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-507">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-507">**Option name**</span></span> | <span data-ttu-id="71af9-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="71af9-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="71af9-509">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-509">**Applicable languages**</span></span> | <span data-ttu-id="71af9-510">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-510">C#</span></span> |
| <span data-ttu-id="71af9-511">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-511">**Introduced version**</span></span> | <span data-ttu-id="71af9-512">Visual Studio 2017 15.7 版</span><span class="sxs-lookup"><span data-stu-id="71af9-512">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="71af9-513">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-513">**Option values**</span></span> | <span data-ttu-id="71af9-514">`true` - 在空白引數清單括弧內插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-514">`true` - Insert space within empty argument list parentheses</span></span><br /><br /><span data-ttu-id="71af9-515">`false` - 將空白引數清單括弧內的空格移除</span><span class="sxs-lookup"><span data-stu-id="71af9-515">`false` - Remove space within empty argument list parentheses</span></span> |

<span data-ttu-id="71af9-516">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-516">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a><span data-ttu-id="71af9-517">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="71af9-517">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>

|<span data-ttu-id="71af9-518">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-518">Property</span></span>|<span data-ttu-id="71af9-519">值</span><span class="sxs-lookup"><span data-stu-id="71af9-519">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-520">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-520">**Option name**</span></span> | <span data-ttu-id="71af9-521">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="71af9-521">csharp_space_between_method_call_name_and_opening_parenthesis</span></span> |
| <span data-ttu-id="71af9-522">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-522">**Applicable languages**</span></span> | <span data-ttu-id="71af9-523">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-523">C#</span></span> |
| <span data-ttu-id="71af9-524">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-524">**Introduced version**</span></span> | <span data-ttu-id="71af9-525">Visual Studio 2017 15.7 版</span><span class="sxs-lookup"><span data-stu-id="71af9-525">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="71af9-526">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-526">**Option values**</span></span> | <span data-ttu-id="71af9-527">`true` - 在方法呼叫名稱與左括弧之間插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-527">`true` - Insert space between method call name and opening parenthesis</span></span><br /><br /><span data-ttu-id="71af9-528">`false` - 將方法呼叫名稱與左括弧之間的空格移除</span><span class="sxs-lookup"><span data-stu-id="71af9-528">`false` - Remove space between method call name and opening parenthesis</span></span> |

<span data-ttu-id="71af9-529">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-529">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_after_comma"></a><span data-ttu-id="71af9-530">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="71af9-530">csharp_space_after_comma</span></span>

|<span data-ttu-id="71af9-531">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-531">Property</span></span>|<span data-ttu-id="71af9-532">值</span><span class="sxs-lookup"><span data-stu-id="71af9-532">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-533">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-533">**Option name**</span></span> | <span data-ttu-id="71af9-534">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="71af9-534">csharp_space_after_comma</span></span> |
| <span data-ttu-id="71af9-535">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-535">**Applicable languages**</span></span> | <span data-ttu-id="71af9-536">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-536">C#</span></span> |
| <span data-ttu-id="71af9-537">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-537">**Option values**</span></span> | <span data-ttu-id="71af9-538">`true` - 在逗號後面插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-538">`true` - Insert space after a comma</span></span><br /><br /><span data-ttu-id="71af9-539">`false` - 將逗號後面的空格移除</span><span class="sxs-lookup"><span data-stu-id="71af9-539">`false` - Remove space after a comma</span></span> |

<span data-ttu-id="71af9-540">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-540">Code examples:</span></span>

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a><span data-ttu-id="71af9-541">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="71af9-541">csharp_space_before_comma</span></span>

|<span data-ttu-id="71af9-542">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-542">Property</span></span>|<span data-ttu-id="71af9-543">值</span><span class="sxs-lookup"><span data-stu-id="71af9-543">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-544">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-544">**Option name**</span></span> | <span data-ttu-id="71af9-545">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="71af9-545">csharp_space_before_comma</span></span> |
| <span data-ttu-id="71af9-546">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-546">**Applicable languages**</span></span> | <span data-ttu-id="71af9-547">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-547">C#</span></span> |
| <span data-ttu-id="71af9-548">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-548">**Option values**</span></span> | <span data-ttu-id="71af9-549">`true` - 在逗號之前插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-549">`true` - Insert space before a comma</span></span><br /><br /><span data-ttu-id="71af9-550">`false` - 移除逗號之前的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-550">`false` - Remove space before a comma</span></span> |

<span data-ttu-id="71af9-551">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-551">Code examples:</span></span>

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a><span data-ttu-id="71af9-552">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="71af9-552">csharp_space_after_dot</span></span>

|<span data-ttu-id="71af9-553">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-553">Property</span></span>|<span data-ttu-id="71af9-554">值</span><span class="sxs-lookup"><span data-stu-id="71af9-554">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-555">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-555">**Option name**</span></span> | <span data-ttu-id="71af9-556">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="71af9-556">csharp_space_after_dot</span></span> |
| <span data-ttu-id="71af9-557">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-557">**Applicable languages**</span></span> | <span data-ttu-id="71af9-558">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-558">C#</span></span> |
| <span data-ttu-id="71af9-559">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-559">**Option values**</span></span> | <span data-ttu-id="71af9-560">`true` - 在點後面插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-560">`true` - Insert space after a dot</span></span><br /><br /><span data-ttu-id="71af9-561">`false` - 將點後面的空格移除</span><span class="sxs-lookup"><span data-stu-id="71af9-561">`false` - Remove space after a dot</span></span> |

<span data-ttu-id="71af9-562">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-562">Code examples:</span></span>

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a><span data-ttu-id="71af9-563">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="71af9-563">csharp_space_before_dot</span></span>

|<span data-ttu-id="71af9-564">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-564">Property</span></span>|<span data-ttu-id="71af9-565">值</span><span class="sxs-lookup"><span data-stu-id="71af9-565">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-566">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-566">**Option name**</span></span> | <span data-ttu-id="71af9-567">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="71af9-567">csharp_space_before_dot</span></span> |
| <span data-ttu-id="71af9-568">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-568">**Applicable languages**</span></span> | <span data-ttu-id="71af9-569">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-569">C#</span></span> |
| <span data-ttu-id="71af9-570">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-570">**Option values**</span></span> | <span data-ttu-id="71af9-571">`true` - 在點之前插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-571">`true` - Insert space before a dot</span></span> <br /><br /><span data-ttu-id="71af9-572">`false` - 移除點之前的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-572">`false` - Remove space before a dot</span></span> |

<span data-ttu-id="71af9-573">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-573">Code examples:</span></span>

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a><span data-ttu-id="71af9-574">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="71af9-574">csharp_space_after_semicolon_in_for_statement</span></span>

|<span data-ttu-id="71af9-575">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-575">Property</span></span>|<span data-ttu-id="71af9-576">值</span><span class="sxs-lookup"><span data-stu-id="71af9-576">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-577">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-577">**Option name**</span></span> | <span data-ttu-id="71af9-578">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="71af9-578">csharp_space_after_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="71af9-579">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-579">**Applicable languages**</span></span> | <span data-ttu-id="71af9-580">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-580">C#</span></span> |
| <span data-ttu-id="71af9-581">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-581">**Option values**</span></span> | <span data-ttu-id="71af9-582">`true` - 在 `for` 陳述式的每個分號之後插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-582">`true` - Insert space after each semicolon in a `for` statement</span></span><br /><br /><span data-ttu-id="71af9-583">`false` - 移除 `for` 陳述式每個分號之後的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-583">`false` - Remove space after each semicolon in a `for` statement</span></span> |

<span data-ttu-id="71af9-584">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-584">Code examples:</span></span>

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a><span data-ttu-id="71af9-585">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="71af9-585">csharp_space_before_semicolon_in_for_statement</span></span>

|<span data-ttu-id="71af9-586">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-586">Property</span></span>|<span data-ttu-id="71af9-587">值</span><span class="sxs-lookup"><span data-stu-id="71af9-587">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-588">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-588">**Option name**</span></span> | <span data-ttu-id="71af9-589">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="71af9-589">csharp_space_before_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="71af9-590">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-590">**Applicable languages**</span></span> | <span data-ttu-id="71af9-591">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-591">C#</span></span> |
| <span data-ttu-id="71af9-592">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-592">**Option values**</span></span> | <span data-ttu-id="71af9-593">`true` - 在 `for` 陳述式的每個分號之前插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-593">`true` - Insert space before each semicolon in a `for` statement</span></span> <br /><br /><span data-ttu-id="71af9-594">`false` - 移除 `for` 陳述式每個分號之前的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-594">`false` - Remove space before each semicolon in a `for` statement</span></span> |

<span data-ttu-id="71af9-595">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-595">Code examples:</span></span>

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a><span data-ttu-id="71af9-596">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="71af9-596">csharp_space_around_declaration_statements</span></span>

|<span data-ttu-id="71af9-597">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-597">Property</span></span>|<span data-ttu-id="71af9-598">值</span><span class="sxs-lookup"><span data-stu-id="71af9-598">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-599">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-599">**Option name**</span></span> | <span data-ttu-id="71af9-600">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="71af9-600">csharp_space_around_declaration_statements</span></span> |
| <span data-ttu-id="71af9-601">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-601">**Applicable languages**</span></span> | <span data-ttu-id="71af9-602">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-602">C#</span></span> |
| <span data-ttu-id="71af9-603">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-603">**Option values**</span></span> | <span data-ttu-id="71af9-604">`ignore` - 不要移除宣告陳述式中的額外空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-604">`ignore` - Don't remove extra space characters in declaration statements</span></span><br /><br /><span data-ttu-id="71af9-605">`false` - 移除宣告陳述式中的額外空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-605">`false` - Remove extra space characters in declaration statements</span></span> |

<span data-ttu-id="71af9-606">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-606">Code examples:</span></span>

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a><span data-ttu-id="71af9-607">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="71af9-607">csharp_space_before_open_square_brackets</span></span>

|<span data-ttu-id="71af9-608">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-608">Property</span></span>|<span data-ttu-id="71af9-609">值</span><span class="sxs-lookup"><span data-stu-id="71af9-609">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-610">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-610">**Option name**</span></span> | <span data-ttu-id="71af9-611">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="71af9-611">csharp_space_before_open_square_brackets</span></span> |
| <span data-ttu-id="71af9-612">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-612">**Applicable languages**</span></span> | <span data-ttu-id="71af9-613">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-613">C#</span></span> |
| <span data-ttu-id="71af9-614">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-614">**Option values**</span></span> | <span data-ttu-id="71af9-615">`true` - 在左方括弧 `[` 之前插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-615">`true` - Insert space before opening square brackets `[`</span></span> <br /><br /><span data-ttu-id="71af9-616">`false` - 移除左方括弧 `[` 之前的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-616">`false` - Remove space before opening square brackets `[`</span></span> |

<span data-ttu-id="71af9-617">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-617">Code examples:</span></span>

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a><span data-ttu-id="71af9-618">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="71af9-618">csharp_space_between_empty_square_brackets</span></span>

|<span data-ttu-id="71af9-619">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-619">Property</span></span>|<span data-ttu-id="71af9-620">值</span><span class="sxs-lookup"><span data-stu-id="71af9-620">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-621">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-621">**Option name**</span></span> | <span data-ttu-id="71af9-622">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="71af9-622">csharp_space_between_empty_square_brackets</span></span> |
| <span data-ttu-id="71af9-623">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-623">**Applicable languages**</span></span> | <span data-ttu-id="71af9-624">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-624">C#</span></span> |
| <span data-ttu-id="71af9-625">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-625">**Option values**</span></span> | <span data-ttu-id="71af9-626">`true` - 在空白方括弧 `[ ]` 之間插入空格</span><span class="sxs-lookup"><span data-stu-id="71af9-626">`true` - Insert space between empty square brackets `[ ]`</span></span> <br /><br /><span data-ttu-id="71af9-627">`false` - 移除空白方括弧 `[]` 之間的空格</span><span class="sxs-lookup"><span data-stu-id="71af9-627">`false` - Remove space between empty square brackets `[]`</span></span> |

<span data-ttu-id="71af9-628">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-628">Code examples:</span></span>

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a><span data-ttu-id="71af9-629">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="71af9-629">csharp_space_between_square_brackets</span></span>

|<span data-ttu-id="71af9-630">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-630">Property</span></span>|<span data-ttu-id="71af9-631">值</span><span class="sxs-lookup"><span data-stu-id="71af9-631">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-632">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-632">**Option name**</span></span> | <span data-ttu-id="71af9-633">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="71af9-633">csharp_space_between_square_brackets</span></span> |
| <span data-ttu-id="71af9-634">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-634">**Applicable languages**</span></span> | <span data-ttu-id="71af9-635">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-635">C#</span></span> |
| <span data-ttu-id="71af9-636">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-636">**Option values**</span></span> | <span data-ttu-id="71af9-637">`true` - 在非空白方括弧 `[ 0 ]` 中插入空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-637">`true` - Insert space characters in non-empty square brackets `[ 0 ]`</span></span> <br /><br /><span data-ttu-id="71af9-638">`false` - 移除非空白方括弧 `[0]` 之間的空白字元</span><span class="sxs-lookup"><span data-stu-id="71af9-638">`false` - Remove space characters in non-empty square brackets `[0]`</span></span> |

<span data-ttu-id="71af9-639">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-639">Code examples:</span></span>

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a><span data-ttu-id="71af9-640">包裝選項</span><span class="sxs-lookup"><span data-stu-id="71af9-640">Wrap options</span></span>

<span data-ttu-id="71af9-641">這些格式化規則是有關陳述式和程式碼區塊的單一行與個別行的使用。</span><span class="sxs-lookup"><span data-stu-id="71af9-641">These formatting rules concern the use of single lines versus separate lines for statements and code blocks.</span></span>

<span data-ttu-id="71af9-642">Editorconfig 檔案範例︰</span><span class="sxs-lookup"><span data-stu-id="71af9-642">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a><span data-ttu-id="71af9-643">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="71af9-643">csharp_preserve_single_line_statements</span></span>

|<span data-ttu-id="71af9-644">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-644">Property</span></span>|<span data-ttu-id="71af9-645">值</span><span class="sxs-lookup"><span data-stu-id="71af9-645">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-646">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-646">**Option name**</span></span> | <span data-ttu-id="71af9-647">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="71af9-647">csharp_preserve_single_line_statements</span></span> |
| <span data-ttu-id="71af9-648">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-648">**Applicable languages**</span></span> | <span data-ttu-id="71af9-649">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-649">C#</span></span> |
| <span data-ttu-id="71af9-650">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-650">**Introduced version**</span></span> | <span data-ttu-id="71af9-651">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-651">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-652">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-652">**Option values**</span></span> | <span data-ttu-id="71af9-653">`true` - 將陳述式和成員宣告保留在同一行上</span><span class="sxs-lookup"><span data-stu-id="71af9-653">`true` - Leave statements and member declarations on the same line</span></span><br /><br /><span data-ttu-id="71af9-654">`false` - 將陳述式和成員宣告保留在不同的行上</span><span class="sxs-lookup"><span data-stu-id="71af9-654">`false` - Leave statements and member declarations on different lines</span></span> |

<span data-ttu-id="71af9-655">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-655">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a><span data-ttu-id="71af9-656">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="71af9-656">csharp_preserve_single_line_blocks</span></span>

|<span data-ttu-id="71af9-657">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-657">Property</span></span>|<span data-ttu-id="71af9-658">值</span><span class="sxs-lookup"><span data-stu-id="71af9-658">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-659">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-659">**Option name**</span></span> | <span data-ttu-id="71af9-660">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="71af9-660">csharp_preserve_single_line_blocks</span></span> |
| <span data-ttu-id="71af9-661">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-661">**Applicable languages**</span></span> | <span data-ttu-id="71af9-662">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-662">C#</span></span> |
| <span data-ttu-id="71af9-663">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-663">**Introduced version**</span></span> | <span data-ttu-id="71af9-664">Visual Studio 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="71af9-664">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="71af9-665">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-665">**Option values**</span></span> | <span data-ttu-id="71af9-666">`true` - 將程式碼區塊保留在單行上</span><span class="sxs-lookup"><span data-stu-id="71af9-666">`true` - Leave code block on single line</span></span><br /><br /><span data-ttu-id="71af9-667">`false` - 將程式碼區塊保留在不同的行上</span><span class="sxs-lookup"><span data-stu-id="71af9-667">`false` - Leave code block on separate lines</span></span> |

<span data-ttu-id="71af9-668">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-668">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a><span data-ttu-id="71af9-669">Using 指示詞選項</span><span class="sxs-lookup"><span data-stu-id="71af9-669">Using directive options</span></span>

<span data-ttu-id="71af9-670">此格式設定規則會考慮使用在命名空間內部與外部的 using 指示詞。</span><span class="sxs-lookup"><span data-stu-id="71af9-670">This formatting rule concerns the use of using directives being placed inside versus outside a namespace.</span></span>

<span data-ttu-id="71af9-671">Editorconfig 檔案範例︰</span><span class="sxs-lookup"><span data-stu-id="71af9-671">Example *.editorconfig* file:</span></span>

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a><span data-ttu-id="71af9-672">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="71af9-672">csharp_using_directive_placement</span></span>

|<span data-ttu-id="71af9-673">屬性</span><span class="sxs-lookup"><span data-stu-id="71af9-673">Property</span></span>|<span data-ttu-id="71af9-674">值</span><span class="sxs-lookup"><span data-stu-id="71af9-674">Value</span></span>|
|-|-|
| <span data-ttu-id="71af9-675">**選項名稱**</span><span class="sxs-lookup"><span data-stu-id="71af9-675">**Option name**</span></span> | <span data-ttu-id="71af9-676">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="71af9-676">csharp_using_directive_placement</span></span> |
| <span data-ttu-id="71af9-677">**適用的語言**</span><span class="sxs-lookup"><span data-stu-id="71af9-677">**Applicable languages**</span></span> | <span data-ttu-id="71af9-678">C#</span><span class="sxs-lookup"><span data-stu-id="71af9-678">C#</span></span> |
| <span data-ttu-id="71af9-679">**引進的版本**</span><span class="sxs-lookup"><span data-stu-id="71af9-679">**Introduced version**</span></span> | <span data-ttu-id="71af9-680">Visual Studio 2019 16.1 版</span><span class="sxs-lookup"><span data-stu-id="71af9-680">Visual Studio 2019 version 16.1</span></span> |
| <span data-ttu-id="71af9-681">**選項值**</span><span class="sxs-lookup"><span data-stu-id="71af9-681">**Option values**</span></span> | <span data-ttu-id="71af9-682">`outside_namespace` -離開命名空間以外的 using 指示詞</span><span class="sxs-lookup"><span data-stu-id="71af9-682">`outside_namespace` - Leave using directives outside namespace</span></span><br /><br /><span data-ttu-id="71af9-683">`inside_namespace` -保留命名空間內的 using 指示詞</span><span class="sxs-lookup"><span data-stu-id="71af9-683">`inside_namespace` - Leave using directives inside namespace</span></span> |

<span data-ttu-id="71af9-684">程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="71af9-684">Code examples:</span></span>

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a><span data-ttu-id="71af9-685">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71af9-685">See also</span></span>

- [<span data-ttu-id="71af9-686">語言規則</span><span class="sxs-lookup"><span data-stu-id="71af9-686">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="71af9-687">命名規則</span><span class="sxs-lookup"><span data-stu-id="71af9-687">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="71af9-688">.NET 程式碼樣式規則參考</span><span class="sxs-lookup"><span data-stu-id="71af9-688">.NET code style rules reference</span></span>](index.md)
