---
title: .NET Framework & Windows 作業系統版本
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: 486b320ca30323684d301630ad29f8f4615764ee
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504055"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework 版本和相依性

.NET Framework 的每個版本都包含 common language runtime （CLR）、基類庫和其他 managed 程式庫。 本文說明依版本 .NET Framework 的主要功能、提供有關基礎 CLR 版本和相關聯開發環境的資訊，以及識別 Windows 作業系統（OS）所安裝的版本。

.NET Framework 的每個新版本都會新增新功能，但會保留舊版的功能。

CLR 是透過自己的版本號碼加以識別。 每次發行時，.NET Framework 版本號碼都會遞增，但是 CLR 版本不一定會遞增。 例如，.NET Framework 4、4.5 和更新版本包含 CLR 4，但 .NET Framework 2.0、3.0 和3.5 包含 CLR 2.0。 (沒有 CLR 版本 3)。

> [!TIP]
>
> - 如需所支援作業系統的完整清單，請參閱[系統需求](../get-started/system-requirements.md)。
> - 如需下載，請參閱[安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)。
> - 如需判斷電腦上已安裝哪些 .NET Framework 版本的相關資訊，請參閱[如何判斷安裝的 .NET Framework 版本](how-to-determine-which-versions-are-installed.md)。

## <a name="version-information"></a>版本資訊

下表摘要說明 .NET Framework 版本歷程記錄，並將每個版本與 Visual Studio、Windows 和 Windows Server 相互關聯。 Visual Studio 支援多目標，因此您不限於列出的 .NET Framework 版本。

- 核取記號圖示✔️代表安裝 .NET Framework 的作業系統版本，但必須[在控制台中](../install/dotnet-35-windows-10.md)啟用（適用于 windows）或透過伺服器管理員（適用于 windows Server）。
- 加號圖示➕表示未安裝 .NET Framework 但可以安裝的作業系統版本。

| | |
| - | - |
| [.NET Framework 4.8](#net-framework-48) | [.NET Framework 4.7.2](#net-framework-472) | [.NET Framework 4.7.1](#net-framework-471) | [.NET Framework 4.7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4.6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET Framework 4](#net-framework-4) | [.NET Framework 3.5](#net-framework-35) |
| [.NET Framework 3。0](#net-framework-30) | [.NET Framework 2。0](#net-framework-20) | [.NET Framework 1。1](#net-framework-11) | [.NET Framework 1。0](#net-framework-10) |

### <a name="net-framework-48"></a>.NET Framework 4.8

- [新功能](../whats-new/index.md#whats-new-in-net-framework-48)
- [協助工具的新功能](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**Windows 版本**|✔️ 10 5 月2019更新<br/>➕ 10 2018 年10月更新（版本1809）<br/>➕2018年4月更新（版本1803）<br/>➕10秋季建立者更新（版本1709）<br/>➕10建立者更新（版本1703）<br/>➕10周年更新（版本1607）<br/>➕8。1<br/>➕7|
|**Windows Server 版本**|➕ Windows Server 2019<br/>➕ Windows Server，版本1809<br/>➕ Windows Server，版本1803<br/>➕2016<br/>➕ 2012 R2<br/>➕2012<br/>➕ 2008 R2 SP1|
|**若要判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br/>- 528040 (Windows 10 2019 年 5 月更新)<br/>- 528049 (所有其他作業系統版本)<br/>（請參閱[指示](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-472"></a>.NET Framework 4.7.2

- [新功能](../whats-new/index.md#whats-new-in-net-framework-472)
- [協助工具的新功能](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**包含在 Visual Studio 版本中**|2019<sup>1</sup>|
|**Windows 版本**|✔️ 10 2018 年10月更新（版本1809）<br/>✔️2018年4月更新（版本1803）<br/>➕10秋季建立者更新（版本1709）<br/>➕10建立者更新（版本1703）<br/>➕10周年更新（版本1607）<br/>➕8。1<br/>➕7|
|**Windows Server 版本**|✔️ Windows Server 2019<br/>✔️ Windows Server，版本1809<br/>✔️ Windows Server，版本1803<br/>➕ Windows Server，版本1709<br/>➕2016<br/>➕ 2012 R2<br/>➕2012<br/>➕ 2008 R2 SP1|
|**若要判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br/>- 461814 (Windows 10 2018 年 10 月更新)<br/>- 461808 (Windows 10 2018 年 4 月更新及 Windows Server，版本 1803)<br/>- 461814 (所有其他作業系統版本)<br/>（請參閱[指示](how-to-determine-which-versions-are-installed.md)）|

<sup>1</sup>需要安裝 **.net 桌面開發**、 **ASP.NET 和網頁開發**、 **Azure 開發**、 **Office/SharePoint 開發**、**使用 .net 的**行動裝置開發，或 **.net Core 跨平臺開發**工作負載。

### <a name="net-framework-471"></a>.NET Framework 4.7.1

- [新功能](../whats-new/index.md#whats-new-in-net-framework-471)
- [協助工具的新功能](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**Windows 版本**|✔️10秋季建立者更新（版本1709）<br/>➕10建立者更新（版本1703）<br/>➕10周年更新（版本1607）<br/>➕8。1<br/>➕7|
|**Windows Server 版本**|➕ Windows Server，版本1803<br/>✔️ Windows Server，版本1709<br/>➕2016<br/>➕ 2012 R2<br/>➕2012<br/>➕ 2008 R2 SP1|
|**若要判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br/>- 461308 (Windows 10 Creators Update 及 Windows Server，版本 1709)<br/>- 461310 (所有其他 OS 版本)<br/>（請參閱[指示](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-47"></a>.NET Framework 4.7

- [新功能](../whats-new/index.md#whats-new-in-net-framework-47)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**Windows 版本**|✔️10建立者更新（版本1703）<br/>➕10周年更新（版本1607）<br/>➕8。1<br/>➕7|
|**Windows Server 版本**|➕2016<br/>➕ 2012 R2<br/>➕2012<br/>➕ 2008 R2 SP1|
|**若要判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br/>- 460798 (Windows 10 Creators Update)<br/>- 460805 (所有其他作業系統版本)<br/>（請參閱[指示](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [新功能](../whats-new/index.md#whats-new-in-net-framework-462)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**Windows 版本**|✔️10周年更新（版本1607）<br/>➕10年11月更新（版本1511）<br/>➕10<br/>➕8。1<br />➕7|
|**Windows Server 版本**|✔️2016<br /><br/>➕ 2012 R2<br />➕2012<br />➕ 2008 R2 SP1|
|**若要判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br /><br/>- 394802 (Windows 10 年度更新版及 Windows Server 2016)<br/>- 394806 (所有其他作業系統版本)<br /><br/>（請參閱[指示](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [新功能](../whats-new/index.md#whats-new-in-net-framework-461)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**包含在 Visual Studio 版本中**|2017<sup>1</sup>|
|**Windows 版本**|✔️10年11月更新（版本1511）<br/>➕10<br />➕8。1<br />➕8<br />➕7|
|**Windows Server 版本**|➕ 2012 R2<br />➕2012<br />➕ 2008 R2 SP1|
|**若要判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br /><br/>- 394254 (Windows 10 11 月更新)<br />- 394271 (所有其他作業系統版本)<br /><br/>（請參閱[指示](how-to-determine-which-versions-are-installed.md)）|

<sup>1</sup>需要安裝 **.net 桌面開發**、 **ASP.NET 和網頁開發**、 **Azure 開發**、 **Office/SharePoint 開發**、**使用 .net 的**行動裝置開發，或 **.net Core 跨平臺開發**工作負載。

### <a name="net-framework-46"></a>.NET Framework 4.6

- [新功能](../whats-new/index.md#whats-new-in-net-2015)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**包含在 Visual Studio 版本中**|2015|
|**Windows 版本**|✔️10<br /><br />➕8。1<br />➕8<br />➕7<br />➕ Vista|
|**Windows Server 版本**|➕ 2012 R2<br />➕2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**若要判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br /><br />- 393295 (Windows 10)<br />- 393297 (所有其他作業系統版本)<br /><br />（請參閱[指示](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [新功能](../whats-new/index.md#whats-new-in-net-framework-452)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**Windows 版本**|➕8。1<br />➕8<br />➕7<br />➕ Vista|
|**Windows Server 版本**|➕ 2012 R2<br />➕2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**若要判斷已安裝的 .NET 版本**|使用 `Release` DWORD 379893<br /><br />（請參閱[指示](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [新功能](../whats-new/index.md#whats-new-in-net-framework-451)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**包含在 Visual Studio 版本中**|2013|
|**Windows 版本**|✔️8。1<br /><br />➕8<br />➕7<br />➕ Vista|
|**Windows Server 版本**|✔️ 2012 R2<br /><br />➕2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**若要判斷已安裝的 .NET 版本**|使用 `Release` DWORD：<br /><br />- 378675 (Windows 8.1)<br />- 378758 (其他所有版本)<br /><br />（請參閱[指示](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [新功能](../whats-new/index.md#whats-new-in-net-framework-45)
- [版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**CLR 版本**|4|
|**包含在 Visual Studio 版本中**|2012|
|**Windows 版本**|✔️8<br />➕7<br />➕ Vista|
|**Windows Server 版本**|✔️2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**若要判斷已安裝的 .NET 版本**|使用 `Release` DWORD 378389<br /><br />（請參閱[指示](how-to-determine-which-versions-are-installed.md)）|

### <a name="net-framework-4"></a>.NET Framework 4

[新功能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**CLR 版本**|4|
|**包含在 Visual Studio 版本中**|2010|
|**Windows 版本**|➕7<br />➕ Vista|
|**Windows Server 版本**|➕ 2008 R2 SP1<br />➕ 2008 SP2<br />➕2003|
|**若要判斷已安裝的 .NET 版本**|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-35"></a>.NET Framework 3.5

[新功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\))：

- LINQ
- 運算式樹狀架構
- 改善 AJAX 開發的 ASP.NET 支援
- HashSet 集合
- DateTimeOffset
- WCF 和 WF 整合
- 對等網路
- 擴充性的增益集

|||
|-|-|
|**CLR 版本**|2.0|
|**包含在 Visual Studio 版本中**|2008|
|**Windows 版本**|✔️ 10\*<br/>✔️ 8.1\*<br />✔️ 8\*<br />✔️7<br /><br />➕ Vista|
|**Windows Server 版本**|➕ Windows Server，版本 1803\*<br/>➕ Windows Server，版本 1709\*<br/>➕ 2016\*<br/>➕ 2012 R2\*<br />➕ 2012\*<br /><br />✔️ 2008 R2 SP1\*<br /><br/>➕ 2008 SP2<br />➕2003|
|**若要判斷已安裝的 .NET 版本**|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-30"></a>.NET Framework 3.0

[新功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90))：

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Windows CardSpace

|||
|-|-|
|**CLR 版本**|2.0|
|**Windows 版本**|✔️ Vista|
|**Windows Server 版本**|✔️ 2008 R2 SP1 *<br />✔️ 2008 SP2\*<br /><br />➕2003|
|**若要判斷已安裝的 .NET 版本**|請參閱 [指示](how-to-determine-which-versions-are-installed.md)。|

### <a name="net-framework-20"></a>.NET Framework 2.0

[新功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29)：

- 泛型
- 偵錯工具編輯後繼續
- 改良的擴充性和效能
- ClickOnce 部署
- 在 ASP.NET 2.0 中，新的控制項和支援廣泛的瀏覽器陣列
- 64 位元支援

|||
|-|-|
|**CLR 版本**|2.0|
|**包含在 Visual Studio 版本中**|2005|
|**Windows 版本**|N/A|
|**Windows Server 版本**|✔️ 2008 R2 SP1<br />✔️ 2008 SP2<br />✔️2003|
|**若要判斷已安裝的 .NET 版本**|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-11"></a>.NET Framework 1.1

[新功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29)：

- ASP.NET mobile 控制項
- 並存執行
- IPv6 支援

|||
|-|-|
|**CLR 版本**|1.1|
|**包含在 Visual Studio 版本中**|2003|
|**Windows 版本**|N/A|
|**Windows Server 版本**|✔️2003|
|**若要判斷已安裝的 .NET 版本**|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**CLR 版本**|1.0|
|**包含在 Visual Studio 版本中**|Visual Studio .NET|
|**Windows 版本**|N/A|
|**Windows Server 版本**|N/A|
|**若要判斷已安裝的 .NET 版本**|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|

> [!NOTE]
>
> - 必須透過[控制台（適用于 windows）或伺服器管理員（適用于 Windows Server）](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel)，在此作業系統上啟用 .NET Framework。
> - 一般來說，您不應該卸載電腦上已安裝的任何 .NET Framework 版本，因為您使用的應用程式可能相依于特定版本，如果移除該版本，可能會中斷。 您可以同時在單一電腦上載入多個版本的 .NET Framework。 這表示您可以安裝 .NET Framework，而不需要卸載舊版本。 如需詳細資訊，請參閱[使用者入門](../get-started/index.md)。

## <a name="remarks-for-version-45-and-later"></a>4\.5 版和更新版本的備註

.NET Framework 4.5 是就地更新，會取代您電腦上的 .NET Framework 4，同樣地，.NET Framework 4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 和4.8 都是 .NET Framework 4.5 的就地更新。 就地更新表示它們使用相同的執行階段版本，但元件版本會更新，並包含新的類型和成員。 安裝其中一個更新之後，您的 .NET Framework 4、.NET Framework 4.5、.NET Framework 4.6 或 .NET Framework 4.7 應用程式會繼續執行，而不需重新編譯。 不過，反向操作則不可行。 我們不建議在舊版上執行以較新版本 .NET Framework 為目標的應用程式。 例如，我們不建議您在 .NET Framework 4.5 上執行針對 .NET Framework 4.6 的應用程式。

以下是適用的方針：

- 在 Visual Studio 中，您可以選擇 .NET Framework 4.5 作為專案的目標 Framework (這會設定 <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> 屬性)，將專案編譯為 .NET Framework 4.5 的組件或可執行檔。 此組件或可執行檔可用於任何已安裝 .NET Framework 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或 4.8 的電腦。

- 在 Visual Studio 中，您可以選擇 .NET Framework 4.5.1 做為專案的目標架構，將它編譯為 .NET Framework 4.5.1 元件或可執行檔。 只能在已安裝 .NET Framework 4.5.1 或更新版本的電腦上執行此元件或可執行檔。 以 .NET Framework 4.5.1 為目標的可執行檔將會遭到封鎖，而無法在只安裝舊版 .NET Framework 的電腦上執行，例如 .NET Framework 4.5。 系統會提示使用者安裝 .NET Framework 4.5.1。 此外，不應從以舊版 .NET Framework 為目標的應用程式中呼叫 .NET Framework 4.5.1 元件，例如 .NET Framework 4.5。

  > [!NOTE]
  > .NET framework 4.5.1 及 .NET Framework 4.5 在此處僅用於示範。 所述的原則適用于以較新版本為目標的任何應用程式，而其執行所在之系統上所安裝的 .NET Framework。

.NET Framework 中的某些變更可能需要變更您的應用程式程式碼;請先參閱[應用程式相容性](application-compatibility.md)，再使用 .NET Framework 4.5 或更新版本執行現有的應用程式。 如需安裝目前版本的詳細資訊，請參閱[安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)。 如需 .NET Framework 支援的相關資訊，請參閱 .NET 網站上的[.NET Framework 官方支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)。

## <a name="remarks-for-older-versions"></a>較舊版本的備註

.NET Framework 版本 2.0、3.0 和 3.5 使用相同版本的 CLR (CLR 2.0) 建置。 這些版本代表單一安裝的連續執行層。 每個版本都是以累加方式建置於舊版之上。 您不能在電腦上並存執行2.0、3.0 和3.5 版。 當您安裝 3.5 版時，會自動取得 2.0 和 3.0 執行層，而針對 2.0、3.0 和 3.5 版所建置的應用程式全都可以在 3.5 版上執行。 不過，.NET Framework 4 結束此分層方法，且該版本和更新版本 (.NET Framework 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 和 4.8) 也代表單一安裝的連續層。 從 .NET Framework 4 開始，您可以使用同進程、並存裝載，在單一進程中執行多個 CLR 版本。 如需詳細資訊，請參閱[組件和並存執行](../../standard/assembly/side-by-side-execution.md)。

此外，如果您的應用程式以2.0、3.0 或3.5 版為目標，您的使用者可能需要先在 Windows 8、Windows 8.1 或 Windows 10 電腦上啟用 .NET Framework 3.5，才能執行您的應用程式。 如需詳細資訊，請參閱[在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5](../install/dotnet-35-windows-10.md)。

## <a name="next-steps"></a>後續步驟

- 如果您還不熟悉 .NET Framework，請參閱[概觀](../get-started/overview.md)中有關重要概念和功能的簡介。

- 如需 .NET Framework 4.5 及其點發行版的新功能和改進，請參閱[.NET Framework 的新](../whats-new/index.md)功能。

- 如需將您的應用程式遷移至較新版本的 .NET Framework 的詳細資訊，請參閱[遷移指南](index.md)。

- 如需判斷電腦上已安裝哪些版本或更新的資訊，請參閱 [如何：判斷安裝的 .NET Framework 版本](how-to-determine-which-versions-are-installed.md)和[如何：判斷安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。

## <a name="see-also"></a>另請參閱

- [版本相容性](version-compatibility.md)
| [.NET Framework 官方支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](../install/troubleshoot-blocked-installations-and-uninstallations.md)
