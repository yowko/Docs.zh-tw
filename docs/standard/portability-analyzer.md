---
title: .NET Portability Analyzer - .NET | Microsoft Docs
description: "了解如何使用.NET Portability Analyzer 工具來評估程式碼移植到不同 .NET 實作之間的可行性。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.translationtype: HT
ms.sourcegitcommit: 3155295489e1188640dae5aa5bf9fdceb7480ed6
ms.openlocfilehash: adb1971c14c8ff8c147dba378ae0e9a5bc0fb5ad
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---

# <a name="the-net-portability-analyzer"></a><span data-ttu-id="06d1b-104">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="06d1b-104">The .NET Portability Analyzer</span></span>

<span data-ttu-id="06d1b-105">要將您的程式庫變成多平台？</span><span class="sxs-lookup"><span data-stu-id="06d1b-105">Want to make your libraries multi-platform?</span></span> <span data-ttu-id="06d1b-106">想要查看花費多少功夫才能讓您的應用程式與其他 .NET 實作相容嗎？</span><span class="sxs-lookup"><span data-stu-id="06d1b-106">Want to see how much work is required to make your application compatible with other .NET implementations?</span></span> <span data-ttu-id="06d1b-107">[.NET Portability Analyzer](http://go.microsoft.com/fwlink/?LinkID=507467) 是一項工具，其藉由分析組件來提供您有關程式在跨 .NET 實作上之彈性的詳細報表。</span><span class="sxs-lookup"><span data-stu-id="06d1b-107">The [.NET Portability Analyzer](http://go.microsoft.com/fwlink/?LinkID=507467) is a tool that provides you with a detailed report on how flexible your program is across .NET implementations by analyzing assemblies.</span></span> <span data-ttu-id="06d1b-108">Portability Analyzer 會以 Visual Studio 擴充功能和主控台應用程式的形式提供給您。</span><span class="sxs-lookup"><span data-stu-id="06d1b-108">The Portability Analyzer is offered as a Visual Studio Extension and as a console app.</span></span>

## <a name="new-targets"></a><span data-ttu-id="06d1b-109">新目標</span><span class="sxs-lookup"><span data-stu-id="06d1b-109">New targets</span></span>

* <span data-ttu-id="06d1b-110">[.NET core](https://dotnetfoundation.org/net-core)︰具有模組化的設計，採用並存，並且適合在跨平台的情況下使用。</span><span class="sxs-lookup"><span data-stu-id="06d1b-110">[.NET Core](https://dotnetfoundation.org/net-core): Has a modular design, employs side-by-side, and targets cross-platform scenarios.</span></span> <span data-ttu-id="06d1b-111">並存可讓您採用新的 .NET Core 版本，而不會中斷其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="06d1b-111">Side-by-side allows you to adopt new .NET Core versions without breaking other apps.</span></span>
* <span data-ttu-id="06d1b-112">[ASP.NET Core](https://dotnetfoundation.org/asp-net-core)︰是建置於 .NET Core 上的現代 Web 架構，因此提供開發人員相同的優點。</span><span class="sxs-lookup"><span data-stu-id="06d1b-112">[ASP.NET Core](https://dotnetfoundation.org/asp-net-core): is a modern web-framework built on .NET Core thus giving developers the same benefits.</span></span>
* <span data-ttu-id="06d1b-113">[通用 Windows 平台](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance)︰改善 Windows 市集應用程式的效能，這些應用程式在 x64 和 ARM 電腦上使用 .NET Native 的靜態編譯來執行。</span><span class="sxs-lookup"><span data-stu-id="06d1b-113">[Universal Windows Platform](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): Improve performance of your Windows Store apps that run on x64 and ARM machines by using .NET Native’s static compilation.</span></span> 
* <span data-ttu-id="06d1b-114">.NET Core + 平台延伸模組：包含 .NET Core API，以及 .NET 生態系統中的其他 API，例如 WCF、ASP.NET Core、FSharp 和 Azure。</span><span class="sxs-lookup"><span data-stu-id="06d1b-114">.NET Core + Platform Extensions: Includes the .NET Core APIs in addition to other APIs in the .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>
* <span data-ttu-id="06d1b-115">.NET Standard + 平台延伸模組：包含 .NET Standard API，以及其他 .NET 生態系統，例如 WCF、ASP.NET Core、FSharp 和 Azure。</span><span class="sxs-lookup"><span data-stu-id="06d1b-115">.NET Standard + Platform Extensions: Includes the .NET Standard APIs in addition to other .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>

## <a name="how-to-use-portability-analyzer"></a><span data-ttu-id="06d1b-116">如何使用 Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="06d1b-116">How to use Portability Analyzer</span></span>

<span data-ttu-id="06d1b-117">若要開始使用.NET Portability Analyzer，必須從 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=507467) 下載及安裝此延伸模組。</span><span class="sxs-lookup"><span data-stu-id="06d1b-117">To begin using the .NET Portability Analyzer, you first need to download and install the extension from the [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=507467).</span></span> <span data-ttu-id="06d1b-118">它適用於 Visual Studio 2015 和 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="06d1b-118">It works on Visual Studio 2015 and Visual Studio 2017.</span></span> <span data-ttu-id="06d1b-119">您可以在 Visual Studio 中，使用 [分析] > [Portability Analyzer Settings] (Portability Analyzer 設定) 設定此工具，然後選取您的目標平台。</span><span class="sxs-lookup"><span data-stu-id="06d1b-119">You can configure it in Visual Studio via **Analyze** > **Portability Analyzer Settings** and select your Target Platforms.</span></span>

![可攜性螢幕擷取畫面](./media/portability-analyzer/portability-screenshot.png)

<span data-ttu-id="06d1b-121">若要分析整個專案，在方案總管中以滑鼠右鍵按一下您的專案，然後選取 [Analyze Assembly Portability] (分析組件可攜性)。</span><span class="sxs-lookup"><span data-stu-id="06d1b-121">To analyze your entire project, right-click on your project in **Solution Explorer** and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="06d1b-122">否則，請移至 [分析] 功能表，然後選取 [Analyze Assembly Portability] (分析組件可攜性)。</span><span class="sxs-lookup"><span data-stu-id="06d1b-122">Otherwise, go to the **Analyze** menu and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="06d1b-123">從這裡選取專案的可執行檔或 DLL。</span><span class="sxs-lookup"><span data-stu-id="06d1b-123">From there, select your project’s executable or DLL.</span></span>

![可攜性方案總管](./media/portability-analyzer/portability-solution-explorer.png)

<span data-ttu-id="06d1b-125">執行分析之後，您會看到 .NET Portability 的報表。</span><span class="sxs-lookup"><span data-stu-id="06d1b-125">After running the analysis, you will see your .NET Portability Report.</span></span> <span data-ttu-id="06d1b-126">僅有目標平台不支援的類型才會顯示在清單中，您可以在 [錯誤清單] 的 [訊息] 索引標籤中檢閱建議。</span><span class="sxs-lookup"><span data-stu-id="06d1b-126">Only types that are unsupported by a target platform appear in the list and you can review recommendations in the **Messages** tab in the **Error List**.</span></span> <span data-ttu-id="06d1b-127">您也可以直接從 [訊息] 索引標籤跳到有問題的地方。</span><span class="sxs-lookup"><span data-stu-id="06d1b-127">You can also jump to problem areas directly from the **Messages** tab.</span></span>

![可攜性報表](./media/portability-analyzer/portability-report.png)

<span data-ttu-id="06d1b-129">不想使用 Visual Studio？</span><span class="sxs-lookup"><span data-stu-id="06d1b-129">Don’t want to use Visual Studio?</span></span> <span data-ttu-id="06d1b-130">您也可以從命令提示字元使用 Portability Analyzer。</span><span class="sxs-lookup"><span data-stu-id="06d1b-130">You can also use the Portability Analyzer from the command prompt.</span></span> <span data-ttu-id="06d1b-131">下載 [API Portability Analyzer](http://www.microsoft.com/download/details.aspx?id=42678)。</span><span class="sxs-lookup"><span data-stu-id="06d1b-131">Just download the [API Portability Analyzer](http://www.microsoft.com/download/details.aspx?id=42678).</span></span>

*   <span data-ttu-id="06d1b-132">輸入下列命令分析目前的目錄︰`\...\ApiPort.exe analyze -f .`</span><span class="sxs-lookup"><span data-stu-id="06d1b-132">Type the following command to analyze the current directory: `\...\ApiPort.exe analyze -f .`</span></span>
*   <span data-ttu-id="06d1b-133">若要分析特定的 .dll 檔案清單，請輸入下列命令︰`\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span><span class="sxs-lookup"><span data-stu-id="06d1b-133">To analyze a specific list of .dll files, type the following command: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span></span>

<span data-ttu-id="06d1b-134">您的 .NET Portability 報表會以 Excel 檔案 (*.xlsx*) 格式儲存在您目前目錄中。</span><span class="sxs-lookup"><span data-stu-id="06d1b-134">Your .NET Portability Report is saved as an Excel file (*.xlsx*) in your current directory.</span></span> <span data-ttu-id="06d1b-135">Excel 活頁簿中的 [詳細資料] 索引標籤會包含更多的資訊。</span><span class="sxs-lookup"><span data-stu-id="06d1b-135">The **Details** tab in the Excel Workbook contains more information.</span></span>

<span data-ttu-id="06d1b-136">如需 .NET Portability Analyzer 的詳細資訊，請瀏覽 [GitHub 文件](https://github.com/Microsoft/dotnet-apiport#documentation)和 Channel 9 影片 [Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (.NET Portability Analyzer 簡介)。</span><span class="sxs-lookup"><span data-stu-id="06d1b-136">For more information on the .NET Portability Analyzer, visit the [GitHub documentation](https://github.com/Microsoft/dotnet-apiport#documentation) and [A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9 video.</span></span>

