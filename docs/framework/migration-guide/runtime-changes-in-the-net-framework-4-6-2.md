---
title: ".NET Framework 4.6.2 中的執行階段變更 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6.2
- application compatibility
ms.assetid: 23bf3a87-6fa1-4b5e-b92c-a39867a06e7f
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: da809955776b5a5cd3776898ecc4c97db74ceb0e
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="runtime-changes-in-the-net-framework-462"></a>.NET Framework 4.6.2 中的執行階段變更
在某些罕見的情況下，執行階段變更可能會影響以舊版 .NET Framework 為目標，但在新版 .NET Framework 執行階段上執行的現有應用程式。 這些變更也包含在不同的 .NET Framework 執行階段環境中執行之應用程式間的行為差異。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 包含下列區域的變更：  
  
-   [核心](#Core)  
  
-   [ASP.NET](#ASP)

-   [Data](#Data)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [XML 簽署和驗證](#XML)  
  
<a name="Core"></a>   
## <a name="core"></a>核心  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName><br /><br /> <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory%2A?displayProperty=fullName>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中的字元類別根據 Unicode 版本 8.0。 .NET framework 4.5 至 4.6.1 版是根據 Unicode 6.3 版來分類 Unicode 字元。<br /><br /> 字元比較和排序不會受到這項變更的影像。 如需詳細資訊，請參閱 <xref:System.String> 類別主題的＜字串及 Unicode 標準＞一節。|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中的字元類別可能不符合舊版 .NET Framework。 這項變更主要會影響卻洛奇文音節和新傣仂文母音符號和音調標記。<br /><br /> 若要解決這項變更的影響，您應該檢閱程式碼並將仰賴硬式編碼的 Unicode 字元分類邏輯移除或變更。|次要|  
|<xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=fullName>, <xref:System.Security.Cryptography.RSACng.ImportParameters%2A?displayProperty=fullName>, <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A?displayProperty=fullName>, <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=fullName>|從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，這些方法都能存取具有非標準金鑰大小的 RSA 憑證金鑰。 在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和更早版本中，嘗試存取那些金鑰會擲回 <xref:System.Security.Cryptography.CryptographicException>。|使用非標準金鑰大小時，如果有任何仰賴 <xref:System.Security.Cryptography.CryptographicException> 的例外狀況處理邏輯，都應予以移除。|Edge|  
|<xref:System.Security.Cryptography.RSACng.VerifyHash%2A?displayProperty=fullName>|從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，如果簽章本身的格式不正確，此方法會傳回 `false`。 現在任何驗證失敗都會傳回 `false`。<br /><br /> 在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 和 4.6.1 中，如果簽章的格式不正確，此方法會擲回 <xref:System.Security.Cryptography.CryptographicException>。|如果驗證失敗且此方法傳回 `false`，應改為執行任何仰賴 <xref:System.Security.Cryptography.CryptographicException> 來執行的程式碼。|次要|  
  
## <a name="a-nameasp--aspnet"></a><a name="ASP" /> ASP.NET

|功能|變更|影響|範圍| 
|-------------|------------|------------|-----------|  
| <xref:System.Web.HttpRuntime.AppDomainApopPath%2A> | 在 .NET Framework 4.6.2 中，當擷取包含 Null 字元的 <xref:System.Web.HttpRuntime.AppDomainAppPath%2A> 值時，執行階段會擲回 <xref:System.NullReferenceException>。 在 .NET Framework 4.6.1 和更早版本中，它會擲回 <xref:System.ArgumentNullException>。  | 您可以執行下列動作以回應這項變更︰ <br/> - 如果您的應用程式是在 .NET Framework 4.6.2 上執行，請處理 <xref:System.NullReferenceException>。 <br /> - 升級至 .NET Framework 4.7，這可以還原舊版行為並擲回 <xref:System.ArgumentNullException>。 | Edge |

<a name="Data"></a>   
## <a name="data"></a>資料  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|Azure SQL 資料庫的連接集區封鎖期|針對已知 Azure SQL 資料庫的連線開啟要求，移除連接集區封鎖期間。|發生暫時性連線錯誤之後，幾乎會立即嘗試重試連線開啟要求。 如需詳細資訊，請參閱[風險降低︰集區封鎖期](~/docs/framework/migration-guide/mitigation-pool-blocking-period.md)。|次要|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName> <br /> <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName>|當使用 NetTcp 搭配傳輸安全性和憑證類型的認證時，SSL 3 通訊協定已不再是用來交涉安全連接的預設通訊協定。|在大部分情況下，應該不會影響現有的應用程式，因為 TLS 1.0 總是包含在 NetTcp 的通訊協定清單中。 所有現有的用戶端應該能夠使用至少 TLS 1.0 來交涉連接。<br /><br /> 如果需要 SSL3，您可以使用下列組態機制之一，將 SSL3 加入交涉通訊協定的清單：<br /><br /> -   <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=fullName> 屬性<br />-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName> 屬性<br />-   [\<netTcpBinding>](~/docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) 的 [\<transport>](~/docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md) 區段<br />-   [\<customBinding>](~/docs/framework/configure-apps/file-schema/wcf/custombinding.md) 的 [\<sslStreamSecurity>](~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) 區段|Edge|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Controls.TextBlock> 控制項之父代的 `IsEnabled` 屬性|從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，變更 <xref:System.Windows.Controls.TextBlock> 控制項之父代的 `IsEnabled` 屬性，會影響 <xref:System.Windows.Controls.TextBlock> 控制項的任何子控制項 (例如超連結和按鈕)。<br /><br /> 在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和更早版本的 .NET Framework 中，<xref:System.Windows.Controls.TextBlock> 內的控制項不一定會反映出 <xref:System.Windows.Controls.TextBlock> 父代的 `IsEnabled` 屬性狀態。|這項變更符合 <xref:System.Windows.Controls.TextBlock> 控制項內的之控制項的預期行為。|次要|  
|水平捲動、虛擬化和 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName>|和主要捲動方向呈正交方向執行自身虛擬化的 <xref:System.Windows.Controls.ItemsControl> 之捲動作業的行為已變更。|此變更會為使用者產生更為可預測且直覺式的體驗，但它會影響依賴 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> 於水平捲動後之確切值的所有應用程式。 如需詳細資訊，請參閱[風險降低：水平捲動和虛擬化](~/docs/framework/migration-guide/mitigation-horizontal-scrolling-and-virtualization.md)。|次要|  
|WPF 拼字檢查程式 (<xref:System.Windows.Controls.SpellCheck?displayProperty=fullName> 類別)|在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 下執行時注意到的三個 WPF 拼字檢查問題已在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中解決：<br /><br /> -   在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，叫用 [ISpellChecker (英文)](https://msdn.microsoft.com/library/windows/desktop/hh869767\(v=vs.85\).aspx) 或 [ISpellCheckerFactory (英文)](https://msdn.microsoft.com/library/windows/desktop/hh869770\(v=vs.85\).aspx) 方法時，拼字檢查工具有時會擲回 <xref:System.Runtime.InteropServices.COMException>。 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，已經排除這些例外狀況。<br />-   在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，拼字檢查工具會誤將複合字識別為拼字錯誤，例如德文中的 "Hausnummer"。 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，拼字檢查工具可正確處理複合字。<br />-   在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，使用 [以不同的使用者身分執行] 來啟動應用程式時，拼字檢查工具會擲回 <xref:System.UnauthorizedAccessException>。 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，不支援這種情況並會以無訊息模式停用拼字檢查工具。|這些變更增強拼字檢查工具的加強性。  除非應用程式程式碼倚賴擲回的例外狀況，否則對應用程式不會造成不良影響。|Edge|  
| [DataGridCellsPanel.BringIndexIntoView](xref:System.Windows.Controls.DataGridCellsPanel.BringIndexInfoView(System.Int32)) 方法 | 在.NET Framework 4.6.2 中，啟用資料行虛擬化，但尚未決定資料行寬度時，**BringIndexIntoView** 方法會以非同步方式執行。 不過，如果資料行在非同步作業完成之前遭到移除，會發生 [ArgumentOutOfRangeException](xref:System.ArgumentOutOfRangeException)。<br/></br>從 .NET Framework 4.7 開始，這種情況不會再擲回例外狀況。 | 您可以執行下列任何動作以防止發生例外狀況： <br/> - 升級至 .NET Framework 4.7。 <br/> 1 為 .NET Framework 4.6.2 安裝最新的服務修補程式。 <br/> - 在 [DataGrid.ScrollIntoView](xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object))方法的非同步回應完成之前，避免移除資料行。 | Edge | 
  
<a name="XML"></a>   
## <a name="signed-xml-verification-requirements"></a>已簽署的 XML 驗證需求  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> 和 <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName>|已停用外部資源載入，並會將模稜兩可的目標視為無效。|在許多情況下都會擲回例外狀況，包括：<br /><br /> -   根據 id 屬性識別元素並使用相同的識別碼定義第二個元素。<br />-   定義不是合法 `NCName` 值的識別碼。<br />-   參考外部 URI。<br /><br /> 針對下列的文件，<xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A?displayProperty=fullName> 一律會傳回 `false`：<br /><br /> -   使用 XPath 參考轉換。<br />-   使用 XSLT 參考轉換。<br /><br /> 開發人員應檢閱 <xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=fullName> 和 <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>，以及衍生自 <xref:System.Security.Cryptography.Xml.Transform?displayProperty=fullName> 之類型的使用方式，因為文件收件者可能無法處理它。<br /><br /> 如需詳細資訊，請參閱[套用安全性更新 3141780 之後，.NET Framework 應用程式在處理包含 SignedXml 的檔案時遇到例外狀況錯誤或意外錯誤](https://support.microsoft.com/en-us/kb/3148821)。|次要|  
  
## <a name="see-also"></a>另請參閱  
 [4.6.2 中的應用程式相容性](~/docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
