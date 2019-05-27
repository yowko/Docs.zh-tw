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
# <a name="the-net-portability-analyzer"></a>.NET Portability Analyzer

要將您的程式庫變成多平台？ 想要查看需要多少工作，才能讓您的應用程式相容於其他 .NET 實作和設定檔 (包括 .NET Core、.NET Standard、UWP 和適用於 iOS、Android 和 Mac 的 Xamarin) 嗎？ [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) 是一項工具，其藉由分析組件來提供您有關程式在跨 .NET 實作上之彈性的詳細報表。 Portability Analyzer 會以 Visual Studio 擴充功能和主控台應用程式的形式提供給您。

## <a name="new-targets"></a>新目標

* [.NET Core](../../core/index.md)：具有模組化的設計，採用並存，並且適合在跨平台的情況下使用。 並存可讓您採用新的 .NET Core 版本，而不會中斷其他應用程式。
* [ASP.NET Core](/aspnet/core)︰是建置於 .NET Core 上的現代 Web 架構，因此提供開發人員相同的優點。
* [通用 Windows 平](/uwp)：改善某些 Windows 市集應用程式的效能，這些應用程式在 x64 和 ARM 電腦上使用 .NET Native 的靜態編譯來執行。 
* .NET Core + 平台延伸模組：包含 .NET Core API，以及 .NET 生態系統中的其他 API，例如 WCF、ASP.NET Core、FSharp 和 Azure。
* .NET Standard + 平台延伸模組：包含 .NET Standard API，以及 .NET 生態系統中的其他 API，例如 WCF、ASP.NET Core、FSharp 和 Azure。

## <a name="how-to-use-the-portability-analyzer"></a>如何使用可攜性分析器

若要開始使用.NET Portability Analyzer，必須從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) 下載及安裝此延伸模組。 它適用於 Visual Studio 2017 和更新版本。 您可以在 Visual Studio 中，使用 [分析] > [Portability Analyzer Settings] (Portability Analyzer 設定) 設定此工具，然後選取您的目標平台。

![可攜性螢幕擷取畫面](./media/portability-analyzer/portability-screenshot.png)

若要分析整個專案，在方案總管中以滑鼠右鍵按一下您的專案，然後選取 [Analyze Assembly Portability] (分析組件可攜性)。 否則，請移至 [分析] 功能表，然後選取 [Analyze Assembly Portability] (分析組件可攜性)。 從這裡選取專案的可執行檔或 DLL。

![[方案總管] 中的可攜性分析器](./media/portability-analyzer/portability-solution-explorer.png)

執行分析之後，您會看到 .NET 可攜性報表。 僅有目標平台不支援的類型才會顯示在清單中，您可以在 [錯誤清單] 的 [訊息] 索引標籤中檢閱建議。 您也可以直接從 [訊息] 索引標籤跳到有問題的地方。

![可攜性報表](./media/portability-analyzer/portability-report.png)

如果您不想使用 Visual Studio，您可以從命令提示字元使用可攜性分析器。 只要從 [Microsoft/dotnet-apiport](https://github.com/Microsoft/dotnet-apiport/releases) 存放庫下載 API 可攜性分析器。

* 輸入下列命令分析目前的目錄︰`\...\ApiPort.exe analyze -f .`
* 若要分析特定的 .dll 檔案清單，請輸入下列命令︰`\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

您的 .NET Portability 報表會以 Excel 檔案 ( *.xlsx*) 格式儲存在您目前目錄中。 Excel 活頁簿中的 [詳細資料] 索引標籤會包含更多的資訊。

如需 .NET Portability Analyzer 的詳細資訊，請瀏覽 [GitHub 文件](https://github.com/Microsoft/dotnet-apiport#documentation)和 Channel 9 影片 [Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (.NET Portability Analyzer 簡介)。
