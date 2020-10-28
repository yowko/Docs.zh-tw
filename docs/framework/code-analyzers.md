---
title: .NET Framework 的程式碼分析器
titleSuffix: ''
description: 瞭解如何使用 .NET Framework 分析器套件中的分析器，找出並解決程式碼中的問題。
author: billwagner
ms.author: wiwagn
ms.date: 10/23/2020
ms.openlocfilehash: 69dfbc9f9645c7f602ffbce46308b241c119fd96
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687844"
---
# <a name="code-analysis"></a><span data-ttu-id="0053f-103">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="0053f-103">Code analysis</span></span>

<span data-ttu-id="0053f-104">您可以使用程式碼分析器找出 .NET Framework 應用程式程式碼中的潛在問題。</span><span class="sxs-lookup"><span data-stu-id="0053f-104">You can use code analyzers to find potential issues in your .NET Framework application code.</span></span> <span data-ttu-id="0053f-105">分析器會找出潛在的問題，並為其提供建議的修正程式。</span><span class="sxs-lookup"><span data-stu-id="0053f-105">The analyzers find potential issues and suggest fixes for them.</span></span>

<span data-ttu-id="0053f-106">以 Roslyn 為基礎的程式碼分析器會在您撰寫程式碼時以互動方式在 Visual Studio 中執行，或作為 CI 組建的一部分執行。</span><span class="sxs-lookup"><span data-stu-id="0053f-106">Roslyn-based code analyzers run interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="0053f-107">您應儘早在開發週期中將分析器新增至專案。</span><span class="sxs-lookup"><span data-stu-id="0053f-107">You should add the analyzers to your project as early as possible in the development cycle.</span></span> <span data-ttu-id="0053f-108">在程式碼中找到任何潛在問題的速度愈快，修正就愈容易。</span><span class="sxs-lookup"><span data-stu-id="0053f-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="0053f-109">分析器會標示現有程式碼中的問題，並在您繼續開發時警告新問題。</span><span class="sxs-lookup"><span data-stu-id="0053f-109">The analyzers flag issues in existing code and warn about new issues as you continue development.</span></span>

## <a name="install-and-configure-analyzers"></a><span data-ttu-id="0053f-110">安裝和設定分析器</span><span class="sxs-lookup"><span data-stu-id="0053f-110">Install and configure analyzers</span></span>

<span data-ttu-id="0053f-111">[Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet 套件提供 .NET Framework Analyzer。</span><span class="sxs-lookup"><span data-stu-id="0053f-111">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="0053f-112">此套件提供 .NET Framework Api 專屬的分析器，包括安全性分析器。</span><span class="sxs-lookup"><span data-stu-id="0053f-112">This package provides analyzers that are specific to .NET Framework APIs, which includes security analyzers.</span></span> <span data-ttu-id="0053f-113">套件隨附于 [CodeAnalysis. 將 microsoft.codeanalysis.fxcopanalyzers 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)，因此，如果您安裝該套件，則不需要個別安裝 .NET Framework 分析器。</span><span class="sxs-lookup"><span data-stu-id="0053f-113">The package is included with the [Microsoft.CodeAnalysis.FxCopAnalyzers package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), so if you install that package, there's no need to install the .NET Framework analyzers separately.</span></span>

<span data-ttu-id="0053f-114">在您想要執行分析器的每個專案上安裝 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="0053f-114">Install the NuGet package on every project where you want the analyzers to run.</span></span> <span data-ttu-id="0053f-115">只有一位開發人員必須將它們新增至專案。</span><span class="sxs-lookup"><span data-stu-id="0053f-115">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="0053f-116">分析器套件是一種專案相依性，而且會在具有已更新方案之後，於每位開發人員的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="0053f-116">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="0053f-117">若要安裝套件，請在專案上按一下滑鼠右鍵，然後選取 [管理相依性]。</span><span class="sxs-lookup"><span data-stu-id="0053f-117">To install the package, right-click on the project, and select "Manage Dependencies".</span></span> <span data-ttu-id="0053f-118">從 NuGet explorer 搜尋 ".Netframework"。</span><span class="sxs-lookup"><span data-stu-id="0053f-118">From the NuGet explorer, search for "Microsoft.NetFramework.Analyzers".</span></span> <span data-ttu-id="0053f-119">在您方案的所有專案中安裝最新穩定版本。</span><span class="sxs-lookup"><span data-stu-id="0053f-119">Install the latest stable version in all projects in your solution.</span></span>

## <a name="use-the-analyzers"></a><span data-ttu-id="0053f-120">流量分析器</span><span class="sxs-lookup"><span data-stu-id="0053f-120">Use the analyzers</span></span>

<span data-ttu-id="0053f-121">安裝 NuGet 套件之後，請建置方案。</span><span class="sxs-lookup"><span data-stu-id="0053f-121">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="0053f-122">分析器將會報告它在您的程式碼基底中找到的任何問題。</span><span class="sxs-lookup"><span data-stu-id="0053f-122">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="0053f-123">在 Visual Studio [錯誤清單] 視窗中，這些問題回報為警告，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="0053f-123">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![.NET Framework 分析器回報的問題。](./media/framework-analyzers-2.png)

<span data-ttu-id="0053f-125">當您撰寫程式碼時，會在程式碼的任何潛在問題下方看到曲線。</span><span class="sxs-lookup"><span data-stu-id="0053f-125">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="0053f-126">將滑鼠停留在任何問題上以取得詳細資訊，並查看任何可能修正的建議，如下列影像所示：</span><span class="sxs-lookup"><span data-stu-id="0053f-126">Hover over any issue to get more information and see suggestions for any possible fix, as shown in the following image:</span></span>

![程式碼分析器發現的互動式問題報表。](./media/framework-analyzers-1.png)

<span data-ttu-id="0053f-128">如需詳細資訊，請參閱 [Visual Studio 中的程式碼分析](/visualstudio/code-quality/roslyn-analyzers-overview)。</span><span class="sxs-lookup"><span data-stu-id="0053f-128">For more information, see [Code analysis in Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

## <a name="types-of-rules"></a><span data-ttu-id="0053f-129">規則類型</span><span class="sxs-lookup"><span data-stu-id="0053f-129">Types of rules</span></span>

<span data-ttu-id="0053f-130">分析器會檢查方案中的程式碼，並以前置詞呈現警告 `CA` 。</span><span class="sxs-lookup"><span data-stu-id="0053f-130">The analyzers examine the code in your solution and surface warnings with a `CA` prefix.</span></span> <span data-ttu-id="0053f-131">如需所有可能警告的清單，請參閱程式 [代碼品質規則](../fundamentals/code-analysis/quality-rules/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0053f-131">For a list of all possible warnings, see [Code quality rules](../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="0053f-132">只有部分警告適用于 .NET Framework 的 API，包括：</span><span class="sxs-lookup"><span data-stu-id="0053f-132">Only some of these warnings apply to .NET Framework APIS, including:</span></span>

- [<span data-ttu-id="0053f-133">CA1058:類型不應該擴充特定基底類型</span><span class="sxs-lookup"><span data-stu-id="0053f-133">CA1058: Types should not extend certain base types</span></span>](../fundamentals/code-analysis/quality-rules/ca1058.md)

- [<span data-ttu-id="0053f-134">CA2153：不要攔截損毀狀態例外</span><span class="sxs-lookup"><span data-stu-id="0053f-134">CA2153: Do not catch corrupted state exceptions</span></span>](../fundamentals/code-analysis/quality-rules/ca2153.md)

- [<span data-ttu-id="0053f-135">CA2229:必須實作序列化建構函式</span><span class="sxs-lookup"><span data-stu-id="0053f-135">CA2229: Implement serialization constructors</span></span>](../fundamentals/code-analysis/quality-rules/ca2229.md)

- [<span data-ttu-id="0053f-136">CA2235:必須標記所有不可序列化的欄位</span><span class="sxs-lookup"><span data-stu-id="0053f-136">CA2235: Mark all non-serializable fields</span></span>](../fundamentals/code-analysis/quality-rules/ca2235.md)

- [<span data-ttu-id="0053f-137">CA2237：必須以可序列化標記 ISerializable 類型</span><span class="sxs-lookup"><span data-stu-id="0053f-137">CA2237: Mark ISerializable types with serializable</span></span>](../fundamentals/code-analysis/quality-rules/ca2237.md)

- [<span data-ttu-id="0053f-138">CA3075：XML 中的不安全 DTD 處理</span><span class="sxs-lookup"><span data-stu-id="0053f-138">CA3075: Insecure DTD processing in XML</span></span>](../fundamentals/code-analysis/quality-rules/ca3075.md)

- [<span data-ttu-id="0053f-139">CA5350：請勿使用弱式密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="0053f-139">CA5350: Do not use weak cryptographic algorithms</span></span>](../fundamentals/code-analysis/quality-rules/ca5350.md)

- [<span data-ttu-id="0053f-140">CA5351 不使用中斷的密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="0053f-140">CA5351 Do not use broken cryptographic algorithms</span></span>](../fundamentals/code-analysis/quality-rules/ca5351.md)

## <a name="see-also"></a><span data-ttu-id="0053f-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="0053f-141">See also</span></span>

- [<span data-ttu-id="0053f-142">Visual Studio 中的程式碼分析</span><span class="sxs-lookup"><span data-stu-id="0053f-142">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="0053f-143">.NET SDK 中的程式碼分析</span><span class="sxs-lookup"><span data-stu-id="0053f-143">Code analysis in the .NET SDK</span></span>](../fundamentals/code-analysis/overview.md)
