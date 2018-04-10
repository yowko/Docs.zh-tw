---
title: Roslyn 分析器 - .NET
description: 了解可找出問題並針對問題提供建議的 Roslyn 分析器相關資訊。
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 8c6524716ba403bc426df8dc33e64b8b2934d3d7
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2018
---
# <a name="the-roslyn-based-analyzers"></a><span data-ttu-id="2085a-104">Roslyn 分析器</span><span class="sxs-lookup"><span data-stu-id="2085a-104">The Roslyn based Analyzers</span></span>

<span data-ttu-id="2085a-105">Roslyn 分析器會使用 .NET Compiler SDK (Roslyn API) 來分析您專案的原始程式碼，以找出問題並建議修正。</span><span class="sxs-lookup"><span data-stu-id="2085a-105">Roslyn-based analyzers use the .NET Compiler SDK (Roslyn APIs) to analyze your project's source code to find issues and suggest corrections.</span></span> <span data-ttu-id="2085a-106">不同的分析器會尋找不同類別的問題，範圍從可能導致錯誤 (bug) 的作法，以及安全性考量與 API 相容性等等。</span><span class="sxs-lookup"><span data-stu-id="2085a-106">Different analyzers look for different classes of issues, ranging from practices that are likely to cause bugs to security concerns to API compatibility.</span></span>

<span data-ttu-id="2085a-107">Roslyn 分析器能夠以互動方式運作，也可以在建置期間運作。</span><span class="sxs-lookup"><span data-stu-id="2085a-107">Roslyn-based analyzers work both interactively and during builds.</span></span> <span data-ttu-id="2085a-108">當在 Visual Studio 或命令列組建中時，分析器會提供不同的指引。</span><span class="sxs-lookup"><span data-stu-id="2085a-108">The analyzer provides different guidance when in Visual Studio or in command-line builds.</span></span>

<span data-ttu-id="2085a-109">在 Visual Studio 中編輯程式碼時，分析器會在您進行變更時執行，並在您建立會引發顧慮的程式碼時立刻攔截可能的問題。</span><span class="sxs-lookup"><span data-stu-id="2085a-109">While you edit code in Visual Studio, the analyzers run as you make changes, catching possible issues as soon as you create code that trigger concerns.</span></span> <span data-ttu-id="2085a-110">任何問題底下都會以波浪線來突顯。</span><span class="sxs-lookup"><span data-stu-id="2085a-110">Any issues are highlighted with squiggles under any issue.</span></span> <span data-ttu-id="2085a-111">Visual Studio 會顯示燈泡，當您按一下燈泡時，分析器會針對該問題建議可能的修正。</span><span class="sxs-lookup"><span data-stu-id="2085a-111">Visual Studio displays a light bulb, and when you click on it the analyzer will suggest possible fixes for that issue.</span></span> <span data-ttu-id="2085a-112">當您建置專案時，不論在 Visual Studio 中或從命令列，都將會分析所有的原始程式碼，且分析器會提供潛在問題的完整清單。</span><span class="sxs-lookup"><span data-stu-id="2085a-112">When you build the project, either in Visual Studio or from the command line, all the source code is analyzed and the analyzer provides a full list of potential issues.</span></span> <span data-ttu-id="2085a-113">下圖將示範一個範例。</span><span class="sxs-lookup"><span data-stu-id="2085a-113">The following figure shows one example.</span></span>

![架構分析器回報的問題](./media/framework-analyzers-2.png)

<span data-ttu-id="2085a-115">根據問題的嚴重性，Roslyn 分析器會將潛在問題回報為錯誤、警告或資訊。</span><span class="sxs-lookup"><span data-stu-id="2085a-115">Roslyn-based analyzers report potential issues as errors, warnings, or information based on the severity of the issue.</span></span>

<span data-ttu-id="2085a-116">在您的專案中，您可以 NuGet 套件來安裝 Roslyn 分析器。</span><span class="sxs-lookup"><span data-stu-id="2085a-116">You install Roslyn-based analyzers as NuGet packages in your project.</span></span> <span data-ttu-id="2085a-117">這會還原已設定的分析器以及各個分析器的所有設定，並在任何開發人員電腦上為該專案執行。</span><span class="sxs-lookup"><span data-stu-id="2085a-117">The configured analyzers and any settings for each analyzer are restored and run on any developer's machine for that project.</span></span>

> [!NOTE]
> <span data-ttu-id="2085a-118">Roslyn 分析器的使用者體驗有別於「程式碼分析」程式庫 (例如舊版 FxCop 和安全性分析工具)。</span><span class="sxs-lookup"><span data-stu-id="2085a-118">The user experience for Roslyn-based analyzers is different than that of the Code Analysis libraries like the older versions of FxCop and the security analysis tools.</span></span>  <span data-ttu-id="2085a-119">您不需要明確地執行 Roslyn 分析器。</span><span class="sxs-lookup"><span data-stu-id="2085a-119">You don't need to explicitly run the Roslyn-based analyzers.</span></span> <span data-ttu-id="2085a-120">不需要使用 Visual Studio 中 [分析] 功能表上的 [執行程式碼分析] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="2085a-120">There's no need to use the "Run Code Analysis" menu items on the "Analyze" menu in Visual Studio.</span></span> <span data-ttu-id="2085a-121">Roslyn 分析器會在您工作時以非同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="2085a-121">Roslyn-based analyzers run asychronously as you work.</span></span> 

## <a name="more-information-on-specific-analyzers"></a><span data-ttu-id="2085a-122">特定分析器的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="2085a-122">More information on specific analyzers</span></span>

<span data-ttu-id="2085a-123">此章節將討論下列分析器：</span><span class="sxs-lookup"><span data-stu-id="2085a-123">The following analyzers are covered in this section:</span></span>

<span data-ttu-id="2085a-124">[API 分析器](api-analyzer.md)：此分析器會在您的程式碼中檢查潛在的相容性風險，或者檢查程式碼中是否使用已被取代的 API。</span><span class="sxs-lookup"><span data-stu-id="2085a-124">[API Analyzer](api-analyzer.md): This analyzer examines your code for potential compatibility risks or uses of deprecated APIs.</span></span>    
<span data-ttu-id="2085a-125">[架構分析器](framework-analyzer.md)：此分析器會檢查您的程式碼，以確保程式碼遵循適用於 .NET Framework 應用程式的指導方針。</span><span class="sxs-lookup"><span data-stu-id="2085a-125">[Framework Analyzer](framework-analyzer.md): This analyzer examines your code to ensure it follows the guidelines for .NET Framework applications.</span></span> <span data-ttu-id="2085a-126">這些規則包含數個安全性建議。</span><span class="sxs-lookup"><span data-stu-id="2085a-126">These rules include several security-based recommendations.</span></span>
