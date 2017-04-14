---
title: "WPF 部分信任安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯部分信任的應用程式"
  - "偵測使用權限"
  - "功能安全性需求"
  - "管理使用權限"
  - "部分信任的應用程式, 偵錯"
  - "部分信任安全性"
  - "權限, 偵測"
  - "權限, 管理"
  - "Internet Explorer 安全性設定"
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
caps.latest.revision: 40
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 36
---
# WPF 部分信任安全性
<a name="introduction"></a> 一般來說，應該禁止網際網路應用程式直接存取重要系統資源，以防產生惡意損害。  根據預設，[!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] 和用戶端指令碼語言無法存取重要系統資源。  因為 [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] 瀏覽器裝載的應用程式可以從瀏覽器啟動，所以應該要受到類似的限制。  若要強制執行這些限制，[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 會依賴[!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] 和 [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] \(請參閱 [WPF 安全性策略 – 平台安全性](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)\)。  根據預設，瀏覽器裝載的應用程式會要求 \[網際網路\] 區域 [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] 權限集合，不論這些應用程式是從網際網路、近端內部網路或本機電腦啟動。  不是以完整權限集合執行的應用程式就是所謂的以部分信任執行。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 提供各種的支援，確保有最多的功能能夠安全地在部分信任的應用程式中使用，與 [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] 搭配使用則提供針對部分信任的額外程式設計支援。  
  
 此主題包括下列章節：  
  
-   [WPF 功能部分信任支援](#WPF_Feature_Partial_Trust_Support)  
  
-   [部分信任程式設計](#Partial_Trust_Programming)  
  
-   [管理使用權限](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## WPF 功能部分信任支援  
 下表概略列出 [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] 的功能，這些功能可以安全地在 \[網際網路\] 區域權限集合限制之下使用。  
  
 表 1：可以在部分信任下安全使用的 WPF 功能  
  
|功能區域|功能|  
|----------|--------|  
|一般|瀏覽器視窗<br /><br /> 原始站台存取<br /><br /> IsolatedStorage \(512KB 限制\)<br /><br /> UIAutomation 提供者<br /><br /> 命令<br /><br /> 輸入法 \(IME\)<br /><br /> Tablet 手寫筆和筆墨\/筆跡<br /><br /> 使用滑鼠捕捉和移動事件模擬拖放<br /><br /> OpenFileDialog<br /><br /> XAML 還原序列化 \(透過 XamlReader.Load\)|  
|Web 整合|瀏覽器下載對話方塊<br /><br /> 最上層使用者啟始的巡覽<br /><br /> mailto:links<br /><br /> 統一資源識別元參數<br /><br /> HTTPWebRequest<br /><br /> IFRAME 中裝載的 WPF 內容<br /><br /> 使用框架裝載相同站台的 HTML 網頁<br /><br /> 使用 WebBrowser 裝載相同站台的 HTML 網頁<br /><br /> Web 服務 \(ASMX\)<br /><br /> Web 服務 \(使用 Windows Communication Foundation\)<br /><br /> 指令碼<br /><br /> 文件物件模型|  
|視覺效果|2D 和 3D<br /><br /> 動畫<br /><br /> 媒體 \(原始站台和跨網域\)<br /><br /> 影像\/音訊\/視訊|  
|讀取|FlowDocument<br /><br /> XPS 文件<br /><br /> 內嵌和系統字型<br /><br /> CFF 和 TrueType 字型|  
|編輯|拼字檢查<br /><br /> RichTextBox<br /><br /> 純文字和筆墨\/筆跡剪貼簿支援<br /><br /> 使用者啟始的貼上<br /><br /> 複製選取的內容|  
|控制項|一般控制項|  
  
 上表涵蓋概略的 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 功能。  如需詳細資訊，請參閱 [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] 文件中有關於每個 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 成員所需權限的說明。  此外，下列功能也具有關於部分信任執行的詳細資訊，包括特殊考量。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] \(請參閱 [XAML 概觀 \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)\)。  
  
-   快顯 \(請參閱 <xref:System.Windows.Controls.Primitives.Popup?displayProperty=fullName>\)。  
  
-   拖放 \(請參閱[拖放概觀](../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)\)。  
  
-   剪貼簿 \(請參閱 <xref:System.Windows.Clipboard?displayProperty=fullName>\)。  
  
-   影像處理 \(請參閱 <xref:System.Windows.Controls.Image?displayProperty=fullName>\)。  
  
-   序列化 \(請參閱 <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=fullName>、<xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=fullName>\)。  
  
-   開啟檔案對話方塊 \(請參閱 <xref:Microsoft.Win32.OpenFileDialog?displayProperty=fullName>\)。  
  
 下表概述無法安全地在 \[網際網路\] 區域權限集合限制之下執行的 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 功能。  
  
 表 2：在部分信任下不安全的 WPF 功能  
  
|功能區域|功能|  
|----------|--------|  
|一般|視窗 \(應用程式定義的視窗和對話方塊\)<br /><br /> SaveFileDialog<br /><br /> 檔案系統<br /><br /> 登錄存取<br /><br /> 拖放<br /><br /> XAML 序列化 \(透過 XamlWriter.Save\)<br /><br /> UIAutomation 用戶端<br /><br /> 來源視窗存取 \(HwndHost\)<br /><br /> 完全語音支援<br /><br /> Windows Form 互通性|  
|視覺效果|點陣圖效果<br /><br /> 影像編碼|  
|編輯|RTF 剪貼簿<br /><br /> 完全 XAML 支援|  
  
<a name="Partial_Trust_Programming"></a>   
## 部分信任程式設計  
 對於 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] 應用程式，超過預設使用權限集合的程式碼將會根據安全性區域而有不同的行為。  在某些情況下，使用者會在嘗試安裝此程式碼時收到警告。  使用者可以選擇繼續或取消安裝。  下表說明應用程式在每個安全性區域的行為，以及您要怎麼做才能讓應用程式獲得完全信任。  
  
|安全性區域|行為|取得完全信任|  
|-----------|--------|------------|  
|本機電腦|自動完全信任|不需任何動作。|  
|內部網路和限制的網站|提示需有完全信任|使用憑證簽署 XBAP，以便使用者在提示中看見來源。|  
|網際網路|失敗並顯示「未授與信任」|使用憑證簽署 XBAP。|  
  
> [!NOTE]
>  上表中說明的行為適用於未遵循 ClickOnce 信任部署模型的完全信任 XBAP。  
  
 一般來說，會超過允許之權限的程式碼通常都是供獨立應用程式和瀏覽器裝載的應用程式共用的通用程式碼。  [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] 和 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 提供數個方法可以管理這個案例。  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### 使用 CAS 偵測權限  
 在某些情況下，程式庫組件中的共用程式碼可能同時由獨立應用程式和 [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] 兩者使用。  在這些情況下，程式碼執行功能時需要的權限可能會比應用程式權限集合所允許的權限還多。  您的應用程式可以使用 [!INCLUDE[TLA#tla_winfx](../../../includes/tlasharptla-winfx-md.md)] 安全性來偵測它是否有特定的權限。  體來說，它可以在期望有某特定權限的執行個體上呼叫 <xref:System.Security.CodeAccessPermission.Demand%2A> 方法來測試是否具有特定權限。  這會顯示在下列範例中，其中的程式碼會查詢它是否有權將檔案儲存至本機磁碟：  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 如果應用程式沒有所需的權限，這個 <xref:System.Security.CodeAccessPermission.Demand%2A> 呼叫會擲回安全性例外狀況。  否則表示已授與權限。  `IsPermissionGranted` 會封裝此行為並依適當情況傳回 `true` 或 `false`。  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### 功能上非失誤性降低  
 遇到能夠從不同區域執行的程式碼時，如果能夠偵測該程式碼是否有權執行需要的作業，將有很大的幫助。  偵測區域是一回事，如果可能的話最好能夠提供替代方法給使用者。  例如，完全信任的應用程式通常可以讓使用者在任何位置建立檔案，而部分信任應用程式則只能在獨立的儲存區中建立檔案。  如果由完全信任應用程式 \(獨立應用程式\) 和部分信任應用程式 \(裝載瀏覽器的應用程式\) 兩者共用的組件中，有建立檔案的程式碼，而且這兩種應用程式都想讓使用者可以建立檔案，則共用程式碼應先偵測它是在部分信任或完全信任下執行，再於適當位置建立檔案。  下列程式碼會示範這兩種情形。  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 在許多情況下，您應該可以找到部分信任替代方法。  
  
 在受控制的環境中，例如內部網路，自訂 Managed 架構可以跨用戶端群安裝至[!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)] 中。  這些程式庫可執行需要完全信任的程式碼，並能透過 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 由只擁有部分信任的應用程式參考 \(如需詳細資訊，請參閱 [安全性](../../../docs/framework/wpf/security-wpf.md)和 [WPF 安全性策略 – 平台安全性](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)\)。  
  
<a name="Browser_Host_Detection"></a>   
### 瀏覽器裝載偵測  
 使用 [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] 檢查權限，是在需要以個別權限基準做檢查時相當適合的方法。  雖然這個方法依賴攔截例外狀況做為正常處理程序的一部分，但不建議在一般作業中使用，而且會有效能問題。  相反地，如果您的 [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] 只在 \[網際網路\] 區域沙箱中執行，可以使用 <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=fullName> 屬性，它會針對 [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] 傳回 true。  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> 只會區分應用程式是否是在瀏覽器中執行，不會區分執行所使用的權限集合。  
  
<a name="Managing_Permissions"></a>   
## 管理使用權限  
 根據預設，[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] 會以部分信任執行 \(預設 \[網際網路\] 區域權限集合\)。  不過，根據應用程式需求的不同，可能會變更預設的權限集合。  例如，[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] 如果是從近端內部網路啟動，就可以運用更高的權限集合，如下表所示。  
  
 表 3：近端內部網路和網際網路權限  
  
|使用權限|屬性|近端內部網路|網際網路|  
|----------|--------|------------|----------|  
|DNS|存取 DNS 伺服器|是|否|  
|環境變數|讀取|是|否|  
|檔案對話方塊|開啟|是|是|  
|檔案對話方塊|不受限|是|否|  
|隔離儲存區|依據使用者的組件隔離|是|否|  
|隔離儲存區|未知的隔離|是|是|  
|隔離儲存區|無限制的使用者配額|是|否|  
|媒體|安全音訊、視訊及影像|是|是|  
|列印|預設列印|是|否|  
|列印|安全列印|是|是|  
|反映|發出|是|否|  
|安全性|Managed 程式碼執行|是|是|  
|安全性|判斷提示授與的權限|是|否|  
|使用者介面|不受限|是|否|  
|使用者介面|安全的最上層視窗|是|是|  
|使用者介面|專屬的剪貼簿|是|是|  
|Web 瀏覽器|至 HTML 的安全架構巡覽|是|是|  
  
> [!NOTE]
>  使用者啟始的「剪下及貼上」只適用於部分信任的情況。  
  
 如果您需要提高權限，則需變更專案設定和 ClickOnce 應用程式資訊清單。  如需詳細資訊，請參閱 [WPF XAML 瀏覽器應用程式概觀](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)。  下列文件也能提供有用的資訊。  
  
-   [Mage.exe \(資訊清單產生和編輯工具\)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
-   [MageUI.exe \(圖形用戶端、資訊清單產生和編輯工具\)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
-   [保護 ClickOnce 應用程式](../Topic/Securing%20ClickOnce%20Applications.md).  
  
 如果您的 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] 需要完整信任，可以使用相同的工具提高要求的權限。  不過，[!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] 只有在安裝於本機電腦並從本機電腦、內部網路或是瀏覽器的信任或允許網站中列出的 URL 啟動時，才會獲得完全信任。  如果應用程式是從內部網路或信任的網站安裝，則使用者將收到通知權限提升的標準 ClickOnce 提示。  使用者可以選擇繼續或取消安裝。  
  
 或者，您可以使用 ClickOnce 信任部署模型從任何安全性區域進行完全信任的部署。  如需詳細資訊，請參閱[受信任的應用程式部署概觀](../Topic/Trusted%20Application%20Deployment%20Overview.md)和 [安全性](../../../docs/framework/wpf/security-wpf.md)。  
  
## 請參閱  
 [安全性](../../../docs/framework/wpf/security-wpf.md)   
 [WPF 安全性策略 – 平台安全性](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)   
 [WPF 安全性策略 – 安全性工程](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)