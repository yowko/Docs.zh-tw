---
title: .NET Framework 版本和相依性
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9f7a0bc3a7a41a77db3c90c2f88fb5ddfd7bfa0
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971081"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework 版本和相依性
每一版 .NET Framework 都包含通用語言執行平台 (CLR)、基底類別庫及其他 Managed 程式庫。 本主題將說明各版 .NET Framework 的主要功能、提供有關基礎 CLR 版本和相關聯開發環境的資訊，以及識別 Windows 作業系統所安裝的版本。  
  
> [!NOTE]
> 如需下載和安裝 .NET Framework 的資訊，請參閱[安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)。  
  
 下表摘要說明 .NET Framework 版本記錄，並將每個版本與 Visual Studio、Windows 和 Windows Server 相互關聯。 請注意，Visual Studio 提供多目標功能，因此不受限於所列出的 .NET Framework 版本。  
  
 每一個新的 .NET Framework 版本都會保留舊版的功能並增加新的功能。 CLR 是透過自己的版本號碼加以識別。 .NET Framework 版本號碼會隨每個發行版本遞增，但是 CLR 版本不一定會遞增。 例如，.NET Framework 4、4.5 和更新版本包含 CLR 4，但是 .NET Framework 2.0、3.0 和 3.5 包含 CLR 2.0。 (沒有 CLR 版本 3)。  
  
 如需完整的支援作業系統清單，請參閱[系統需求](../get-started/system-requirements.md)。 如需下載，請參閱[安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)。 若要判斷電腦上安裝的 .NET Framework 版本，請參閱[如何：判斷安裝的 .NET Framework 版本](how-to-determine-which-versions-are-installed.md)。  
  
 在下表中，[隨附於/可安裝於 Windows] 與 [隨附於/可安裝於 Windows Server] 欄中標有 ✓ 的作業系統版本上安裝的 .NET Framework 版本，必須[在控制台中啟用](../install/dotnet-35-windows-10.md) (適用於 Windows) 或透過伺服器管理員啟用 (適用於 Windows Server)。  

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]
 
|.NET Framework 版本|CLR 版本|包含在<br /> Visual Studio<br/>版本|✓ 隨附於<br />+ 可安裝於<br />Windows|✓ 隨附於<br />+ 可安裝於<br />Windows Server|判斷已安裝的 .NET 版本|  
|----------------------------|-----------------|--------------|---------------------------------------|----------------------------------------------------|-----------------------------------------------------------|-----------------------------------------| 
|4.8<br/><br/>[新功能](../whats-new/index.md#whats-new-in-net-framework-48)<br/><br/>[協助工具的新功能](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)<br /><br >[版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)|4| | ✓ 10 2019 年 5 月更新<br/><br/> + 10 2018 年 10 月更新 (版本 1809) <br/> + 10 2018 年 4 月更新 (版本 1803) <br/> + 10 Fall Creators Update (版本 1709) <br/> + 10 Creators Update (版本 1703) <br/> + 10 Anniversary Update (版本 1607) <br/> + 8.1 <br/> +7 | + Windows Server 2019<br/> + Windows Server，版本 1809 <br/> + Windows Server，版本 1803 <br/> + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |使用 `Release` DWORD：<br/><br/> - 528040 (Windows 10 2019 年 5 月更新) <br/> - 528049 (所有其他作業系統版本) <br/><br/> (請參閱[相關指示](how-to-determine-which-versions-are-installed.md))|
|4.7.2<br/><br/>[新功能](../whats-new/index.md#whats-new-in-net-framework-472)<br/><br/>[協助工具的新功能](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)<br /><br >[版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)|4| | ✓ 10 2018 年 10 月更新 (版本 1809) <br/> ✓ 10 2018 年 4 月更新 (版本 1803) <br/><br/> + 10 Fall Creators Update (版本 1709) <br/> + 10 Creators Update (版本 1703) <br/> + 10 Anniversary Update (版本 1607) <br/> + 8.1 <br/> +7 | ✓ Windows Server 2019<br/> ✓ Windows Server，版本 1809 <br/> ✓ Windows Server，版本 1803 <br/><br/> + Windows Server，版本 1709 <br/> + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |使用 `Release` DWORD：<br/><br/> - 461814 (Windows 10 2018 年 10 月更新) <br/> - 461808 (Windows 10 2018 年 4 月更新及 Windows Server，版本 1803) <br/> - 461814 (所有其他作業系統版本) <br/><br/> (請參閱[相關指示](how-to-determine-which-versions-are-installed.md))|
|4.7.1<br/><br/>[新功能](../whats-new/index.md#whats-new-in-net-framework-471)<br/><br/>[協助工具的新功能](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)<br /><br >[版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)|4| | ✓ 10 Fall Creators Update (版本 1709) <br/> <br/> + 10 Creators Update (版本 1703) <br/> + 10 Anniversary Update (版本 1607) <br/> + 8.1 <br/> +7| + Windows Server，版本 1803 <br/><br/> ✓ Windows Server，版本 1709 <br/><br/> + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |使用 `Release` DWORD：<br/><br/> - 461308 (Windows 10 Creators Update 及 Windows Server，版本 1709) <br/> - 461310 (所有其他 OS 版本) <br/><br/> (請參閱[相關指示](how-to-determine-which-versions-are-installed.md))| 
|4.7<br/><br/>[新功能](../whats-new/index.md#whats-new-in-net-framework-47)<br /><br >[版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)|4| | ✓ 10 Creators Update (版本 1703) <br/> <br/> + 10 Anniversary Update (版本 1607) <br/> + 8.1 <br/> +7| + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |使用 `Release` DWORD：<br/><br/> - 460798 (Windows 10 Creators Update) <br/> - 460805 (所有其他作業系統版本) <br/><br/> (請參閱[相關指示](how-to-determine-which-versions-are-installed.md)) |  
|4.6.2<br/><br/>[新功能](../whats-new/index.md#whats-new-in-net-framework-462)<br /><br >[版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)|4||✓ 10 年度更新 (版本 1607) <br /><br /> + 10 November Update (版本 1511) <br/> + 10 <br/> + 8.1<br />+ 7|✓ 2016<br /><br /> + 2012 R2<br />+ 2012<br />+ 2008 R2 SP1|使用 `Release` DWORD：<br /><br /> - 394802 (Windows 10 年度更新版及 Windows Server 2016) <br />- 394806 (所有其他作業系統版本)<br /><br /> (請參閱[相關指示](how-to-determine-which-versions-are-installed.md))|  
|4.6.1<br/><br/>[新功能](../whats-new/index.md#whats-new-in-net-framework-461)<br /><br >[版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)|4||✓ 10 11 月更新 (版本 1511) <br /><br /> + 10<br />+ 8.1<br />+ 8<br />+ 7|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1|使用 `Release` DWORD：<br /><br /> - 394254 (Windows 10 11 月更新)<br />- 394271 (所有其他作業系統版本)<br /><br /> (請參閱[相關指示](how-to-determine-which-versions-are-installed.md))|  
|4.6<br/><br/>[新功能](../whats-new/index.md#whats-new-in-net-2015)<br /><br >[版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)|4|2015|✓ 10<br /><br />+ 8.1<br />+ 8<br />+ 7<br />+ Vista|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|使用 `Release` DWORD：<br /><br /> - 393295 (Windows 10)<br />- 393297 (所有其他作業系統版本)<br /><br /> (請參閱[相關指示](how-to-determine-which-versions-are-installed.md))|  
|4.5.2<br/><br/>[新功能](../whats-new/index.md#whats-new-in-net-framework-452)<br /><br >[版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)|4|-|+ 8.1<br />+ 8<br />+ 7<br />+ Vista|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|使用 `Release` DWORD：<br /><br /> 379893<br /><br />(請參閱[相關指示](how-to-determine-which-versions-are-installed.md))|  
|4.5.1<br/><br/>[新功能](../whats-new/index.md#whats-new-in-net-framework-451)<br /><br >[版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)|4|2013|✓ 8.1<br /><br />+ 8<br />+ 7<br />+ Vista|✓ 2012 R2<br /><br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|使用 `Release` DWORD：<br /><br /> - 378675 (Windows 8.1)<br />- 378758 (其他所有版本)<br /><br /> (請參閱[相關指示](how-to-determine-which-versions-are-installed.md))|  
|4.5<br/><br/>[新功能](../whats-new/index.md#whats-new-in-net-framework-45)<br /><br >[版本資訊](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)|4|2012|✓ 8<br />+ 7<br />+ Vista|✓ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|使用 `Release` DWORD：<br /><br /> 378389<br /><br />(請參閱[相關指示](how-to-determine-which-versions-are-installed.md))|  
|4<br/><br/>[新功能](../whats-new/index.md)|4|2010|+ 7<br />+ Vista|+ 2008 R2 SP1<br />+ 2008 SP2<br />+ 2003|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|  
|3.5<br/><br/>[新功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\))|2.0|2008|✓ 10\*<br/>✓ 8.1\*<br />✓ 8\*<br />✓ 7<br /><br />+ Vista|  + Windows Server，版本 1803\* <br/> + Windows Server，版本 1709\* <br/> + 2016\* <br/>+ 2012 R2\*<br />+ 2012\*<br /><br />✓2008 R2 SP1\*<br /><br/>+ 2008 SP2<br />+ 2003|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|  
|3.0<br/><br/>新增：<br/>WPF、WCF、WF、CardSpace|2.0|-|✓ Vista|✓ 2008 R2 SP1*<br />✓ 2008 SP2\*<br /><br />+ 2003|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|  
|2.0<br/><br/>[新功能](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/ms229284\(v%3dvs.80\))|2.0|2005|-|✓ 2008 R2 SP1<br />✓ 2008 SP2<br />✓ 2003|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|  
|1.1<br/><br/>[新功能](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/9wtde3k4\(v%3dvs.71\))|1.1|2003|-|✓ 2003|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|  
|1.0|1.0|Visual Studio .NET|-|-|請參閱[相關指示](how-to-determine-which-versions-are-installed.md)|  

**注意事項**

<sup>\*</sup>&nbsp;&nbsp;必須在此作業系統上透過[控制台 (適用於 Windows) 或伺服器管理員 (適用於 Windows Server)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel) 來啟用 .NET Framework。

 一般而言，您不應該解除安裝電腦上已安裝的任何 .NET Framework 版本，因為您使用的應用程式可能倚賴特定版本，如果移除該版本，可能使應用程式中斷。 您可以同時在單一電腦上載入多個 .NET Framework 版本。 這表示，您不需要解除安裝舊版，可以直接安裝新版 .NET Framework。 如需詳細資訊，請參閱[使用者入門](../get-started/index.md)。

## <a name="targeting-and-running-net-framework-apps-for-version-45-and-later"></a>鎖定執行 .NET Framework 4.5 及更新版本的應用程式  
 .NET framework 4.5 是取代您電腦中 .NET Framework 4 的就地更新；同樣地，.NET Framework 4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 和 4.8 都是 .NET Framework 4.5 的就地更新，這表示它們使用相同的執行階段版本，但會更新組件版本並納入新的類型和成員。 安裝其中一個更新之後，您的 .NET Framework 4、.NET Framework 4.5、.NET Framework 4.6 或 .NET Framework 4.7 應用程式會繼續執行，而不需重新編譯。 不過，反向操作則不可行。 不建議您在舊版 .NET Framework 上執行目標為新版 .NET Framework 的應用程式。 例如，我們不建議您在 .NET Framework 4.5 上執行針對 .NET Framework 4.6 的應用程式。 以下是適用的方針：  
  
- 在 Visual Studio 中，您可以選擇 .NET Framework 4.5 作為專案的目標 Framework (這會設定 <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> 屬性)，將專案編譯為 .NET Framework 4.5 的組件或可執行檔。 此組件或可執行檔可用於任何已安裝 .NET Framework 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或 4.8 的電腦。  
  
- 在 Visual Studio 中，您可以選擇 .NET Framework 4.5.1 作為專案的目標 Framework (這會設定 <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> 屬性)，將專案編譯為 .NET Framework 4.5.1 組件或可執行檔。 此組件或可執行檔只應在已安裝 .NET Framework 4.5.1 或更新版本 .NET framework 的電腦上執行。 針對 .NET Framework 4.5.1 的可執行檔，將無法在僅安裝舊版 .NET Framework 的電腦上執行 (例如 .NET Framework 4.5)，系統會提示使用者安裝 .NET Framework 4.5.1。 此外，.NET Framework 4.5.1 組件不應從針對舊版 .NET Framework (例如 .NET Framework 4.5) 的應用程式中呼叫。  
  
     .NET framework 4.5.1 及 .NET Framework 4.5 在此處僅用於示範。 此準則適用於目標較安裝於執行所在系統上版本更新之 .NET Framework 的任何應用程式。  
  
 .NET Framework 中的某些變更可能需要變更您的應用程式程式碼；在您使用 .NET Framework 4.5 或更新版本執行現有應用程式之前，請參閱[應用程式相容性](application-compatibility.md)。 如需安裝目前版本的詳細資訊，請參閱[安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)。 如需 .NET Framework 支援的資訊，請參閱 Microsoft 技術支援網站上的 [Microsoft .NET Framework 支援週期原則](https://go.microsoft.com/fwlink/?LinkId=196607)。  
  
## <a name="targeting-and-running-apps-for-older-versions"></a>鎖定及執行舊版的應用程式  

.NET Framework 版本 2.0、3.0 和 3.5 使用相同版本的 CLR (CLR 2.0) 建置。 這些版本代表單一安裝的連續執行層。 每個版本都是以累加方式建置於舊版之上。 2\.0、3.0 和 3.5 版無法在電腦上並存執行。 當您安裝 3.5 版時，會自動取得 2.0 和 3.0 執行層，而針對 2.0、3.0 和 3.5 版所建置的應用程式全都可以在 3.5 版上執行。 不過，.NET Framework 4 結束此分層方法，且該版本和更新版本 (.NET Framework 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 和 4.8) 也代表單一安裝的連續層。  從 .NET Framework 4 開始，您可以使用內含式並存裝載，在單一處理序中執行多個版本的 CLR。 如需詳細資訊，請參閱[組件和並存執行](../../standard/assembly/side-by-side-execution.md)。  
  
 此外，如果您的應用程式是以 2.0、3.0 或 3.5 作版為目標，則使用者可能需要先在 Windows 8、Windows 8.1 或 Windows 10 的電腦上啟用 .NET Framework 3.5，才可執行您的應用程式。 如需詳細資訊，請參閱[在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5](../install/dotnet-35-windows-10.md)。  
  
## <a name="next-steps"></a>後續步驟  
  
- 如果您還不熟悉 .NET Framework，請參閱[概觀](../get-started/overview.md)中有關重要概念和功能的簡介。  
  
- 如需 .NET Framework 4.5 及其點發行版本中的新功能和增強功能，請參閱 [.NET Framework 的新功能](../whats-new/index.md)。  
  
- 如需將應用程式從 .NET Framework 4 移轉至 .NET Framework 4.5 及其點發行版本的資訊，請參閱[移轉手冊](index.md)。  
  
- 如需判斷電腦上已安裝哪些版本或更新的資訊，請參閱[如何：判斷安裝的 .NET Framework 版本](how-to-determine-which-versions-are-installed.md)和[如何：判斷安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。  
  
## <a name="see-also"></a>另請參閱

- [版本相容性](version-compatibility.md)
- [Microsoft .NET Framework 支援週期原則](https://go.microsoft.com/fwlink/?LinkId=196607)
- [疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](../install/troubleshoot-blocked-installations-and-uninstallations.md)
