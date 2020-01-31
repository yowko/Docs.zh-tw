---
title: 部分信任安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- partial trust security [WPF]
- detecting permissions [WPF]
- security settings for Internet Explorer [WPF]
- partial trust applications [WPF], debugging
- permissions [WPF], managing
- debugging partial trust applications [WPF]
- permissions [WPF], detecting
- feature security requirements [WPF]
- managing permissions [WPF]
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
ms.openlocfilehash: 0d9bbcc32eea49afc6ecc713b0cf005b4434a67d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743337"
---
# <a name="wpf-partial-trust-security"></a>WPF 部分信任安全性
<a name="introduction"></a> 一般而言，網際網路應用程式應該限制不得直接存取重要的系統資源，以防止惡意損害。 根據預設，HTML 和用戶端指令碼語言無法存取重要的系統資源。 因為 Windows Presentation Foundation （WPF）瀏覽器裝載的應用程式可以從瀏覽器啟動，所以它們應該符合一組類似的限制。 為了強制執行這些限制，WPF 同時依賴代碼啟用安全性（CAS）和 ClickOnce （請參閱[Wpf 安全性策略-平臺安全性](wpf-security-strategy-platform-security.md)）。 根據預設，瀏覽器裝載的應用程式會要求網際網路區域 CA 的許可權集，而不論它們是從網際網路、近端內部網路或本機電腦啟動。 使用少於完整權限集執行的應用程式便是以部分信任執行。  
  
 WPF 提供各種不同的支援，以確保能夠在部分信任的情況下安全地使用最多的功能，以及使用 CAS，為部分信任程式設計提供額外的支援。  
  
 此主題包括下列章節：  
  
- [WPF 功能部分信任支援](#WPF_Feature_Partial_Trust_Support)  
  
- [部分信任程式設計](#Partial_Trust_Programming)  
  
- [管理權限](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>WPF 功能部分信任支援  
 下表列出可在網際網路區域許可權集合限制內安全使用的 Windows Presentation Foundation （WPF）高階功能。  
  
 表 1：在部分信任中安全的 WPF 功能  
  
|功能區|特殊功能|  
|------------------|-------------|  
|一般|瀏覽器視窗<br /><br /> 原始站台存取<br /><br /> IsolatedStorage (512 KB 限制)<br /><br /> UIAutomation 提供者<br /><br /> 命令<br /><br /> 輸入法 (IME)<br /><br /> 平板電腦手寫筆和筆跡<br /><br /> 使用滑鼠捕捉和移動事件模擬拖放<br /><br /> OpenFileDialog<br /><br /> XAML 還原序列化 (透過 XamlReader.Load)|  
|Web 整合|瀏覽器下載對話方塊<br /><br /> 最上層使用者啟始的瀏覽<br /><br /> mailto:links<br /><br /> 統一資源識別項參數<br /><br /> HTTPWebRequest<br /><br /> 在 IFRAME 中裝載的 WPF 內容<br /><br /> 使用框架裝載相同站台的 HTML 頁面<br /><br /> 使用網頁瀏覽器裝載相同站台的 HTML 頁面<br /><br /> Web 服務 (ASMX)<br /><br /> Web 服務 (使用 Windows Communication Foundation)<br /><br /> 正在處理指令碼<br /><br /> 文件物件模型|  
|視覺效果|2D 和 3D<br /><br /> 動畫<br /><br /> 媒體 (原始站台和跨網域)<br /><br /> 影像處理/音訊/視訊|  
|讀取|FlowDocuments<br /><br /> XPS 文件<br /><br /> 內嵌與系統字型<br /><br /> CFF 與 TrueType 字型|  
|使用|拼字檢查<br /><br /> RichTextBox<br /><br /> 純文字和筆跡剪貼簿支援<br /><br /> 使用者啟始的貼上<br /><br /> 複製選取的內容|  
|Controls|一般控制項|  
  
 下表涵蓋高階的 WPF 功能。 如需詳細資訊，Windows SDK 記錄 WPF 中每個成員所需的許可權。 此外，下列功能有關於部分信任執行的更詳細資訊，包括特殊考量。  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] （請參閱[XAML 總覽（WPF）](../../desktop-wpf/fundamentals/xaml.md)）。  
  
- 快顯視窗（請參閱 <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>）。  
  
- 拖放（請參閱[拖放總覽](./advanced/drag-and-drop-overview.md)）。  
  
- 剪貼簿（請參閱 <xref:System.Windows.Clipboard?displayProperty=nameWithType>）。  
  
- 影像處理（請參閱 <xref:System.Windows.Controls.Image?displayProperty=nameWithType>）。  
  
- 序列化（請參閱 <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>，<xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>）。  
  
- [開啟檔案] 對話方塊（請參閱 <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>）。  
  
 下表概述在網際網路區域許可權集合的限制內，不安全執行的 WPF 功能。  
  
 表 2：在部分信任中不安全的 WPF 功能  
  
|功能區|特殊功能|  
|------------------|-------------|  
|一般|視窗 (應用程式定義的視窗和對話方塊)<br /><br /> SaveFileDialog<br /><br /> 檔案系統<br /><br /> 登錄存取<br /><br /> 拖放<br /><br /> XAML 序列化 (透過 XamlWriter.Save)<br /><br /> UIAutomation 用戶端<br /><br /> 來源視窗存取 (HwndHost)<br /><br /> 完整的語音支援<br /><br /> Windows Forms 互通性|  
|視覺效果|點陣圖效果<br /><br /> 影像編碼|  
|使用|RTF 格式剪貼簿<br /><br /> 完整的 XAML 支援|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>部分信任程式設計  
 針對 XBAP 應用程式，超過預設許可權集合的程式碼會根據安全性區域而有不同的行為。 在某些情況下，使用者會在嘗試安裝它時收到一則警告。 使用者可以選擇繼續或取消安裝。 下表描述每個安全性區域的應用程式行為，以及您必須針對應用程式執行什麼動作才能得到完全信任。  
  
|安全性區域|行為|取得完全信任|  
|-------------------|--------------|------------------------|  
|本機電腦|自動的完全信任|無須任何動作。|  
|內部網路和信任的網站|完全信任的提示|使用憑證簽署 XBAP，讓使用者在提示中看到來源。|  
|網際網路|因為「未授與信任」而失敗|使用憑證簽署 XBAP。|  
  
> [!NOTE]
> 上表中描述的行為是針對未遵循 ClickOnce 受信任部署模型的完全信任 XBAP。  
  
 一般而言，可能超過允許權限的程式碼很可能是在獨立式與瀏覽器裝載的應用程式之間共用的通用程式碼。 CAS 和 WPF 提供數種管理此案例的技術。  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>使用 CAS 偵測權限  
 在某些情況下，獨立應用程式和 Xbap 都可以使用程式庫元件中的共用程式碼。 在這些情況下，程式碼執行的功能，所需的權限可能會超過應用程式的已授與權限集合所允許的權限。 您的應用程式可以使用 Microsoft .NET Framework 安全性來偵測其是否具有特定許可權。 具體來說，它可以在所需許可權的實例上呼叫 <xref:System.Security.CodeAccessPermission.Demand%2A> 方法，測試它是否有特定的許可權。 這會顯示在下列的範例中，程式碼會查詢它是否能夠將檔案儲存到本機磁碟︰  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 如果應用程式沒有所需的許可權，<xref:System.Security.CodeAccessPermission.Demand%2A> 的呼叫將會擲回安全性例外狀況。 否則，便已授與權限。 `IsPermissionGranted` 會封裝此行為，並視需要傳回 `true` 或 `false`。  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>功能正常降級  
 能夠偵測程式碼是否有權執行它需要做的事，對於可以從不同區域執行的程式碼而言很有趣。 不過偵測區域是一件事，可能的話，為使用者提供替代方式會好上許多。 比方說，完全信任應用程式通常可讓使用者在任何想要的地方建立檔案，而部分信任應用程式則只能在隔離儲存區建立檔案。 如果建立檔案的程式碼存在於完全信任 (獨立式) 應用程式和部分信任 (瀏覽器裝載) 應用程式所共用的組件中，而且兩個應用程式都想要讓使用者能夠建立檔案，則共用的程式碼應該先偵測它是在部分信任還是完全信任中執行，然後才能在適當位置中建立檔案。 下列程式碼可示範兩種情況。  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 在許多情況下，您應該能夠找到部分信任的替代方法。  
  
 在受控制的環境（例如內部網路）中，可以將自訂的受控架構安裝到全域組件快取（GAC）中的用戶端基礎上。 這些程式庫可以執行需要完全信任的程式碼，並使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 來參考僅允許部分信任的應用程式（如需詳細資訊，請參閱[安全性](security-wpf.md)和[WPF 安全性策略-平臺安全性](wpf-security-strategy-platform-security.md)）。  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>瀏覽器裝載偵測  
 當您需要檢查每個許可權時，使用 CAS 檢查許可權是適合的技巧。 不過，這項技巧依賴在一般處理時攔截例外狀況，一般而言不建議這麼做，其可能會發生效能問題。 相反地，如果您的 XAML 瀏覽器應用程式（XBAP）只在網際網路區域沙箱中執行，您可以使用 <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> 屬性，它會針對 XAML 瀏覽器應用程式（Xbap）傳回 true。  
  
> [!NOTE]
> <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> 只會區別應用程式是否在瀏覽器中執行，而不是應用程式執行時所使用的許可權集。  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>管理權限  
 根據預設，Xbap 會以部分信任來執行（預設的網際網路區域許可權集合）。 不過，根據應用程式的需求，也可以變更預設的權限集合。 例如，如果從近端內部網路啟動 Xbap，它可以利用增加的許可權集合，如下表所示。  
  
 表 3︰近端內部網路和網際網路權限  
  
|[權限]|屬性|LocalIntranet|網際網路|  
|----------------|---------------|-------------------|--------------|  
|DNS|存取 DNS 伺服器|是|否|  
|環境變數|讀取|是|否|  
|檔案對話方塊|開啟|是|是|  
|檔案對話方塊|無限制的|是|否|  
|隔離儲存區|依據使用者隔離組件|是|否|  
|隔離儲存區|未知的隔離|是|是|  
|隔離儲存區|無限制的使用者配額|是|否|  
|媒體|安全的音訊、視訊和影像|是|是|  
|列印|預設列印|是|否|  
|列印|安全列印|是|是|  
|反射|發出|是|否|  
|安全性|Managed 程式碼執行|是|是|  
|安全性|判斷提示授與權限|是|否|  
|使用者介面|無限制的|是|否|  
|使用者介面|安全的最上層視窗|是|是|  
|使用者介面|擁有剪貼簿|是|是|  
|Web 瀏覽器|HTML 框架安全瀏覽|是|是|  
  
> [!NOTE]
> 在部分信任中，只有在使用者啟動時，才允許剪下和貼上。  
  
 如果您需要提高權限，您需要變更專案設定和 ClickOnce 應用程式資訊清單。 如需詳細資訊，請參閱 [WPF XAML 瀏覽器應用程式概觀](./app-development/wpf-xaml-browser-applications-overview.md)。 下列文件可能有用。  
  
- [Mage.exe (資訊清單產生和編輯工具)](../tools/mage-exe-manifest-generation-and-editing-tool.md)。  
  
- [MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)。  
  
- [保護 ClickOnce 應用程式](/visualstudio/deployment/securing-clickonce-applications)。  
  
 如果您的 XBAP 需要完全信任，您可以使用相同的工具來增加所要求的許可權。 雖然 XBAP 只會在安裝並從本機電腦、內部網路或從瀏覽器的受信任或允許的網站中所列的 URL 啟動時，才會收到完全信任。 如果應用程式是從內部網路或受信任的網站安裝，使用者會收到標準 ClickOnce 提示，通知他們權限已提高。 使用者可以選擇繼續或取消安裝。  
  
 或者，您可以使用 ClickOnce 受信任部署模型，以從任何安全性區域進行完全信任部署。 如需詳細資訊，請參閱[受信任的應用程式部署總覽](/visualstudio/deployment/trusted-application-deployment-overview)和[安全性](security-wpf.md)。  
  
## <a name="see-also"></a>請參閱

- [Security](security-wpf.md)
- [WPF 安全性策略 – 平台安全性](wpf-security-strategy-platform-security.md)
- [WPF 安全性策略 – 安全性工程](wpf-security-strategy-security-engineering.md)
