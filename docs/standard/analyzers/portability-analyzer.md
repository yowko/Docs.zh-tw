---
title: .NET Portability Analyzer - .NET
description: 了解如何使用.NET Portability Analyzer 工具來評估程式碼移植到不同 .NET 實作之間的可行性，包括 .NET Core、.NET Standard、UWP 和 Xamarin。
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 7de6aa72b2d30c3e54d2ddf9a2d951688571d654
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063414"
---
# <a name="the-net-portability-analyzer"></a><span data-ttu-id="e45fb-103">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="e45fb-103">The .NET Portability Analyzer</span></span>

<span data-ttu-id="e45fb-104">要將您的程式庫變成多平台？</span><span class="sxs-lookup"><span data-stu-id="e45fb-104">Want to make your libraries multi-platform?</span></span> <span data-ttu-id="e45fb-105">想要查看需要多少工作，才能讓您的應用程式相容於其他 .NET 實作和設定檔 (包括 .NET Core、.NET Standard、UWP 和適用於 iOS、Android 和 Mac 的 Xamarin) 嗎？</span><span class="sxs-lookup"><span data-stu-id="e45fb-105">Want to see how much work is required to make your application compatible with other .NET implementations and profiles, including .NET Core, .NET Standard, UWP, and Xamarin for iOS, Android, and Mac?</span></span> <span data-ttu-id="e45fb-106">[.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) 是一項工具，其藉由分析組件來提供您有關程式在跨 .NET 實作上之彈性的詳細報表。</span><span class="sxs-lookup"><span data-stu-id="e45fb-106">The [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) is a tool that provides you with a detailed report on how flexible your program is across .NET implementations by analyzing assemblies.</span></span> <span data-ttu-id="e45fb-107">Portability Analyzer 會以 Visual Studio 擴充功能和主控台應用程式的形式提供給您。</span><span class="sxs-lookup"><span data-stu-id="e45fb-107">The Portability Analyzer is offered as a Visual Studio Extension and as a console app.</span></span>

## <a name="new-targets"></a><span data-ttu-id="e45fb-108">新目標</span><span class="sxs-lookup"><span data-stu-id="e45fb-108">New targets</span></span>

* <span data-ttu-id="e45fb-109">[.NET Core](../../core/index.md)：具有模組化的設計，採用並存，並且適合在跨平台的情況下使用。</span><span class="sxs-lookup"><span data-stu-id="e45fb-109">[.NET Core](../../core/index.md): Has a modular design, employs side-by-side, and targets cross-platform scenarios.</span></span> <span data-ttu-id="e45fb-110">並存可讓您採用新的 .NET Core 版本，而不會中斷其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="e45fb-110">Side-by-side allows you to adopt new .NET Core versions without breaking other apps.</span></span>
* <span data-ttu-id="e45fb-111">[ASP.NET Core](/aspnet/core)︰是建置於 .NET Core 上的現代 Web 架構，因此提供開發人員相同的優點。</span><span class="sxs-lookup"><span data-stu-id="e45fb-111">[ASP.NET Core](/aspnet/core): is a modern web-framework built on .NET Core thus giving developers the same benefits.</span></span>
* <span data-ttu-id="e45fb-112">[通用 Windows 平](/uwp)：改善某些 Windows 市集應用程式的效能，這些應用程式在 x64 和 ARM 電腦上使用 .NET Native 的靜態編譯來執行。</span><span class="sxs-lookup"><span data-stu-id="e45fb-112">[Universal Windows Platform](/uwp): Improve performance of your Windows Store apps that run on x64 and ARM machines by using .NET Native’s static compilation.</span></span> 
* <span data-ttu-id="e45fb-113">.NET Core + 平台延伸模組：包含 .NET Core API，以及 .NET 生態系統中的其他 API，例如 WCF、ASP.NET Core、FSharp 和 Azure。</span><span class="sxs-lookup"><span data-stu-id="e45fb-113">.NET Core + Platform Extensions: Includes the .NET Core APIs in addition to other APIs in the .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>
* <span data-ttu-id="e45fb-114">.NET Standard + 平台延伸模組：包含 .NET Standard API，以及 .NET 生態系統中的其他 API，例如 WCF、ASP.NET Core、FSharp 和 Azure。</span><span class="sxs-lookup"><span data-stu-id="e45fb-114">.NET Standard + Platform Extensions: Includes the .NET Standard APIs in addition to other .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>

## <a name="how-to-use-the-portability-analyzer"></a><span data-ttu-id="e45fb-115">如何使用可攜性分析器</span><span class="sxs-lookup"><span data-stu-id="e45fb-115">How to use the Portability Analyzer</span></span>

<span data-ttu-id="e45fb-116">若要開始使用.NET Portability Analyzer，必須從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) 下載及安裝此延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e45fb-116">To begin using the .NET Portability Analyzer, you first need to download and install the extension from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span> <span data-ttu-id="e45fb-117">它適用於 Visual Studio 2017 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="e45fb-117">It works on Visual Studio 2017 and later versions.</span></span> <span data-ttu-id="e45fb-118">您可以在 Visual Studio 中，使用 [分析] > [Portability Analyzer Settings] (Portability Analyzer 設定) 設定此工具，然後選取您的目標平台。</span><span class="sxs-lookup"><span data-stu-id="e45fb-118">You can configure it in Visual Studio via **Analyze** > **Portability Analyzer Settings** and select your Target Platforms.</span></span>

![可攜性螢幕擷取畫面](./media/portability-analyzer/portability-screenshot.png)

<span data-ttu-id="e45fb-120">若要分析整個專案，在方案總管中以滑鼠右鍵按一下您的專案，然後選取 [Analyze Assembly Portability] (分析組件可攜性)。</span><span class="sxs-lookup"><span data-stu-id="e45fb-120">To analyze your entire project, right-click on your project in **Solution Explorer** and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="e45fb-121">否則，請移至 [分析] 功能表，然後選取 [Analyze Assembly Portability] (分析組件可攜性)。</span><span class="sxs-lookup"><span data-stu-id="e45fb-121">Otherwise, go to the **Analyze** menu and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="e45fb-122">從這裡選取專案的可執行檔或 DLL。</span><span class="sxs-lookup"><span data-stu-id="e45fb-122">From there, select your project’s executable or DLL.</span></span>

![[方案總管] 中的可攜性分析器](./media/portability-analyzer/portability-solution-explorer.png)

<span data-ttu-id="e45fb-124">執行分析之後，您會看到 .NET 可攜性報表。</span><span class="sxs-lookup"><span data-stu-id="e45fb-124">After running the analysis, you'll see your .NET Portability Report.</span></span> <span data-ttu-id="e45fb-125">僅有目標平台不支援的類型才會顯示在清單中，您可以在 [錯誤清單] 的 [訊息] 索引標籤中檢閱建議。</span><span class="sxs-lookup"><span data-stu-id="e45fb-125">Only types that are unsupported by a target platform appear in the list and you can review recommendations in the **Messages** tab in the **Error List**.</span></span> <span data-ttu-id="e45fb-126">您也可以直接從 [訊息] 索引標籤跳到有問題的地方。</span><span class="sxs-lookup"><span data-stu-id="e45fb-126">You can also jump to problem areas directly from the **Messages** tab.</span></span>

![可攜性報表](./media/portability-analyzer/portability-report.png)

<span data-ttu-id="e45fb-128">如果您不想使用 Visual Studio，您可以從命令提示字元使用可攜性分析器。</span><span class="sxs-lookup"><span data-stu-id="e45fb-128">If you don’t want to use Visual Studio, you can use the Portability Analyzer from the command prompt.</span></span> <span data-ttu-id="e45fb-129">只要從 [Microsoft/dotnet-apiport](https://github.com/Microsoft/dotnet-apiport/releases) 存放庫下載 API 可攜性分析器。</span><span class="sxs-lookup"><span data-stu-id="e45fb-129">Just download the API Portability Analyzer from the [Microsoft/dotnet-apiport](https://github.com/Microsoft/dotnet-apiport/releases) repository.</span></span>

* <span data-ttu-id="e45fb-130">輸入下列命令分析目前的目錄︰`\...\ApiPort.exe analyze -f .`</span><span class="sxs-lookup"><span data-stu-id="e45fb-130">Type the following command to analyze the current directory: `\...\ApiPort.exe analyze -f .`</span></span>
* <span data-ttu-id="e45fb-131">若要分析特定的 .dll 檔案清單，請輸入下列命令︰`\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span><span class="sxs-lookup"><span data-stu-id="e45fb-131">To analyze a specific list of .dll files, type the following command: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span></span>

<span data-ttu-id="e45fb-132">您的 .NET Portability 報表會以 Excel 檔案 ( *.xlsx*) 格式儲存在您目前目錄中。</span><span class="sxs-lookup"><span data-stu-id="e45fb-132">Your .NET Portability Report is saved as an Excel file (*.xlsx*) in your current directory.</span></span> <span data-ttu-id="e45fb-133">Excel 活頁簿中的 [詳細資料] 索引標籤會包含更多的資訊。</span><span class="sxs-lookup"><span data-stu-id="e45fb-133">The **Details** tab in the Excel Workbook contains more information.</span></span>

<span data-ttu-id="e45fb-134">如需 .NET Portability Analyzer 的詳細資訊，請瀏覽 [GitHub 文件](https://github.com/Microsoft/dotnet-apiport#documentation)和 Channel 9 影片 [Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (.NET Portability Analyzer 簡介)。</span><span class="sxs-lookup"><span data-stu-id="e45fb-134">For more information on the .NET Portability Analyzer, visit the [GitHub documentation](https://github.com/Microsoft/dotnet-apiport#documentation) and [A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9 video.</span></span>
