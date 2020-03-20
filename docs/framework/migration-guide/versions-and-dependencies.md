---
title: .NET 框架& Windows 作業系統版本
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: 486b320ca30323684d301630ad29f8f4615764ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504055"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework 版本和相依性

.NET 框架的每個版本都包含通用語言運行時 （CLR）、基類庫和其他託管庫。 本文介紹了 .NET Framework 的主要功能（按版本），提供有關基礎 CLR 版本和相關開發環境的資訊，並標識 Windows 作業系統 （OS） 安裝的版本。

每個新版本的 .NET Framework 都增加了新功能，但保留了早期版本的功能。

CLR 是透過自己的版本號碼加以識別。 .NET 框架版本號在每個版本中遞增，但 CLR 版本並不總是遞增。 例如，.NET 框架 4、4.5 和更高版本包括 CLR 4，但 .NET 框架 2.0、3.0 和 3.5 包括 CLR 2.0。 (沒有 CLR 版本 3)。

> [!TIP]
>
> - 有關支援的作業系統的完整清單，請參閱[系統要求](../get-started/system-requirements.md)。
> - 如需下載，請參閱[安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)。
> - 有關確定電腦上安裝了 .NET Framework 的哪些版本的資訊，請參閱[如何確定哪些 .NET Framework 版本已安裝](how-to-determine-which-versions-are-installed.md)。

## <a name="version-information"></a>版本資訊

以下表匯總 .NET 框架版本歷程記錄，並將每個版本與視覺化工作室、Windows 和 Windows 伺服器相關聯。 Visual Studio 支援多定位，因此您不僅限於列出的 .NET 框架版本。

- 核取記號圖示✔️表示安裝了 .NET 框架的作業系統版本，但必須在[控制台](../install/dotnet-35-windows-10.md)（用於 Windows）或通過伺服器管理員（用於 Windows 伺服器）中啟用。
- 加號圖示➕表示 OS 版本，其中 .NET Framework 未安裝但可以安裝。

| | |
| - | - |
| [.NET Framework 4.8](#net-framework-48) | [.NET Framework 4.7.2](#net-framework-472) | [.NET Framework 4.7.1](#net-framework-471) | [.NET Framework 4.7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4.6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET 框架 4](#net-framework-4) | [.NET Framework 3.5](#net-framework-35) |
| [.NET Framework 3.0](#net-framework-30) | [.NET Framework 2.0](#net-framework-20) | [.NET Framework 1.1](#net-framework-11) | [.NET Framework 1.0](#net-framework-10) |

### <a name="net-framework-48"></a>.NET Framework 4.8

- [新功能](../whats-new/index.md#whats-new-in-net-framework-48)
- [協助工具的新功能](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**Windows 版本**|✔️ 2019 年 5 月 10 日更新<br/>➕ 2018 年 10 月 10 日更新 （版本 1809）<br/>➕ 2018 年 4 月 10 日更新 （版本 1803）<br/>➕ 10 秋季建立者更新（版本 1709）<br/>➕ 10 個建立者更新（版本 1703）<br/>➕ 10 周年更新（版本 1607）<br/>➕ 8.1<br/>➕7|
|**Windows 伺服器版本**|➕視窗伺服器 2019<br/>➕ Windows 伺服器，版本 1809<br/>➕ Windows 伺服器，版本 1803<br/>2016➕<br/>➕ 2012 R2<br/>2012年➕<br/>➕ 2008 R2 SP1|
|**判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br/>- 528040 (Windows 10 2019 年 5 月更新)<br/>- 528049 (所有其他作業系統版本)<br/>（見[說明](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-472"></a>.NET Framework 4.7.2

- [新功能](../whats-new/index.md#whats-new-in-net-framework-472)
- [協助工具的新功能](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**隨附於 Visual Studio 版本**|2019<sup>1</sup>|
|**Windows 版本**|2018年10月10✔️更新（版本1809）<br/>2018 年 4 月 10 ✔️ 更新（版本 1803）<br/>➕ 10 秋季建立者更新（版本 1709）<br/>➕ 10 個建立者更新（版本 1703）<br/>➕ 10 周年更新（版本 1607）<br/>➕ 8.1<br/>➕7|
|**Windows 伺服器版本**|✔️視窗伺服器 2019<br/>✔️ Windows 伺服器，版本 1809<br/>✔️ Windows 伺服器，版本 1803<br/>➕ Windows 伺服器，版本 1709<br/>2016➕<br/>➕ 2012 R2<br/>2012年➕<br/>➕ 2008 R2 SP1|
|**判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br/>- 461814 (Windows 10 2018 年 10 月更新)<br/>- 461808 (Windows 10 2018 年 4 月更新及 Windows Server，版本 1803)<br/>- 461814 (所有其他作業系統版本)<br/>（見[說明](how-to-determine-which-versions-are-installed.md)）|

<sup>1</sup>需要安裝 **.NET 桌面開發****、ASP.NET和 Web 開發****、Azure 開發****、Office/SharePoint 開發**、使用 **.NET 的移動開發**或 **.NET Core 跨平臺開發**工作負載。

### <a name="net-framework-471"></a>.NET Framework 4.7.1

- [新功能](../whats-new/index.md#whats-new-in-net-framework-471)
- [協助工具的新功能](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**Windows 版本**|✔️ 10 秋季建立者更新（版本 1709）<br/>➕ 10 個建立者更新（版本 1703）<br/>➕ 10 周年更新（版本 1607）<br/>➕ 8.1<br/>➕7|
|**Windows 伺服器版本**|➕ Windows 伺服器，版本 1803<br/>✔️ Windows 伺服器，版本 1709<br/>2016➕<br/>➕ 2012 R2<br/>2012年➕<br/>➕ 2008 R2 SP1|
|**判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br/>- 461308 (Windows 10 Creators Update 及 Windows Server，版本 1709)<br/>- 461310 (所有其他 OS 版本)<br/>（見[說明](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-47"></a>.NET Framework 4.7

- [新功能](../whats-new/index.md#whats-new-in-net-framework-47)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**Windows 版本**|✔️ 10 個建立者更新（版本 1703）<br/>➕ 10 周年更新（版本 1607）<br/>➕ 8.1<br/>➕7|
|**Windows 伺服器版本**|2016➕<br/>➕ 2012 R2<br/>2012年➕<br/>➕ 2008 R2 SP1|
|**判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br/>- 460798 (Windows 10 Creators Update)<br/>- 460805 (所有其他作業系統版本)<br/>（見[說明](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [新功能](../whats-new/index.md#whats-new-in-net-framework-462)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**Windows 版本**|✔️ 10 周年更新（版本 1607）<br/>➕ 11 月 10 日更新（版本 1511）<br/>➕ 10<br/>➕ 8.1<br />➕ 7|
|**Windows 伺服器版本**|2016✔️<br /><br/>➕ 2012 R2<br />2012年➕<br />➕ 2008 R2 SP1|
|**判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br /><br/>- 394802 (Windows 10 年度更新版及 Windows Server 2016)<br/>- 394806 (所有其他作業系統版本)<br /><br/>（見[說明](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [新功能](../whats-new/index.md#whats-new-in-net-framework-461)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**隨附於 Visual Studio 版本**|2017<sup>1</sup>|
|**Windows 版本**|✔️ 11 月 10 日更新（版本 1511）<br/>➕ 10<br />➕ 8.1<br />➕ 8<br />➕ 7|
|**Windows 伺服器版本**|➕ 2012 R2<br />2012年➕<br />➕ 2008 R2 SP1|
|**判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br /><br/>- 394254 (Windows 10 11 月更新)<br />- 394271 (所有其他作業系統版本)<br /><br/>（見[說明](how-to-determine-which-versions-are-installed.md)）|

<sup>1</sup>需要安裝 **.NET 桌面開發****、ASP.NET和 Web 開發****、Azure 開發****、Office/SharePoint 開發**、使用 **.NET 的移動開發**或 **.NET Core 跨平臺開發**工作負載。

### <a name="net-framework-46"></a>.NET Framework 4.6

- [新功能](../whats-new/index.md#whats-new-in-net-2015)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**隨附於 Visual Studio 版本**|2015|
|**Windows 版本**|✔️ 10<br /><br />➕ 8.1<br />➕ 8<br />➕ 7<br />➕維斯塔|
|**Windows 伺服器版本**|➕ 2012 R2<br />2012年➕<br />➕ 2008 R2 SP1<br />2008 ➕ SP2|
|**判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br /><br />- 393295 (Windows 10)<br />- 393297 (所有其他作業系統版本)<br /><br />（見[說明](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [新功能](../whats-new/index.md#whats-new-in-net-framework-452)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**Windows 版本**|➕ 8.1<br />➕ 8<br />➕ 7<br />➕維斯塔|
|**Windows 伺服器版本**|➕ 2012 R2<br />2012年➕<br />➕ 2008 R2 SP1<br />2008 ➕ SP2|
|**判斷已安裝的 .NET 版本**|使用`Release`DWORD 379893<br /><br />（見[說明](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [新功能](../whats-new/index.md#whats-new-in-net-framework-451)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**隨附於 Visual Studio 版本**|2013|
|**Windows 版本**|✔️ 8.1<br /><br />➕ 8<br />➕ 7<br />➕維斯塔|
|**Windows 伺服器版本**|2012 ✔️ R2<br /><br />2012年➕<br />➕ 2008 R2 SP1<br />2008 ➕ SP2|
|**判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br /><br />- 378675 (Windows 8.1)<br />- 378758 (其他所有版本)<br /><br />（見[說明](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [新功能](../whats-new/index.md#whats-new-in-net-framework-45)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**隨附於 Visual Studio 版本**|2012|
|**Windows 版本**|✔️ 8<br />➕ 7<br />➕維斯塔|
|**Windows 伺服器版本**|2012✔️<br />➕ 2008 R2 SP1<br />2008 ➕ SP2|
|**判斷已安裝的 .NET 版本**|使用`Release`DWORD 378389<br /><br />（見[說明](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-4"></a>.NET Framework 4

[新功能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**CLR 版本**|4|
|**隨附於 Visual Studio 版本**|2010|
|**Windows 版本**|➕ 7<br />➕維斯塔|
|**Windows 伺服器版本**|➕ 2008 R2 SP1<br />2008 ➕ SP2<br />2003年➕|
|**判斷已安裝的 .NET 版本**|請參閱[說明](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-35"></a>.NET Framework 3.5

[新功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\))：

- LINQ
- 運算式樹狀架構
- 改進了對AJAX開發ASP.NET支援
- HashSet 集合
- DateTimeOffset
- WCF 和 WF 集成
- 點對點網路
- 擴充性的載入項

|||
|-|-|
|**CLR 版本**|2.0|
|**隨附於 Visual Studio 版本**|2008|
|**Windows 版本**|✔️ 10\*<br/>✔️ 8.1\*<br />✔️ 8\*<br />✔️ 7<br /><br />➕維斯塔|
|**Windows 伺服器版本**|➕ Windows 伺服器，版本 1803\*<br/>➕ Windows 伺服器，版本 1709\*<br/>2016➕\*<br/>➕ 2012 R2\*<br />2012年➕\*<br /><br />✔️2008 R2 SP1\*<br /><br/>2008 ➕ SP2<br />2003年➕|
|**判斷已安裝的 .NET 版本**|請參閱[說明](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-30"></a>.NET Framework 3.0

[新功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90))：

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Windows CardSpace

|||
|-|-|
|**CLR 版本**|2.0|
|**Windows 版本**|✔️維斯塔|
|**Windows 伺服器版本**|✔️ 2008 R2 SP1*<br />✔️ 2008 SP2\*<br /><br />2003年➕|
|**判斷已安裝的 .NET 版本**|請參閱 [指示](how-to-determine-which-versions-are-installed.md)。|

### <a name="net-framework-20"></a>.NET Framework 2.0

[新功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29)：

- 泛型
- 調試器編輯並繼續
- 提高可擴充性和性能
- ClickOnce 部署
- 在 ASP.NET 2.0 中，對各種瀏覽器的新控制項和支援
- 64 位元支援

|||
|-|-|
|**CLR 版本**|2.0|
|**隨附於 Visual Studio 版本**|2005|
|**Windows 版本**|N/A|
|**Windows 伺服器版本**|2008 年 ✔️ R2 SP1<br />✔️ 2008 SP2<br />2003年✔️|
|**判斷已安裝的 .NET 版本**|請參閱[說明](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-11"></a>.NET Framework 1.1

[新功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29)：

- ASP.NET移動控制
- 並存執行
- IPv6 支援

|||
|-|-|
|**CLR 版本**|1.1|
|**隨附於 Visual Studio 版本**|2003|
|**Windows 版本**|N/A|
|**Windows 伺服器版本**|2003年✔️|
|**判斷已安裝的 .NET 版本**|請參閱[說明](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**CLR 版本**|1.0|
|**隨附於 Visual Studio 版本**|Visual Studio .NET|
|**Windows 版本**|N/A|
|**Windows 伺服器版本**|N/A|
|**判斷已安裝的 .NET 版本**|請參閱[說明](how-to-determine-which-versions-are-installed.md)|

> [!NOTE]
>
> - .NET 框架必須通過[控制台（用於 Windows）或伺服器管理員（用於 Windows 伺服器）](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel)在此作業系統上啟用。
> - 通常，不應卸載電腦上安裝的任何版本的 .NET Framework，因為您使用的應用程式可能依賴于特定版本，如果刪除該版本，可能會中斷。 可以同時在一台電腦上載入多個版本的 .NET 框架。 這意味著您可以安裝 .NET 框架，而無需卸載以前的版本。 有關詳細資訊，請參閱[入門](../get-started/index.md)。

## <a name="remarks-for-version-45-and-later"></a>版本 4.5 及更高版本的注釋

.NET Framework 4.5 是替換電腦上的 .NET Framework 4 的就地更新，同樣，.NET Framework 4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 和 4.8 是 .NET Framework 4.5 的就地更新。 就地更新意味著它們使用相同的執行階段版本，但程式集版本會更新並包含新的類型和成員。 安裝其中一個更新之後，您的 .NET Framework 4、.NET Framework 4.5、.NET Framework 4.6 或 .NET Framework 4.7 應用程式會繼續執行，而不需重新編譯。 不過，反向操作則不可行。 我們不建議在早期版本上運行針對更高版本的 .NET Framework 的應用。 例如，我們不建議您在 .NET Framework 4.5 上執行針對 .NET Framework 4.6 的應用程式。

以下是適用的方針：

- 在 Visual Studio 中，您可以選擇 .NET Framework 4.5 作為專案的目標 Framework (這會設定 <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> 屬性)，將專案編譯為 .NET Framework 4.5 的組件或可執行檔。 此組件或可執行檔可用於任何已安裝 .NET Framework 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或 4.8 的電腦。

- 在 Visual Studio 中，您可以選擇 .NET 框架 4.5.1 作為專案的目標框架，將其編譯為 .NET 框架 4.5.1 程式集或可執行檔。 僅在安裝了 .NET Framework 4.5.1 或更高版本的電腦上運行此程式集或可執行檔。 目標 .NET Framework 4.5.1 的可執行檔將阻止在僅安裝早期版本的 .NET Framework（如 .NET Framework 4.5）的電腦上運行。 系統將提示使用者安裝 .NET 框架 4.5.1。 此外，不應從針對早期版本的 .NET Framework 的應用（如 .NET Framework 4.5）調用 .NET Framework 4.5.1 程式集。

  > [!NOTE]
  > .NET framework 4.5.1 及 .NET Framework 4.5 在此處僅用於示範。 所述原則適用于針對 .NET Framework 更高版本的任何應用，而不是安裝在其運行系統上的應用。

.NET 框架中的某些更改可能需要更改應用代碼;但是，如果更改了 .NET 框架，請更改您的應用代碼。在使用 .NET Framework 4.5 或更高版本運行現有應用之前，請參閱[應用程式相容性](application-compatibility.md)。 如需安裝目前版本的詳細資訊，請參閱[安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)。 有關 .NET 框架支援的資訊，請參閱[.NET 網站上的 .NET 框架官方支援政策](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)。

## <a name="remarks-for-older-versions"></a>舊版本的備註

.NET Framework 版本 2.0、3.0 和 3.5 使用相同版本的 CLR (CLR 2.0) 建置。 這些版本代表單一安裝的連續執行層。 每個版本都是以累加方式建置於舊版之上。 不可能在電腦上並行運行版本 2.0、3.0 和 3.5。 當您安裝 3.5 版時，會自動取得 2.0 和 3.0 執行層，而針對 2.0、3.0 和 3.5 版所建置的應用程式全都可以在 3.5 版上執行。 不過，.NET Framework 4 結束此分層方法，且該版本和更新版本 (.NET Framework 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 和 4.8) 也代表單一安裝的連續層。 從 .NET 框架 4 開始，可以使用進程內並排託管在單個進程中運行多個版本的 CLR。 如需詳細資訊，請參閱[組件和並存執行](../../standard/assembly/side-by-side-execution.md)。

此外，如果應用以版本 2.0、3.0 或 3.5 為目標，則使用者可能需要在 Windows 8、Windows 8.1 或 Windows 10 電腦上啟用 .NET 框架 3.5，然後才能運行你的應用。 如需詳細資訊，請參閱[在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5](../install/dotnet-35-windows-10.md)。

## <a name="next-steps"></a>後續步驟

- 如果您還不熟悉 .NET Framework，請參閱[概觀](../get-started/overview.md)中有關重要概念和功能的簡介。

- 有關 .NET 框架 4.5 及其點版本中的新功能和改進，請參閱[.NET 框架中的新增功能](../whats-new/index.md)。

- 有關將應用遷移到較新版本 .NET Framework 的資訊，請參閱[遷移指南](index.md)。

- 如需判斷電腦上已安裝哪些版本或更新的資訊，請參閱 [如何：判斷安裝的 .NET Framework 版本](how-to-determine-which-versions-are-installed.md)和[如何：判斷安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。

## <a name="see-also"></a>另請參閱

- [版本相容性](version-compatibility.md)
| [.NET 框架官方支援策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](../install/troubleshoot-blocked-installations-and-uninstallations.md)
