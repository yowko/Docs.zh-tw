---
title: '預先定義的設定檔 (程式碼分析) '
description: 瞭解如何使用預先定義的 editorconfig 和規則集檔案，以特定類型的程式碼分析為目標。
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 4937dcab1183fa3f63be4afc71627a7c7c08c6bd
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "96586219"
---
# <a name="predefined-configuration-files"></a><span data-ttu-id="62a17-103">預先定義的設定檔</span><span class="sxs-lookup"><span data-stu-id="62a17-103">Predefined configuration files</span></span>

<span data-ttu-id="62a17-104">預先定義的 EditorConfig 和 [規則集](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) 檔案可讓您快速且輕鬆地啟用類別的程式碼品質規則，例如安全性或設計規則。</span><span class="sxs-lookup"><span data-stu-id="62a17-104">Predefined EditorConfig and [rule set](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) files are available that make it quick and easy to enable a category of code quality rules, such as security or design rules.</span></span> <span data-ttu-id="62a17-105">藉由啟用特定類別的規則，您可以識別目標問題和特定條件。</span><span class="sxs-lookup"><span data-stu-id="62a17-105">By enabling a specific category of rules, you can identify targeted issues and specific conditions.</span></span> <span data-ttu-id="62a17-106">若要存取這些預先定義的檔案，請安裝 [CodeAnalysis NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet analyzer 套件。</span><span class="sxs-lookup"><span data-stu-id="62a17-106">To access these predefined files, install the [Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet analyzer package.</span></span>

<span data-ttu-id="62a17-107">[CodeAnalysis. NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) 包含預先定義的 EditorConfig 檔案和規則集，適用于下列規則類別：</span><span class="sxs-lookup"><span data-stu-id="62a17-107">[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) includes predefined EditorConfig files and rule sets for the following rule categories:</span></span>

- <span data-ttu-id="62a17-108">所有規則</span><span class="sxs-lookup"><span data-stu-id="62a17-108">All rules</span></span>
- <span data-ttu-id="62a17-109">資料流程</span><span class="sxs-lookup"><span data-stu-id="62a17-109">Dataflow</span></span>
- <span data-ttu-id="62a17-110">設計</span><span class="sxs-lookup"><span data-stu-id="62a17-110">Design</span></span>
- <span data-ttu-id="62a17-111">文件</span><span class="sxs-lookup"><span data-stu-id="62a17-111">Documentation</span></span>
- <span data-ttu-id="62a17-112">全球化</span><span class="sxs-lookup"><span data-stu-id="62a17-112">Globalization</span></span>
- <span data-ttu-id="62a17-113">互通性</span><span class="sxs-lookup"><span data-stu-id="62a17-113">Interoperability</span></span>
- <span data-ttu-id="62a17-114">可維護性</span><span class="sxs-lookup"><span data-stu-id="62a17-114">Maintainability</span></span>
- <span data-ttu-id="62a17-115">命名</span><span class="sxs-lookup"><span data-stu-id="62a17-115">Naming</span></span>
- <span data-ttu-id="62a17-116">效能</span><span class="sxs-lookup"><span data-stu-id="62a17-116">Performance</span></span>
- <span data-ttu-id="62a17-117">從 FxCop 移植</span><span class="sxs-lookup"><span data-stu-id="62a17-117">Ported from FxCop</span></span>
- <span data-ttu-id="62a17-118">可靠性</span><span class="sxs-lookup"><span data-stu-id="62a17-118">Reliability</span></span>
- <span data-ttu-id="62a17-119">安全性</span><span class="sxs-lookup"><span data-stu-id="62a17-119">Security</span></span>
- <span data-ttu-id="62a17-120">使用方式</span><span class="sxs-lookup"><span data-stu-id="62a17-120">Usage</span></span>

<span data-ttu-id="62a17-121">每個規則類別都有 EditorConfig 或規則集檔案，以：</span><span class="sxs-lookup"><span data-stu-id="62a17-121">Each of those categories of rules has an EditorConfig or rule set file to:</span></span>

- <span data-ttu-id="62a17-122">啟用類別 (中的所有規則，並停用所有其他規則) </span><span class="sxs-lookup"><span data-stu-id="62a17-122">Enable all the rules in the category (and disable all other rules)</span></span>
- <span data-ttu-id="62a17-123">使用每個規則的預設嚴重性，並預設為啟用 (並停用所有其他規則) </span><span class="sxs-lookup"><span data-stu-id="62a17-123">Use each rule's default severity and enabled by default setting (and disable all other rules)</span></span>

> [!TIP]
> <span data-ttu-id="62a17-124">「所有規則」類別具有其他 EditorConfig 或規則集檔案，以停用所有規則。</span><span class="sxs-lookup"><span data-stu-id="62a17-124">The "all rules" category has an additional EditorConfig or rule set file to disable all rules.</span></span> <span data-ttu-id="62a17-125">使用此檔案可快速清除專案中的任何分析器警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="62a17-125">Use this file to quickly get rid of any analyzer warnings or errors in a project.</span></span>

## <a name="predefined-editorconfig-files"></a><span data-ttu-id="62a17-126">預先定義的 EditorConfig 檔案</span><span class="sxs-lookup"><span data-stu-id="62a17-126">Predefined EditorConfig files</span></span>

<span data-ttu-id="62a17-127">CodeAnalysis. NetAnalyzers analyzer 套件的預先定義 EditorConfig 檔位於安裝 NuGet 套件的 *EditorConfig* 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="62a17-127">The predefined EditorConfig files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *editorconfig* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="62a17-128">例如，啟用所有安全性規則的 EditorConfig 檔案位於 *EditorConfig/SecurityRulesEnabled/EditorConfig*。</span><span class="sxs-lookup"><span data-stu-id="62a17-128">For example, the EditorConfig file to enable all security rules is located at *editorconfig/SecurityRulesEnabled/.editorconfig*.</span></span>

<span data-ttu-id="62a17-129">將所選的 *editorconfig* 檔案複製到您專案的根目錄。</span><span class="sxs-lookup"><span data-stu-id="62a17-129">Copy the chosen *.editorconfig* file to your project's root directory.</span></span>

## <a name="predefined-rule-sets"></a><span data-ttu-id="62a17-130">預先定義的規則集</span><span class="sxs-lookup"><span data-stu-id="62a17-130">Predefined rule sets</span></span>

<span data-ttu-id="62a17-131">適用于 CodeAnalysis. NetAnalyzers 分析器套件的預先定義規則集檔案，位於安裝 NuGet 套件的 [ *規則* 集] 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="62a17-131">The predefined rule set files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *rulesets* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="62a17-132">例如，用來啟用所有安全性規則的規則集檔案位於 [規則集] */[SecurityRulesEnabled*]。</span><span class="sxs-lookup"><span data-stu-id="62a17-132">For example, the rule set file to enable all security rules is located at *rulesets/SecurityRulesEnabled.ruleset*.</span></span> <span data-ttu-id="62a17-133">複製一或多個規則集，並將其貼到包含專案的目錄中。</span><span class="sxs-lookup"><span data-stu-id="62a17-133">Copy one or more of the rule sets and paste them in the directory that contains your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="62a17-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62a17-134">See also</span></span>

- [<span data-ttu-id="62a17-135">分析器設定</span><span class="sxs-lookup"><span data-stu-id="62a17-135">Analyzer configuration</span></span>](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [<span data-ttu-id="62a17-136">適用于 EditorConfig 的 .NET 程式碼樣式規則選項</span><span class="sxs-lookup"><span data-stu-id="62a17-136">.NET code style rule options for EditorConfig</span></span>](code-style-rule-options.md)
