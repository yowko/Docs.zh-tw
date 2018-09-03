---
title: .NET Portability Analyzer - .NET
description: 了解如何使用.NET Portability Analyzer 工具來評估程式碼移植到不同 .NET 實作之間的可行性，包括 .NET Core、.NET Standard、UWP 和 Xamarin。
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 515dd7a393d87811377aa5d9fb02de35943b6966
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43415684"
---
# <a name="the-net-portability-analyzer"></a><span data-ttu-id="f828c-103">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="f828c-103">The .NET Portability Analyzer</span></span>

<span data-ttu-id="f828c-104">要將您的程式庫變成多平台？</span><span class="sxs-lookup"><span data-stu-id="f828c-104">Want to make your libraries multi-platform?</span></span> <span data-ttu-id="f828c-105">想要查看需要多少工作，才能讓您的應用程式相容於其他 .NET 實作和設定檔 (包括 .NET Core、.NET Standard、UWP 和適用於 iOS、Android 和 Mac 的 Xamarin) 嗎？</span><span class="sxs-lookup"><span data-stu-id="f828c-105">Want to see how much work is required to make your application compatible with other .NET implementations and profiles, including .NET Core, .NET Standard, UWP, and Xamarin for iOS, Android, and Mac?</span></span> <span data-ttu-id="f828c-106">[.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) 是一項工具，其藉由分析組件來提供您有關程式在跨 .NET 實作上之彈性的詳細報表。</span><span class="sxs-lookup"><span data-stu-id="f828c-106">The [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) is a tool that provides you with a detailed report on how flexible your program is across .NET implementations by analyzing assemblies.</span></span> <span data-ttu-id="f828c-107">Portability Analyzer 會以 Visual Studio 擴充功能和主控台應用程式的形式提供給您。</span><span class="sxs-lookup"><span data-stu-id="f828c-107">The Portability Analyzer is offered as a Visual Studio Extension and as a console app.</span></span>

## <a name="new-targets"></a><span data-ttu-id="f828c-108">新目標</span><span class="sxs-lookup"><span data-stu-id="f828c-108">New targets</span></span>

* <span data-ttu-id="f828c-109">[.NET core](../../core/index.md)︰具有模組化的設計，採用並存，並且適合在跨平台的情況下使用。</span><span class="sxs-lookup"><span data-stu-id="f828c-109">[.NET Core](../../core/index.md): Has a modular design, employs side-by-side, and targets cross-platform scenarios.</span></span> <span data-ttu-id="f828c-110">並存可讓您採用新的 .NET Core 版本，而不會中斷其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="f828c-110">Side-by-side allows you to adopt new .NET Core versions without breaking other apps.</span></span>
* <span data-ttu-id="f828c-111">[ASP.NET Core](/aspnet/core)︰是建置於 .NET Core 上的現代 Web 架構，因此提供開發人員相同的優點。</span><span class="sxs-lookup"><span data-stu-id="f828c-111">[ASP.NET Core](/aspnet/core): is a modern web-framework built on .NET Core thus giving developers the same benefits.</span></span>
* <span data-ttu-id="f828c-112">[通用 Windows 平台](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance)︰改善 Windows 市集應用程式的效能，這些應用程式在 x64 和 ARM 電腦上使用 .NET Native 的靜態編譯來執行。</span><span class="sxs-lookup"><span data-stu-id="f828c-112">[Universal Windows Platform](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): Improve performance of your Windows Store apps that run on x64 and ARM machines by using .NET Native’s static compilation.</span></span> 
* <span data-ttu-id="f828c-113">.NET Core + 平台延伸模組：包含 .NET Core API，以及 .NET 生態系統中的其他 API，例如 WCF、ASP.NET Core、FSharp 和 Azure。</span><span class="sxs-lookup"><span data-stu-id="f828c-113">.NET Core + Platform Extensions: Includes the .NET Core APIs in addition to other APIs in the .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>
* <span data-ttu-id="f828c-114">.NET Standard + 平台延伸模組：包含 .NET Standard API，以及其他 .NET 生態系統，例如 WCF、ASP.NET Core、FSharp 和 Azure。</span><span class="sxs-lookup"><span data-stu-id="f828c-114">.NET Standard + Platform Extensions: Includes the .NET Standard APIs in addition to other .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>

## <a name="how-to-use-portability-analyzer"></a><span data-ttu-id="f828c-115">如何使用 Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="f828c-115">How to use Portability Analyzer</span></span>

<span data-ttu-id="f828c-116">若要開始使用.NET Portability Analyzer，必須從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) 下載及安裝此延伸模組。</span><span class="sxs-lookup"><span data-stu-id="f828c-116">To begin using the .NET Portability Analyzer, you first need to download and install the extension from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span> <span data-ttu-id="f828c-117">它適用於 Visual Studio 2015 和 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="f828c-117">It works on Visual Studio 2015 and Visual Studio 2017.</span></span> <span data-ttu-id="f828c-118">您可以在 Visual Studio 中，使用 [分析] > [Portability Analyzer Settings] (Portability Analyzer 設定) 設定此工具，然後選取您的目標平台。</span><span class="sxs-lookup"><span data-stu-id="f828c-118">You can configure it in Visual Studio via **Analyze** > **Portability Analyzer Settings** and select your Target Platforms.</span></span>

![可攜性螢幕擷取畫面](./media/portability-analyzer/portability-screenshot.png)

<span data-ttu-id="f828c-120">若要分析整個專案，在方案總管中以滑鼠右鍵按一下您的專案，然後選取 [Analyze Assembly Portability] (分析組件可攜性)。</span><span class="sxs-lookup"><span data-stu-id="f828c-120">To analyze your entire project, right-click on your project in **Solution Explorer** and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="f828c-121">否則，請移至 [分析] 功能表，然後選取 [Analyze Assembly Portability] (分析組件可攜性)。</span><span class="sxs-lookup"><span data-stu-id="f828c-121">Otherwise, go to the **Analyze** menu and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="f828c-122">從這裡選取專案的可執行檔或 DLL。</span><span class="sxs-lookup"><span data-stu-id="f828c-122">From there, select your project’s executable or DLL.</span></span>

![可攜性方案總管](./media/portability-analyzer/portability-solution-explorer.png)

<span data-ttu-id="f828c-124">執行分析之後，您會看到 .NET Portability 的報表。</span><span class="sxs-lookup"><span data-stu-id="f828c-124">After running the analysis, you will see your .NET Portability Report.</span></span> <span data-ttu-id="f828c-125">僅有目標平台不支援的類型才會顯示在清單中，您可以在 [錯誤清單] 的 [訊息] 索引標籤中檢閱建議。</span><span class="sxs-lookup"><span data-stu-id="f828c-125">Only types that are unsupported by a target platform appear in the list and you can review recommendations in the **Messages** tab in the **Error List**.</span></span> <span data-ttu-id="f828c-126">您也可以直接從 [訊息] 索引標籤跳到有問題的地方。</span><span class="sxs-lookup"><span data-stu-id="f828c-126">You can also jump to problem areas directly from the **Messages** tab.</span></span>

![可攜性報表](./media/portability-analyzer/portability-report.png)

<span data-ttu-id="f828c-128">不想使用 Visual Studio？</span><span class="sxs-lookup"><span data-stu-id="f828c-128">Don’t want to use Visual Studio?</span></span> <span data-ttu-id="f828c-129">您也可以從命令提示字元使用 Portability Analyzer。</span><span class="sxs-lookup"><span data-stu-id="f828c-129">You can also use the Portability Analyzer from the command prompt.</span></span> <span data-ttu-id="f828c-130">下載 [API Portability Analyzer](https://www.microsoft.com/download/details.aspx?id=42678)。</span><span class="sxs-lookup"><span data-stu-id="f828c-130">Just download the [API Portability Analyzer](https://www.microsoft.com/download/details.aspx?id=42678).</span></span>

*   <span data-ttu-id="f828c-131">輸入下列命令分析目前的目錄︰`\...\ApiPort.exe analyze -f .`</span><span class="sxs-lookup"><span data-stu-id="f828c-131">Type the following command to analyze the current directory: `\...\ApiPort.exe analyze -f .`</span></span>
*   <span data-ttu-id="f828c-132">若要分析特定的 .dll 檔案清單，請輸入下列命令︰`\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span><span class="sxs-lookup"><span data-stu-id="f828c-132">To analyze a specific list of .dll files, type the following command: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span></span>

<span data-ttu-id="f828c-133">您的 .NET Portability 報表會以 Excel 檔案 (*.xlsx*) 格式儲存在您目前目錄中。</span><span class="sxs-lookup"><span data-stu-id="f828c-133">Your .NET Portability Report is saved as an Excel file (*.xlsx*) in your current directory.</span></span> <span data-ttu-id="f828c-134">Excel 活頁簿中的 [詳細資料] 索引標籤會包含更多的資訊。</span><span class="sxs-lookup"><span data-stu-id="f828c-134">The **Details** tab in the Excel Workbook contains more information.</span></span>

<span data-ttu-id="f828c-135">如需 .NET Portability Analyzer 的詳細資訊，請瀏覽 [GitHub 文件](https://github.com/Microsoft/dotnet-apiport#documentation)和 Channel 9 影片 [Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (.NET Portability Analyzer 簡介)。</span><span class="sxs-lookup"><span data-stu-id="f828c-135">For more information on the .NET Portability Analyzer, visit the [GitHub documentation](https://github.com/Microsoft/dotnet-apiport#documentation) and [A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9 video.</span></span>
