---
title: ".NET Framework 版本和相依性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "版本，.NET Framework"
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
caps.latest.revision: 122
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 118
---
# .NET Framework 版本和相依性
每一版 .NET Framework 都包含通用語言執行平台 \(CLR\)、基底類別庫及其他 Managed 程式庫。 本主題將說明各版 .NET Framework 的主要功能、提供有關基礎 CLR 版本和相關聯開發環境的資訊，以及識別 Windows 作業系統所安裝的版本。  
  
> [!NOTE]
>  如需下載和安裝 .NET Framework 的相關資訊，請參閱[安裝指南](../../../docs/framework/install/guide-for-developers.md)。  
  
 下表摘要說明 .NET Framework 版本記錄，並將每個版本與 Visual Studio、Windows 和 Windows Server 相互關聯。 請注意，Visual Studio 提供多目標功能，因此不受限於所列出的 .NET Framework 版本。  
  
 每一個新的 .NET Framework 版本都會保留舊版的功能並增加新的功能。 CLR 是透過自己的版本號碼加以識別。 .NET Framework 版本號碼會隨每個發行版本遞增，但是 CLR 版本不一定會遞增。 例如，.NET Framework 4、4.5 和更新版本包含 CLR 4，但是 .NET Framework 2.0、3.0 和 3.5 包含 CLR 2.0。 \(沒有 CLR 版本 3\)。  
  
 如需所支援作業系統的完整清單，請參閱 [系統需求](../../../docs/framework/get-started/system-requirements.md)。 如需下載，請參閱[安裝指南](../../../docs/framework/install/guide-for-developers.md)。 如需判斷電腦上安裝的 .NET Framework 版本，請參閱[如何：判斷安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)。  
  
 在資料表中，\[內含於\/可安裝於 Windows\] 與 \[內含於\/可安裝於 Windows Server\] 資料行中標有 \* 的作業系統版本上安裝的 .NET Framework 版本，必須[在控制台中啟用](../../../docs/framework/install/net-framework-3-5-on-windows-8-plus.md) \(適用於 Windows\) 或透過伺服器管理員啟用 \(適用於 Windows Server\)。  
  
|.NET Framework 版本|CLR 版本|功能|隨附於 Visual Studio 版本|✓ 隨附於<br />\+ 可安裝於<br />Windows|✓ 隨附於<br />\+ 可安裝於<br />Windows Server|判斷已安裝的 .NET 版本|  
|-----------------------|------------|--------|--------------------------|-----------------------------|------------------------------------|--------------------|  
|.NET 4.6.2|4|-   加密加強程式，不僅包括含有 FIS 186\-3 DSA 的 X509 憑證支援、必要金鑰對稱式加密支援、SHA\-2 雜湊 <xref:System.Security.Cryptography.Xml.SignedXml> 支援，也讓 ECDiffieHellman 金鑰衍生常式的輸入更清楚。<br />-   若是 Windows Presentation Foundation \(WPF\) 應用程式，則支援螢幕小鍵盤及個別監視器 DPI。<br />-   ClickOnce 支援 TLS 1.1 與 TLS 1.2 通訊協定。<br />-   支援將 Windows Form 和 WPF 應用程式轉換成 UWP 應用程式。||✓  10 年度更新版<br /><br /> \+  10 November Update<br /><br /> \+ 10<br />\+ 8.1<br />\+ 7|\+ 2012 R2<br />\+ 2012<br />\+ 2008 R2 SP1|使用 `Release` DWORD：<br /><br /> -   394802 \(Windows 10 年度更新版\)<br />-   394806 \(所有其他 OS 版本\)<br /><br /> \(請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)\)|  
|Net 4.6.1|4|-   支援包含 ECDSA 的 X509 憑證<br />-   ADO.NET 中硬體保護金鑰的「一律加密」支援<br />-   WPF 中的拼字檢查改進<br />-   [其他...](../../../docs/framework/whats-new/index.md)||✓  10 11 月更新<br /><br /> \+ 10<br />\+ 8.1<br />\+ 8<br />\+ 7|\+ 2012 R2<br />\+ 2012<br />\+ 2008 R2 SP1|使用 `Release` DWORD：<br /><br /> -   394254 \(Windows 10 11 月更新\)<br />-   394271 \(所有其他作業系統版本\)<br /><br /> \(請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)\)|  
|.NET 4.6|4|-   使用 .NET Native 編譯<br />-   ASP.NET Core 5<br />-   事件追蹤的改進<br />-   支援頁面編碼<br />-   [其他...](../../../docs/framework/whats-new/index.md)|2015，雖然有些 .NET 程式庫可於 [NuGet](https://www.nuget.org/) 取得。 如需詳細資訊，請參閱 [.NET Framework 和 Out\-of\-Band 發行版本](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)。|✓ 10<br />\+ 8.1<br />\+ 8<br />\+ 7<br />\+ Vista|\+ 2012 R2<br />\+ 2012<br />\+ 2008 R2 SP1<br />\+ 2008 SP2|使用 `Release` DWORD：<br /><br /> -   393295 \(Windows 10\)<br />-   393297 \(所有其他作業系統版本\)<br /><br /> \(請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)\)|  
|4.5.2|4|-   交易式系統和 ASP.NET 的新應用程式開發介面<br />-   Windows Form 控制項的系統 DPI 調整大小<br />-   程式碼分析增強功能<br />-   ETW 和壓力記錄增強功能<br />-   [其他...](../../../docs/framework/whats-new/index.md)|\-|\+ 8.1<br />\+ 8<br />\+ 7<br />\+ Vista|\+ 2012 R2<br />\+ 2012<br />\+ 2008 R2 SP1<br />\+ 2008 SP2|使用 `Release` DWORD：379893<br />\(請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)\)|  
|4.5.1|4|-   Windows Phone 市集應用程式的支援<br />-   自動繫結重新導向<br />-   效能和偵錯增強功能<br />-   [其他...](../../../docs/framework/whats-new/index.md)|2013|✓ 8.1<br />\+ 8<br />\+ 7<br />\+ Vista|✓ 2012 R2<br />\+ 2012<br />\+ 2008 R2 SP1<br />\+ 2008 SP2|使用 `Release` DWORD：<br /><br /> -   378675 \(Windows 8.1\)<br />-   378758 \(其他所有版本\)<br /><br /> \(請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)\)|  
|4.5|4|-   Windows 市集應用程式的支援<br />-   WPF、WCF、WF、ASP.NET 更新<br />-   [其他...](../../../docs/framework/whats-new/index.md)|2012|✓ 8<br />\+ 7<br />\+ Vista|✓ 2012<br />\+ 2008 R2 SP1<br />\+ 2008 SP2|使用 `Release` DWORD：378389<br />\(請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)\)|  
|4|4|-   擴充的基底類別庫<br />-   使用可攜式類別庫進行跨平台開發<br />-   MEF、DLR、程式碼合約<br />-   [其他...](http://msdn.microsoft.com/library/ms171868\(v=vs.100\).aspx)|2010|\+ 7<br />\+ Vista|\+ 2008 R2 SP1<br />\+ 2008 SP2<br />\+ 2003|請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
|3.5|2.0|-   啟用 AJAX 功能的網站<br />-   LINQ<br />-   動態資料<br />-   [其他...](http://msdn.microsoft.com/library/ms171868\(v=vs.90\).aspx)|2008|✓ 10✓ 8.1\*<br />✓ 8\*<br />✓ 7<br />\+ Vista|✓2008 R2 SP1\*<br />\+ 2012 R2<br />\+ 2012<br />\+ 2008 SP2<br />\+ 2003|請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
|3.0|2.0|-   WPF、WCF、WF、CardSpace|\-|✓ Vista|✓ 2008 R2 SP1\*<br />✓ 2008 SP2\*<br />\+ 2003|請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
|2.0|2.0|-   泛型<br />-   ASP.NET 新增功能<br />-   [其他...](http://msdn.microsoft.com/library/t357fb32\(v=vs.80\).aspx)|2005|\-|✓ 2008 R2 SP1<br />✓ 2008 SP2<br />✓ 2003|請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
|1.1|1.1|-   ASP.NET 和 ADO.NET 更新<br />-   並存執行<br />-   [其他...](http://msdn.microsoft.com/library/9wtde3k4\(v=vs.80\).aspx)|2003|\-|✓ 2003|請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
|1.0|1.0|.NET Framework 的第一個版本。|Visual Studio .NET|\-|\-|請參閱[相關指示](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
  
 一般而言，您不應該解除安裝電腦上已安裝的任何 .NET Framework 版本，因為您使用的應用程式可能倚賴特定版本，如果移除該版本，可能使應用程式中斷。 您可以同時在單一電腦上載入多個 .NET Framework 版本。 這表示，您不需要解除安裝舊版，可以直接安裝新版 .NET Framework。 如需詳細資訊，請參閱[快速入門](../../../docs/framework/get-started/index.md)。  
  
## 鎖定執行 .NET Framework 4.5 及更新版本的應用程式  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 屬於就地更新，會取代您電腦上的 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]；同樣地，[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 4.5.2、4.6、4.6.1 和 4.6.2 也是 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的就地更新，亦即，這些組件全部使用相同的執行階段版本，但組件版本會更新，並加入新的類型及成員。 安裝這些更新的其中一項之後，您的 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 應用程式應該可以繼續執行，而無需重新編譯。 不過，反向操作則不可行。 不建議在舊版 .NET Framework 上執行要以新版 .NET framework 為目標的應用程式。 比方說，我們不建議您在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 上執行以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 為目標的應用程式。 以下是適用的方針：  
  
-   在 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 中，您可以選擇 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 做為專案的目標 Framework \(這樣做會設定 <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=fullName> 屬性\)，將專案編譯成 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 組件或可執行檔。 然後這個組件或可執行檔就可以在任何已安裝 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、4.5.1 或 4.5.2、4.6 或 4.6.1 的電腦上使用。  
  
-   在 Visual Studio 中，您可以選擇 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 做為專案的目標架構 \(這會設定 <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=fullName> 屬性\) 來將專案編譯成 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 組件或可執行檔。 此組件或可執行檔只能在已安裝 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 或 .NET Framework 最新版本的電腦上執行。 以 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 為目標的可執行檔將在只安裝舊版 .NET Framework \(例如 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]\) 的電腦上遭到封鎖而無法執行，而且系統會提示使用者安裝 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]。 此外，不應從以舊版 .NET Framework \(例如 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]\) 為目標的應用程式呼叫 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 組件。  
  
     [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 及 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 在這裡僅作示範用途。 此原則適用於以比執行所在系統上安裝版本更新之 .NET Framework 為目標的任何應用程式。  
  
 .NET Framework 中的某些變更可能需要您變更應用程式程式碼。在您執行 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或更新版本的現有應用程式之前，請參閱[應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md)。 如需安裝目前版本的詳細資訊，請參閱[安裝指南](../../../docs/framework/install/guide-for-developers.md)。 如需 .NET Framework 支援的相關資訊，請參閱 Microsoft 技術支援網站上的 [Microsoft .NET Framework 支援週期原則](http://go.microsoft.com/fwlink/?LinkId=196607)。  
  
## 鎖定及執行舊版的應用程式  
 .NET Framework 2.0、3.0 及 3.5 版是用相同版本的 CLR \(CLR 2.0\) 所建置。 這些版本代表單一安裝的連續執行層。 每個版本都是以累加方式建置於舊版之上。 2.0、3.0 和 3.5 版無法在電腦上並存執行。 當您安裝 3.5 版時，會自動取得 2.0 和 3.0 執行層，而針對 2.0、3.0 和 3.5 版所建置的應用程式全都可以在 3.5 版上執行。 不過，.NET Framework 4 已不再採用此分層方法。 從 .NET Framework 4 開始，您可以使用同處理序並存裝載功能，在單一處理序中執行多個 CLR 版本。 如需詳細資訊，請參閱[組件和並存執行](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)。  
  
 此外，如果您的應用程式是以 2.0、3.0 或 3.5 版為目標，則使用者可能需要先在 [!INCLUDE[win8](../../../includes/win8-md.md)] 或 [!INCLUDE[win81](../../../includes/win81-md.md)] 電腦上啟用 .NET Framework 3.5，才能執行您的應用程式。 如需詳細資訊，請參閱[Installing the .NET Framework 3.5 on Windows 8 and later versions](../../../docs/framework/install/net-framework-3-5-on-windows-8-plus.md)。  
  
## 後續步驟  
  
-   如果您還不熟悉 .NET Framework，請參閱[概觀](../../../docs/framework/get-started/overview.md)中有關重要概念和功能的簡介。  
  
-   如需 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 及其點發行版本中的新功能和增強功能，請參閱[新功能](../../../docs/framework/whats-new/index.md)。  
  
-   如需將應用程式從 .NET Framework 4 移轉至 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 及其點發行版本的詳細資訊，請參閱[移轉指南](../Topic/Migration%20Guide%20to%20the%20.NET%20Framework%204.6%20and%204.5%20.md)。  
  
-   如需判斷電腦上已安裝哪些版本或更新的相關資訊，請參閱[如何：判斷安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)和[如何：判斷安裝的 .NET Framework 更新](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)。  
  
## 請參閱  
 [版本相容性](../../../docs/framework/migration-guide/version-compatibility.md)   
 [Microsoft .NET Framework 支援週期原則](http://go.microsoft.com/fwlink/?LinkId=196607)   
 [疑難排解](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)