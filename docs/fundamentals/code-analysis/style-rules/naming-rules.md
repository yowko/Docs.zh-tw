---
title: 程式碼樣式命名規則
description: 瞭解適用于命名程式碼專案的 .NET 程式碼樣式規則。
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE1006
- naming rules
helpviewer_keywords:
- IDE1006
- naming code style rules [EditorConfig]
- naming rules
- EditorConfig naming conventions
ms.openlocfilehash: 1fce275204b729b4d23729ca432e06a5a249620d
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065131"
---
# <a name="naming-rules"></a><span data-ttu-id="84725-103">命名規則</span><span class="sxs-lookup"><span data-stu-id="84725-103">Naming rules</span></span>

<span data-ttu-id="84725-104">在您的檔案中 `.editorconfig` ，您可以定義 .net 程式設計語言程式碼專案 &mdash; （例如類別、屬性和方法）如何命名的命名規則 &mdash; 。</span><span class="sxs-lookup"><span data-stu-id="84725-104">In your `.editorconfig` file, you can define **naming rules** for how .NET programming language code elements&mdash;such as classes, properties, and methods&mdash;should be named.</span></span> <span data-ttu-id="84725-105">例如，您可以指定公用成員必須為大寫，或私用欄位必須以開頭 `_` 。</span><span class="sxs-lookup"><span data-stu-id="84725-105">For example, you can specify that public members must be capitalized, or that private fields must begin with `_`.</span></span>

<span data-ttu-id="84725-106">命名規則有三個元件：</span><span class="sxs-lookup"><span data-stu-id="84725-106">A naming rule has three components:</span></span>

* <span data-ttu-id="84725-107">**符號群組** &mdash; 規則套用的符號群組。</span><span class="sxs-lookup"><span data-stu-id="84725-107">The **symbol group**&mdash;the group of symbols the rule applies to.</span></span>
* <span data-ttu-id="84725-108">要與規則相關聯的 **命名樣式** 。</span><span class="sxs-lookup"><span data-stu-id="84725-108">The **naming style** to associate with the rule.</span></span>
* <span data-ttu-id="84725-109">強制慣例的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="84725-109">The severity for enforcing the convention.</span></span>

## <a name="general-syntax"></a><span data-ttu-id="84725-110">一般語法</span><span class="sxs-lookup"><span data-stu-id="84725-110">General syntax</span></span>

<span data-ttu-id="84725-111">若要定義命名規則、符號群組或命名樣式，請使用下列語法來設定一或多個屬性：</span><span class="sxs-lookup"><span data-stu-id="84725-111">To define a naming rule, symbol group, or naming style, set one or more properties using the following syntax:</span></span>

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

<span data-ttu-id="84725-112">每個屬性只能設定一次，但某些設定允許多個逗號分隔值。</span><span class="sxs-lookup"><span data-stu-id="84725-112">Each property should only be set once, but some settings allow multiple, comma-separated values.</span></span>

<span data-ttu-id="84725-113">屬性的順序不重要。</span><span class="sxs-lookup"><span data-stu-id="84725-113">The order of the properties is not important.</span></span>

### \<kind>

<span data-ttu-id="84725-114">**\<kind>** 指定要定義的專案類型為 &mdash; 命名規則、符號群組或命名樣式， &mdash; 而且必須是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="84725-114">**\<kind>** specifies which kind of element is being defined&mdash;naming rule, symbol group, or naming style&mdash;and must be one of the following:</span></span>

| <span data-ttu-id="84725-115">若要設定的屬性</span><span class="sxs-lookup"><span data-stu-id="84725-115">To set a property for</span></span> | <span data-ttu-id="84725-116">使用 \<kind> 值</span><span class="sxs-lookup"><span data-stu-id="84725-116">Use the \<kind> value</span></span> | <span data-ttu-id="84725-117">範例</span><span class="sxs-lookup"><span data-stu-id="84725-117">Example</span></span> |
| --- | --- | -- |
| <span data-ttu-id="84725-118">命名規則</span><span class="sxs-lookup"><span data-stu-id="84725-118">Naming rule</span></span> | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| <span data-ttu-id="84725-119">符號群組</span><span class="sxs-lookup"><span data-stu-id="84725-119">Symbol group</span></span> | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| <span data-ttu-id="84725-120">命名樣式</span><span class="sxs-lookup"><span data-stu-id="84725-120">Naming style</span></span> | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

<span data-ttu-id="84725-121">每種類型的定義 &mdash; [命名規則](#naming-rule-properties)、[符號群組](#symbol-group-properties)或[命名樣式](#naming-style-properties) &mdash; 都有自己支援的屬性，如下列各節所述。</span><span class="sxs-lookup"><span data-stu-id="84725-121">Each type of definition&mdash;[naming rule](#naming-rule-properties), [symbol group](#symbol-group-properties), or [naming style](#naming-style-properties)&mdash;has its own supported properties, as described in the following sections.</span></span>

### \<title>

<span data-ttu-id="84725-122">**\<title>** 是您選擇的描述性名稱，可將多個屬性設定與單一定義產生關聯。</span><span class="sxs-lookup"><span data-stu-id="84725-122">**\<title>** is a descriptive name you choose that associates multiple property settings into a single definition.</span></span> <span data-ttu-id="84725-123">例如，下列屬性會產生兩個符號群組定義， `interface` 而且 `types` 每個都有兩個屬性設定。</span><span class="sxs-lookup"><span data-stu-id="84725-123">For example, the following properties produce two symbol group definitions, `interface` and `types`, each of which has two properties set on it.</span></span>

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a><span data-ttu-id="84725-124">命名規則屬性</span><span class="sxs-lookup"><span data-stu-id="84725-124">Naming rule properties</span></span>

<span data-ttu-id="84725-125">所有命名規則屬性都必須要有規則才會生效。</span><span class="sxs-lookup"><span data-stu-id="84725-125">All naming rule properties are required for a rule to take effect.</span></span>

| <span data-ttu-id="84725-126">屬性</span><span class="sxs-lookup"><span data-stu-id="84725-126">Property</span></span> | <span data-ttu-id="84725-127">描述</span><span class="sxs-lookup"><span data-stu-id="84725-127">Description</span></span> |
| -- | -- |
| `symbols` | <span data-ttu-id="84725-128">符號群組的標題;命名規則將套用至此群組中的符號</span><span class="sxs-lookup"><span data-stu-id="84725-128">The title of a symbol group; the naming rule will be applied to the symbols in this group</span></span> |
| `style` | <span data-ttu-id="84725-129">應與此規則相關聯之命名樣式的標題</span><span class="sxs-lookup"><span data-stu-id="84725-129">The title of the naming style which should be associated with this rule</span></span> |
| `severity` |  <span data-ttu-id="84725-130">設定用來強制執行命名規則的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="84725-130">Sets the severity with which to enforce the naming rule.</span></span> <span data-ttu-id="84725-131">將相關聯的值設定為其中一個可用的 [嚴重性層級](../configuration-options.md#severity-level)。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="84725-131">Set the associated value to one of the available [severity levels](../configuration-options.md#severity-level).<sup>1</sup></span></span> |

<span data-ttu-id="84725-132">**注意：**</span><span class="sxs-lookup"><span data-stu-id="84725-132">**Notes:**</span></span>

1. <span data-ttu-id="84725-133">只有在開發 Ide （例如 Visual Studio）中才遵守命名規則內的嚴重性規格。</span><span class="sxs-lookup"><span data-stu-id="84725-133">Severity specification within a naming rule is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="84725-134">C # 或 VB 編譯器無法理解這項設定，因此不會在組建期間遵守。</span><span class="sxs-lookup"><span data-stu-id="84725-134">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="84725-135">若要在組建上強制執行命名樣式規則，您應該改為使用程式 [代碼規則嚴重性](#rule-id-ide1006-naming-rule-violation)設定來設定嚴重性。</span><span class="sxs-lookup"><span data-stu-id="84725-135">To enforce naming style rules on build, you should instead set the severity by using [code rule severity configuration](#rule-id-ide1006-naming-rule-violation).</span></span> <span data-ttu-id="84725-136">如需詳細資訊，請參閱此 [GitHub 問題](https://github.com/dotnet/roslyn/issues/44201)。</span><span class="sxs-lookup"><span data-stu-id="84725-136">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

## <a name="symbol-group-properties"></a><span data-ttu-id="84725-137">符號群組屬性</span><span class="sxs-lookup"><span data-stu-id="84725-137">Symbol group properties</span></span>

<span data-ttu-id="84725-138">您可以設定符號群組的下列屬性，以限制要包含在群組中的符號。</span><span class="sxs-lookup"><span data-stu-id="84725-138">You can set the following properties for symbol groups, to limit which symbols are included in the group.</span></span> <span data-ttu-id="84725-139">若要為單一屬性指定多個值，請以逗號分隔這些值。</span><span class="sxs-lookup"><span data-stu-id="84725-139">To specify multiple values for a single property, separate the values with a comma.</span></span>

| <span data-ttu-id="84725-140">屬性</span><span class="sxs-lookup"><span data-stu-id="84725-140">Property</span></span> | <span data-ttu-id="84725-141">描述</span><span class="sxs-lookup"><span data-stu-id="84725-141">Description</span></span> | <span data-ttu-id="84725-142">允許的值</span><span class="sxs-lookup"><span data-stu-id="84725-142">Allowed values</span></span> | <span data-ttu-id="84725-143">必要</span><span class="sxs-lookup"><span data-stu-id="84725-143">Required</span></span> |
| -- | -- | -- | -- |
| `applicable_kinds` | <span data-ttu-id="84725-144">群組<sup>1</sup>中的符號種類</span><span class="sxs-lookup"><span data-stu-id="84725-144">Kinds of symbols in the group <sup>1</sup></span></span> | <span data-ttu-id="84725-145">`*`(請使用此值來指定所有符號)</span><span class="sxs-lookup"><span data-stu-id="84725-145">`*` (use this value to specify all symbols)</span></span><br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | <span data-ttu-id="84725-146">是</span><span class="sxs-lookup"><span data-stu-id="84725-146">Yes</span></span> |
| `applicable_accessibilities` | <span data-ttu-id="84725-147">群組中符號的存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="84725-147">Accessibility levels of the symbols in the group</span></span> | <span data-ttu-id="84725-148">`*` (請使用此值來指定所有存取層級)</span><span class="sxs-lookup"><span data-stu-id="84725-148">`*` (use this value to specify all accessibility levels)</span></span><br/>`public`<br/><span data-ttu-id="84725-149">`internal` 或 `friend`</span><span class="sxs-lookup"><span data-stu-id="84725-149">`internal` or `friend`</span></span><br/>`private`<br/>`protected`<br/><span data-ttu-id="84725-150">`protected_internal` 或 `protected_friend`</span><span class="sxs-lookup"><span data-stu-id="84725-150">`protected_internal` or `protected_friend`</span></span><br/>`private_protected`<br/><span data-ttu-id="84725-151">`local` 在方法內定義的符號 () </span><span class="sxs-lookup"><span data-stu-id="84725-151">`local` (for symbols defined within a method)</span></span> | <span data-ttu-id="84725-152">是</span><span class="sxs-lookup"><span data-stu-id="84725-152">Yes</span></span> |
| `required_modifiers` | <span data-ttu-id="84725-153">僅符合具有 _所有_ 指定修飾詞 <sup>2</sup>的符號</span><span class="sxs-lookup"><span data-stu-id="84725-153">Only match symbols with _all_ the specified modifiers <sup>2</sup></span></span> | <span data-ttu-id="84725-154">`abstract` 或 `must_inherit`</span><span class="sxs-lookup"><span data-stu-id="84725-154">`abstract` or `must_inherit`</span></span><br/>`async`<br/>`const`<br/>`readonly`<br/><span data-ttu-id="84725-155">`static` 或 `shared` <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="84725-155">`static` or `shared` <sup>3</sup></span></span> | <span data-ttu-id="84725-156">否</span><span class="sxs-lookup"><span data-stu-id="84725-156">No</span></span> |

<span data-ttu-id="84725-157">**注意：**</span><span class="sxs-lookup"><span data-stu-id="84725-157">**Notes:**</span></span>

1. <span data-ttu-id="84725-158">目前不支援元組成員 `applicable_kinds` 。</span><span class="sxs-lookup"><span data-stu-id="84725-158">Tuple members aren't currently supported in `applicable_kinds`.</span></span>
2. <span data-ttu-id="84725-159">符號群組符合屬性中的 _所有_ 修飾詞 `required_modifiers` 。</span><span class="sxs-lookup"><span data-stu-id="84725-159">The symbol group matches _all_ the modifiers in the `required_modifiers` property.</span></span>  <span data-ttu-id="84725-160">如果您省略這個屬性，則不需要任何特定的修飾詞來進行比對。</span><span class="sxs-lookup"><span data-stu-id="84725-160">If you omit this property, no specific modifiers are required for a match.</span></span> <span data-ttu-id="84725-161">這表示不論是否套用此規則，符號的修飾詞都不會造成影響。</span><span class="sxs-lookup"><span data-stu-id="84725-161">This means a symbol's modifiers have no effect on whether or not this rule is applied.</span></span>
3. <span data-ttu-id="84725-162">如果您的群組具有 `static` 或 `shared` 在 `required_modifiers` 屬性中，則群組也會包含 `const` 符號，因為它們是隱含的 `static` / `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="84725-162">If your group has `static` or `shared` in the `required_modifiers` property, the group will also include `const` symbols because they are implicitly `static`/`Shared`.</span></span> <span data-ttu-id="84725-163">但是，如果您不想要將 `static` 命名規則套用至 `const` 符號，可以使用的符號群組來建立新的命名規則 `const` 。</span><span class="sxs-lookup"><span data-stu-id="84725-163">However, if you don't want the `static` naming rule to apply to `const` symbols, you can create a new naming rule with a symbol group of `const`.</span></span>

## <a name="naming-style-properties"></a><span data-ttu-id="84725-164">命名樣式屬性</span><span class="sxs-lookup"><span data-stu-id="84725-164">Naming style properties</span></span>

<span data-ttu-id="84725-165">命名樣式會定義您想要使用規則強制執行的慣例。</span><span class="sxs-lookup"><span data-stu-id="84725-165">A naming style defines the conventions you want to enforce with the rule.</span></span> <span data-ttu-id="84725-166">例如：</span><span class="sxs-lookup"><span data-stu-id="84725-166">For example:</span></span>

* <span data-ttu-id="84725-167">大寫 `PascalCase`</span><span class="sxs-lookup"><span data-stu-id="84725-167">Capitalize with `PascalCase`</span></span>
* <span data-ttu-id="84725-168">開頭為 `m_`</span><span class="sxs-lookup"><span data-stu-id="84725-168">Starts with `m_`</span></span>
* <span data-ttu-id="84725-169">結尾為 `_g`</span><span class="sxs-lookup"><span data-stu-id="84725-169">Ends with `_g`</span></span>
* <span data-ttu-id="84725-170">分隔單字和 `__`</span><span class="sxs-lookup"><span data-stu-id="84725-170">Separate words with `__`</span></span>

<span data-ttu-id="84725-171">您可以針對命名樣式來設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="84725-171">You can set the following properties for a naming style:</span></span>

| <span data-ttu-id="84725-172">屬性</span><span class="sxs-lookup"><span data-stu-id="84725-172">Property</span></span> | <span data-ttu-id="84725-173">描述</span><span class="sxs-lookup"><span data-stu-id="84725-173">Description</span></span> | <span data-ttu-id="84725-174">允許的值</span><span class="sxs-lookup"><span data-stu-id="84725-174">Allowed values</span></span> | <span data-ttu-id="84725-175">必要</span><span class="sxs-lookup"><span data-stu-id="84725-175">Required</span></span> |
| -- | -- | -- | -- |
| `capitalization` | <span data-ttu-id="84725-176">符號內文字的大小寫樣式</span><span class="sxs-lookup"><span data-stu-id="84725-176">Capitalization style for words within the symbol</span></span> | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | <span data-ttu-id="84725-177">是<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="84725-177">Yes<sup>1</sup></span></span> |
| `required_prefix` | <span data-ttu-id="84725-178">必須以這些字元開頭</span><span class="sxs-lookup"><span data-stu-id="84725-178">Must begin with these characters</span></span> | | <span data-ttu-id="84725-179">否</span><span class="sxs-lookup"><span data-stu-id="84725-179">No</span></span> |
| `required_suffix` | <span data-ttu-id="84725-180">必須以這些字元結尾</span><span class="sxs-lookup"><span data-stu-id="84725-180">Must end with these characters</span></span> | | <span data-ttu-id="84725-181">否</span><span class="sxs-lookup"><span data-stu-id="84725-181">No</span></span> |
| `word_separator` | <span data-ttu-id="84725-182">符號內的文字必須以這個字元分隔</span><span class="sxs-lookup"><span data-stu-id="84725-182">Words within the symbol need to be separated with this character</span></span> | | <span data-ttu-id="84725-183">否</span><span class="sxs-lookup"><span data-stu-id="84725-183">No</span></span> |

<span data-ttu-id="84725-184">**注意：**</span><span class="sxs-lookup"><span data-stu-id="84725-184">**Notes:**</span></span>

1. <span data-ttu-id="84725-185">您必須將大寫樣式指定為您命名樣式的一部分，否則您的命名樣式可能會遭到忽略。</span><span class="sxs-lookup"><span data-stu-id="84725-185">You must specify a capitalization style as part of your naming style, otherwise your naming style might be ignored.</span></span>

## <a name="rule-order"></a><span data-ttu-id="84725-186">規則順序</span><span class="sxs-lookup"><span data-stu-id="84725-186">Rule order</span></span>

<span data-ttu-id="84725-187">在 EditorConfig 檔案中定義命名規則的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="84725-187">The order in which naming rules are defined in an EditorConfig file doesn't matter.</span></span> <span data-ttu-id="84725-188">系統會根據規則本身的定義自動排序命名規則。</span><span class="sxs-lookup"><span data-stu-id="84725-188">The naming rules are automatically ordered according to the definition of the rules themselves.</span></span> <span data-ttu-id="84725-189">[EditorConfig Language Service 延伸](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)模組可以分析 EditorConfig 檔和報表案例，其中的規則順序與編譯器將在執行時間使用的情況不同。</span><span class="sxs-lookup"><span data-stu-id="84725-189">The [EditorConfig Language Service extension](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) can analyze an EditorConfig file and report cases where the rule ordering in the file is different to what the compiler will use at run time.</span></span>

> [!NOTE]
>
> <span data-ttu-id="84725-190">如果您使用的 Visual Studio 版本早于 Visual Studio 2019 16.2 版，則在 EditorConfig 檔中，應將命名規則從最特定到最不明確的順序排序。</span><span class="sxs-lookup"><span data-stu-id="84725-190">If you're using a version of Visual Studio earlier than Visual Studio 2019 version 16.2, naming rules should be ordered from most-specific to least-specific in the EditorConfig file.</span></span> <span data-ttu-id="84725-191">第一個遇到的可套用規則，會是唯一套用的規則。</span><span class="sxs-lookup"><span data-stu-id="84725-191">The first rule encountered that can be applied is the only rule that is applied.</span></span> <span data-ttu-id="84725-192">但是，如果有多個具有相同名稱的規則 *屬性*，則最近找到具有該名稱的屬性優先。</span><span class="sxs-lookup"><span data-stu-id="84725-192">However, if there are multiple rule *properties* with the same name, the most recently found property with that name takes precedence.</span></span> <span data-ttu-id="84725-193">如需詳細資訊，請參閱[檔案階層和優先順序](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence)。</span><span class="sxs-lookup"><span data-stu-id="84725-193">For more information, see [File hierarchy and precedence](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span></span>

## <a name="default-naming-styles"></a><span data-ttu-id="84725-194">預設命名樣式</span><span class="sxs-lookup"><span data-stu-id="84725-194">Default naming styles</span></span>

<span data-ttu-id="84725-195">如果您未指定任何自訂命名規則，則會使用下列預設樣式：</span><span class="sxs-lookup"><span data-stu-id="84725-195">If you don't specify any custom naming rules, the following default styles are used:</span></span>

- <span data-ttu-id="84725-196">針對具有 `public`、`private`、`internal`、`protected` 或 `protected_internal` 存取範圍的類別、結構、列舉、屬性及事件，預設的命名樣式為 Pascal 命名法。</span><span class="sxs-lookup"><span data-stu-id="84725-196">For classes, structs, enumerations, properties, and events with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case.</span></span>

- <span data-ttu-id="84725-197">針對具有 `public`、`private`、`internal`、`protected` 或 `protected_internal` 存取範圍的介面，預設的命名樣式為 Pascal 命名法，且必須具有前置詞 **I**。</span><span class="sxs-lookup"><span data-stu-id="84725-197">For interfaces with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case with a required prefix of **I**.</span></span>

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a><span data-ttu-id="84725-198">程式碼規則識別碼： `IDE1006 (Naming rule violation)`</span><span class="sxs-lookup"><span data-stu-id="84725-198">Code Rule ID: `IDE1006 (Naming rule violation)`</span></span>

<span data-ttu-id="84725-199">所有命名選項都有規則識別碼 `IDE1006` 和標題 `Naming rule violation` 。</span><span class="sxs-lookup"><span data-stu-id="84725-199">All naming options have rule ID `IDE1006` and title `Naming rule violation`.</span></span> <span data-ttu-id="84725-200">您可以使用下列語法，在 EditorConfig 檔案中全域設定命名違規的嚴重性：</span><span class="sxs-lookup"><span data-stu-id="84725-200">You can configure the severity of naming violations globally in an EditorConfig file with the following syntax:</span></span>

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

<span data-ttu-id="84725-201">嚴重性值必須是 `warning` 或 `error` [在組建時強制執行](../overview.md#code-style-analysis)。</span><span class="sxs-lookup"><span data-stu-id="84725-201">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="84725-202">如需所有可能的嚴重性值，請參閱 [嚴重性層級](../configuration-options.md#severity-level)。</span><span class="sxs-lookup"><span data-stu-id="84725-202">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="example"></a><span data-ttu-id="84725-203">範例</span><span class="sxs-lookup"><span data-stu-id="84725-203">Example</span></span>

<span data-ttu-id="84725-204">下列 .editorconfig 檔案所包含的命名慣例指定公用屬性、方法、欄位、事件及委派必須為大寫。</span><span class="sxs-lookup"><span data-stu-id="84725-204">The following *.editorconfig* file contains a naming convention that specifies that public properties, methods, fields, events, and delegates must be capitalized.</span></span> <span data-ttu-id="84725-205">請注意，此命名慣例指定了多種要套用規則的符號類型，並使用逗號分隔值。</span><span class="sxs-lookup"><span data-stu-id="84725-205">Notice that this naming convention specifies multiple kinds of symbol to apply the rule to, using a comma to separate the values.</span></span>

```ini
[*.{cs,vb}]

# Defining the 'public_symbols' symbol group
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

# Defining the `first_word_upper_case_style` naming style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

# Defining the `public_members_must_be_capitalized` naming rule, by setting the symbol group to the 'public symbols' symbol group,
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
# setting the naming style to the `first_word_upper_case_style` naming style,
dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
# and setting the severity.
dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

## <a name="see-also"></a><span data-ttu-id="84725-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84725-206">See also</span></span>

- [<span data-ttu-id="84725-207">語言規則</span><span class="sxs-lookup"><span data-stu-id="84725-207">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="84725-208">格式化規則</span><span class="sxs-lookup"><span data-stu-id="84725-208">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="84725-209">Roslyn 命名規則</span><span class="sxs-lookup"><span data-stu-id="84725-209">Roslyn naming rules</span></span>](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [<span data-ttu-id="84725-210">.NET 程式碼樣式規則參考</span><span class="sxs-lookup"><span data-stu-id="84725-210">.NET code style rules reference</span></span>](index.md)
