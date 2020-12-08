---
title: 設定程式碼分析規則
description: 瞭解如何在分析器設定檔中設定程式碼分析規則。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 4f7b392a2b066023fec75c5295bd94651654d645
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851786"
---
# <a name="configuration-options-for-code-analysis"></a><span data-ttu-id="16e94-103">程式碼分析的設定選項</span><span class="sxs-lookup"><span data-stu-id="16e94-103">Configuration options for code analysis</span></span>

<span data-ttu-id="16e94-104">程式碼分析規則有各種不同的設定選項。</span><span class="sxs-lookup"><span data-stu-id="16e94-104">Code analysis rules have various configuration options.</span></span> <span data-ttu-id="16e94-105">這些選項會在 [分析器設定檔](configuration-files.md) 中使用語法指定為索引鍵/值組 `<option key> = <option value>` 。</span><span class="sxs-lookup"><span data-stu-id="16e94-105">These options are specified as key-value pairs in an [analyzer configuration file](configuration-files.md) using the syntax `<option key> = <option value>`.</span></span>

<span data-ttu-id="16e94-106">您將設定的最常見選項是 [規則的嚴重性](#severity-level)。</span><span class="sxs-lookup"><span data-stu-id="16e94-106">The most common option you'll configure is a [rule's severity](#severity-level).</span></span> <span data-ttu-id="16e94-107">您可以設定所有分析器規則的嚴重性層級，包括程式 [代碼品質規則](quality-rules/index.md) 和程式 [代碼樣式規則](style-rules/index.md)。</span><span class="sxs-lookup"><span data-stu-id="16e94-107">You can configure severity level for all analyzer rules, including [code quality rules](quality-rules/index.md) and [code style rules](style-rules/index.md).</span></span> <span data-ttu-id="16e94-108">例如，若要啟用規則做為警告，您可以將下列索引鍵/值組新增至檔案 EditorConfig 。</span><span class="sxs-lookup"><span data-stu-id="16e94-108">For example, to enable a rule as a warning, you can add the following key-value pair to an EditorConfig file.</span></span>

`dotnet_diagnostic.<rule ID>.severity = warning`

<span data-ttu-id="16e94-109">您也可以設定其他選項來自訂規則行為：</span><span class="sxs-lookup"><span data-stu-id="16e94-109">You can also configure additional options to customize rule behavior:</span></span>

- <span data-ttu-id="16e94-110">程式碼品質規則有 [其他選項](code-quality-rule-options.md) 可設定行為，例如規則應套用的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="16e94-110">Code quality rules have [additional options](code-quality-rule-options.md) to configure behavior, such as which method names a rule should apply to.</span></span>
- <span data-ttu-id="16e94-111">程式碼樣式規則有 [自訂程式碼樣式選項](code-style-rule-options.md)。</span><span class="sxs-lookup"><span data-stu-id="16e94-111">Code style rules have [custom code style options](code-style-rule-options.md).</span></span>
- <span data-ttu-id="16e94-112">協力廠商分析器規則可以使用自訂索引鍵名稱和值格式來定義自己的設定選項。</span><span class="sxs-lookup"><span data-stu-id="16e94-112">Third party analyzer rules can define their own configuration options, with custom key names and value formats.</span></span>

<span data-ttu-id="16e94-113">在 [分析器設定檔](configuration-files.md) 中設定特定規則嚴重性的語法如下：</span><span class="sxs-lookup"><span data-stu-id="16e94-113">The syntax for configuring a specific rule's severity in an [analyzer configuration file](configuration-files.md) is as follows:</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a><span data-ttu-id="16e94-114">一般選項</span><span class="sxs-lookup"><span data-stu-id="16e94-114">General options</span></span>

<span data-ttu-id="16e94-115">這些選項適用于整個程式碼分析。</span><span class="sxs-lookup"><span data-stu-id="16e94-115">These options apply to code analysis as a whole.</span></span> <span data-ttu-id="16e94-116">它們不能只套用至單一規則或一組規則。</span><span class="sxs-lookup"><span data-stu-id="16e94-116">They cannot be applied only to a single rule or set of rules.</span></span>

### <a name="exclude-generated-code"></a><span data-ttu-id="16e94-117">排除產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="16e94-117">Exclude generated code</span></span>

<span data-ttu-id="16e94-118">您可以藉由將 `generated_code = true | false` 專案新增至 [設定檔](configuration-files.md)，來將其他檔案和資料夾視為產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="16e94-118">You can configure additional files and folders to be treated as generated code by adding a `generated_code = true | false` entry to your [configuration file](configuration-files.md).</span></span> <span data-ttu-id="16e94-119">.NET 程式碼分析器警告在產生的程式碼檔（例如，設計工具產生的檔案）上並不實用，使用者無法編輯這些檔案來修正任何違規。</span><span class="sxs-lookup"><span data-stu-id="16e94-119">.NET code analyzer warnings aren't useful on generated code files, such as designer-generated files, which users can't edit to fix any violations.</span></span> <span data-ttu-id="16e94-120">在大多數情況下，程式碼分析器會略過產生的程式碼檔案，而不會報告這些檔案的違規。</span><span class="sxs-lookup"><span data-stu-id="16e94-120">In most cases, code analyzers skip generated code files and don't report violations on these files.</span></span>

<span data-ttu-id="16e94-121">依預設，具有特定副檔名或自動產生之檔案標頭的檔案會被視為產生的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="16e94-121">By default, files with certain file extensions or auto-generated file headers are treated as generated code files.</span></span> <span data-ttu-id="16e94-122">例如，以或結尾的檔案名 `.designer.cs` `.generated.cs` 會視為產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="16e94-122">For example, a file name ending with `.designer.cs` or `.generated.cs` is considered generated code.</span></span> <span data-ttu-id="16e94-123">此設定選項可讓您指定其他命名模式。</span><span class="sxs-lookup"><span data-stu-id="16e94-123">This configuration option lets you specify additional naming patterns.</span></span>

<span data-ttu-id="16e94-124">例如，若要將名稱結尾為的所有檔案視為產生的程式 `.MyGenerated.cs` 代碼，請新增下列專案：</span><span class="sxs-lookup"><span data-stu-id="16e94-124">For example, to treat all files whose name ends with `.MyGenerated.cs` as generated code, add the following entry:</span></span>

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a><span data-ttu-id="16e94-125">規則特定選項</span><span class="sxs-lookup"><span data-stu-id="16e94-125">Rule-specific options</span></span>

<span data-ttu-id="16e94-126">規則特定選項可以套用至單一規則、一組規則或所有規則。</span><span class="sxs-lookup"><span data-stu-id="16e94-126">Rule-specific options can be applied to a single rule, a set of rules, or all rules.</span></span> <span data-ttu-id="16e94-127">規則特定的選項包括：</span><span class="sxs-lookup"><span data-stu-id="16e94-127">The rule-specific options include:</span></span>

- [<span data-ttu-id="16e94-128">規則嚴重性層級</span><span class="sxs-lookup"><span data-stu-id="16e94-128">Rule severity level</span></span>](#severity-level)
- [<span data-ttu-id="16e94-129">*程式碼品質規則的* 特定選項</span><span class="sxs-lookup"><span data-stu-id="16e94-129">Options specific to *code-quality* rules</span></span>](code-quality-rule-options.md)

### <a name="severity-level"></a><span data-ttu-id="16e94-130">嚴重性層級</span><span class="sxs-lookup"><span data-stu-id="16e94-130">Severity level</span></span>

<span data-ttu-id="16e94-131">下表顯示您可以為所有分析器規則（包括程式 [代碼品質](quality-rules/index.md) 和程式 [代碼樣式](style-rules/index.md) 規則）設定的不同規則嚴重性。</span><span class="sxs-lookup"><span data-stu-id="16e94-131">The following table shows the different rule severities that you can configure for all analyzer rules, including [code quality](quality-rules/index.md) and [code style](style-rules/index.md) rules.</span></span>

| <span data-ttu-id="16e94-132">Severity</span><span class="sxs-lookup"><span data-stu-id="16e94-132">Severity</span></span> | <span data-ttu-id="16e94-133">組建階段行為</span><span class="sxs-lookup"><span data-stu-id="16e94-133">Build-time behavior</span></span> |
|-|-|
| `error` | <span data-ttu-id="16e94-134">違規會顯示為組建 *錯誤* ，導致組建失敗。</span><span class="sxs-lookup"><span data-stu-id="16e94-134">Violations appear as build *errors* and cause builds to fail.</span></span>|
| `warning` | <span data-ttu-id="16e94-135">違規會顯示為組建 *警告* ，但不會造成組建失敗 (除非您有選項設定為 [錯誤時將警告視為錯誤]) 。</span><span class="sxs-lookup"><span data-stu-id="16e94-135">Violations appear as build *warnings* but do not cause builds to fail (unless you have an option set to treat warnings as errors).</span></span> |
| `suggestion` | <span data-ttu-id="16e94-136">違規在 Visual Studio IDE 中會顯示為組建 *訊息* 和建議。</span><span class="sxs-lookup"><span data-stu-id="16e94-136">Violations appear as build *messages* and as suggestions in the Visual Studio IDE.</span></span> |
| `silent` | <span data-ttu-id="16e94-137">使用者看不到違規。</span><span class="sxs-lookup"><span data-stu-id="16e94-137">Violations aren't visible to the user.</span></span> |
| `none` | <span data-ttu-id="16e94-138">規則已完全隱藏。</span><span class="sxs-lookup"><span data-stu-id="16e94-138">Rule is suppressed completely.</span></span> |
| `default` | <span data-ttu-id="16e94-139">使用規則的預設嚴重性。</span><span class="sxs-lookup"><span data-stu-id="16e94-139">The default severity of the rule is used.</span></span> |

> [!TIP]
> <span data-ttu-id="16e94-140">如需有關 Visual Studio 中的規則嚴重性如何呈現的詳細資訊，請參閱 [嚴重性層級](/visualstudio/ide/editorconfig-language-conventions#severity-levels)。</span><span class="sxs-lookup"><span data-stu-id="16e94-140">For information about how rule severities surface in Visual Studio, see [Severity levels](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span></span>

#### <a name="scope"></a><span data-ttu-id="16e94-141">影響範圍</span><span class="sxs-lookup"><span data-stu-id="16e94-141">Scope</span></span>

<span data-ttu-id="16e94-142">若要設定單一規則的規則嚴重性，請使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="16e94-142">To set the rule severity for a single rule, use the following syntax.</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

<span data-ttu-id="16e94-143">若要設定分析器規則類別的預設規則嚴重性，請使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="16e94-143">To set the default rule severity for a category of analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

<span data-ttu-id="16e94-144">若要設定所有分析器規則的預設規則嚴重性，請使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="16e94-144">To set the default rule severity for all analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a><span data-ttu-id="16e94-145">優先順序</span><span class="sxs-lookup"><span data-stu-id="16e94-145">Precedence</span></span>

<span data-ttu-id="16e94-146">如果您有多個可套用至相同規則識別碼的嚴重性設定專案，則會依下列順序選擇優先級：</span><span class="sxs-lookup"><span data-stu-id="16e94-146">If you have multiple severity configuration entries that can be applied to the same rule ID, precedence is chosen in the following order:</span></span>

- <span data-ttu-id="16e94-147">依識別碼個別規則的專案會優先于類別目錄的專案。</span><span class="sxs-lookup"><span data-stu-id="16e94-147">An entry for an individual rule by ID takes precedence over an entry for a category.</span></span>
- <span data-ttu-id="16e94-148">分類的專案優先于所有分析器規則的專案。</span><span class="sxs-lookup"><span data-stu-id="16e94-148">An entry for a category takes precedence over an entry for all analyzer rules.</span></span>

<span data-ttu-id="16e94-149">請考慮下列範例，其中 [CA1822](/visualstudio/code-quality/ca1822) 具有「效能」類別：</span><span class="sxs-lookup"><span data-stu-id="16e94-149">Consider the following example, where [CA1822](/visualstudio/code-quality/ca1822) has the category "Performance":</span></span>

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

<span data-ttu-id="16e94-150">在上述範例中，這三個嚴重性專案都適用于 CA1822。</span><span class="sxs-lookup"><span data-stu-id="16e94-150">In the preceding example, all three severity entries are applicable to CA1822.</span></span> <span data-ttu-id="16e94-151">不過，使用指定的優先順序規則時，第一個以規則識別碼為基礎的專案會優先于下一個專案。</span><span class="sxs-lookup"><span data-stu-id="16e94-151">However, using the specified precedence rules, the first rule ID-based entry wins over the next entries.</span></span> <span data-ttu-id="16e94-152">在此範例中，CA1822 會具有的有效嚴重性 `error` 。</span><span class="sxs-lookup"><span data-stu-id="16e94-152">In this example, CA1822 will have an effective severity of `error`.</span></span> <span data-ttu-id="16e94-153">「效能」類別中的所有其他規則都會具有的嚴重性 `warning` 。</span><span class="sxs-lookup"><span data-stu-id="16e94-153">All other rules within the "Performance" category will have a severity of `warning`.</span></span>

<span data-ttu-id="16e94-154">如需有關如何決定檔案間優先順序的詳細資訊，請參閱 [設定檔檔的「優先順序」一節](configuration-files.md#precedence)。</span><span class="sxs-lookup"><span data-stu-id="16e94-154">For information about how inter-file precedence is decided, see the [Precedence section of the Configuration files article](configuration-files.md#precedence).</span></span>
