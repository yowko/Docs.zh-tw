---
title: ".NET Framework 4.6 中的執行階段變更 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6
- application compatibility
ms.assetid: 5262bcfa-6e48-416b-8972-69cb4002d386
caps.latest.revision: 34
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 77002c3d1b6553156c225b3efba9a2f29009915a
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-46"></a>.NET Framework 4.6 中的執行階段變更
在某些罕見的情況下，執行階段變更可能會影響以舊版 .NET Framework 為目標，但在新版 .NET Framework 執行階段上執行的現有應用程式。 這些變更也包含在不同的 .NET Framework 執行階段環境中執行之應用程式間的行為差異。 其中包含下列區域的變更：  
  
-   [核心](#Core)  
  
-   [Data](#Data)  
  
-   [網路](#Networking)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [安裝和部署](#Setup)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [新的 64 位元 JIT 編譯器](#RyuJIT)  
  
<a name="Core"></a>   
## <a name="core"></a>核心  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|從 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 開始，<xref:System.Globalization.PersianCalendar> 類別會使用回教陽曆演算法。|回教陽曆演算法所產生的結果，與伊朗和阿富汗目前使用的波斯曆相同。 針對西曆 1800 到 2023 年的日期，它也會產生與先前的演算法相同的結果。 如果使用 <xref:System.Globalization.PersianCalendar> 類別執行日期轉換 (例如在西曆中的日期與波斯曆中的日期之間執行轉換)，或判斷特定年份是否為閏年，則可能會影響超出該範圍的日期。<br /><br /> 由於這項變更，已安裝 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 之系統的 <xref:System.Globalization.PersianCalendar.MinSupportedDateTime%2A?displayProperty=fullName> 屬性值已從 March 21, 0622 變更為 March 22, 0622。<br /><br /> 如需詳細資訊，請參閱 <xref:System.Globalization.PersianCalendar> 主題。|次要|  
|<xref:System.Runtime.Versioning.TargetFrameworkAttribute>|針對預設應用程式定義域，除非將名稱指派給 <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> 屬性來明確定義，否則 <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> 屬性的值會衍生自 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> (如果存在的話)。  在舊版 .NET Framework 中，<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> 屬性的值為 `null`，除非是執行一些特殊程式碼路徑，或建立非預設應用程式定義域時，未在 <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> 屬性中明確指定其目標架構。<br /><br /> 針對非預設應用程式定義域，決定 <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> 屬性值的方式不會有任何變更。 如果未明確指派值給 <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> 屬性，非預設應用程式定義域會從預設應用程式定義域繼承目標架構。|針對預設應用程式定義域，<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> 可能會傳回非 Null 值 (先前傳回 `null`)。 這是所需的行為。|Edge|  
|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|如果系統上有任何已安裝的憑證不受 .NET Framework 支援，將 `True` 值傳遞給 `verbose` 引數會傳回有效的字串。 在舊版 .NET Framework 中，嘗試於某些情況下存取不支援之憑證的公開金鑰資訊會擲回例外狀況。|這個方法僅供參考；相關文件指出不同 .NET Framework 版本的輸出可能不一致。 這項變更只會影響呼叫 `ToString(True)` 方法，並已安裝不受 .NET Framework 支援之憑證的應用程式。 藉由傳回字串 (而不是擲回例外狀況)，這項變更會讓方法更穩固。|Edge|  
|Event Tracing for Windows (ETW) - Windows 事件追蹤 (ETW)|在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 和 4.6.1 中，當兩個事件名稱的差異只在 "Start" 或 "Stop" 後置字元時 (例如當一個事件的名稱為 `LogUser` 而另一個事件的名稱為 `LogUserStart` 時)，執行階段會擲回 <xref:System.ArgumentException>。 在此情況下，執行階段無法建構事件來源，因此無法發出任何記錄。|請確定兩個事件名稱不能只有 "Start" 或 "Stop" 後置字元不同。<br /><br /> 從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，已移除這項需求；執行階段可以釐清只有 "Start" 後置字元不同的事件名稱。|Edge|  
|反映和分散式 COM (DCOM)|無法再將反映物件從 Managed 程式碼傳遞至跨處理序的 DCOM 用戶端。 下列類型會受到影響︰<xref:System.Reflection.Assembly>；<xref:System.Reflection.MemberInfo> 和其衍生類型，包括 <xref:System.Reflection.FieldInfo>、<xref:System.Reflection.MethodInfo>、<xref:System.Type> 和 <xref:System.Reflection.TypeInfo>；<xref:System.Reflection.MethodBody>；<xref:System.Reflection.Module>；以及 <xref:System.Reflection.ParameterInfo>。|呼叫物件的 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707.aspx) 會傳回 `E_NOINTERFACE`。|次要|  
  
<a name="Data"></a>   
## <a name="data"></a>資料  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|解析為 `localhost` 之 SQL Server 資料庫的 TCP/IP 連線|從 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 開始，連線嘗試會失敗，錯誤為：「建立連線至 SQL Server 時，發生網路相關或執行個體特定的錯誤。 找不到或無法存取伺服器。 確認執行個名稱是否正確，以及 SQL Server 是否設定為允許遠端連線 (提供者: SQL 網路錯誤，錯誤: 26 - 搜尋指定的伺服器/執行個體時發生錯誤)」。|在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中已解決此問題，並還原舊版行為。 若要連線到解析為 `localhost` 的 SQL Server 資料庫，請升級至 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]。|次要|  
  
<a name="Networking"></a>   
## <a name="networking"></a>網路  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> 類別中的日期和時間值。|為了符合 [RFC822](http://www.ietf.org/rfc/rfc0822.txt) 和 [RFC2822](http://www.ietf.org/rfc/rfc2822.txt) 標準，格式化日期和時間值現在採用兩位數小時。 之前，上午 10:00 前的值會以單一位數小時來表示。|這項變更會影響下列使用案例：<br /><br /> -   在不同的 .NET Framework 版本之間，比較序列化 <xref:System.Net.Mime.ContentDisposition> 物件的長度或雜湊碼。<br />-   在不同的 .NET Framework 版本之間，比較 <xref:System.Net.Mime.ContentDisposition.ToString%2A> 方法的傳回值或 <xref:System.Net.Mime.ContentDisposition> 日期和時間屬性值的字串表示。|次要|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|使用 NETTCP 進行 SSL 安全性和憑證驗證的 WCF 服務|.NET Framework 4.6 新增了 TLS 1.1 和 TLS 1.2 至 WCF SSL 的預設通訊協定清單。 當用戶端和伺服器電腦安裝 .NET Framework 4.6 或更新版本時，會使用 TLS 1.2 進行交涉。|TLS 1.2 不支援 MD5 憑證驗證。 因此，如果客戶使用 MD5 憑證，WCF 用戶端將無法連線到 WCF 服務。 如需詳細資訊，請參閱[風險降低︰WCF 服務和憑證驗證](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md)。|次要|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|多重監視器案例中的視窗呈現|在多重監視器案例中，當視窗超出顯示畫面之外，仍會呈現完整的視窗而不會予以裁剪。|請參閱[風險降低：WPF 視窗呈現](../../../docs/framework/migration-guide/mitigation-wpf-window-rendering.md)。|次要|  
|啟用 WPF 文字之控制項的拼字檢查|因為只有輸入語言清單上的語言可以使用平台拼字檢查功能，所以拼字檢查工具在 Windows 10 上可能無法運作。|在 Windows 10 中，當將語言加入可用鍵盤的清單時，Windows 會自動下載並安裝對應的 Feature on Demand (FOD) 套件，以提供拼字檢查功能。 只要將語言加入輸入語言清單中，就可支援拼字檢查工具。|次要|  
  
<a name="Setup"></a>   
## <a name="setup-and-deployment"></a>安裝和部署  
  
|特殊功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|產品版本|舊版 .NET Framework (特別是 .NET Framework 4、4.5、4.5.1 和 4.5.2) 的產品版本已變更。 如需詳細資訊，請參閱[風險降低：產品版本](../../../docs/framework/migration-guide/mitigation-product-versioning.md)。|請參閱[風險降低：產品版本](../../../docs/framework/migration-guide/mitigation-product-versioning.md)。|Medium|  
  
<a name="ClickOnce"></a>   
## <a name="clickonce"></a>ClickOnce  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|透過 ClickOnce 發行的應用程式，這些應用程式使用 SHA-256 程式碼簽署憑證。|以 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] (含) 以前版本為目標並已使用 SHA-256 憑證簽署的 ClickOnce 應用程式，不再具有 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] (含) 以後版本的執行階段相依性。|之前，使用 SHA-256 憑證簽署以 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] (含) 以前版本為目標的 ClickOnce 應用程式要求目標系統上必須有 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] (含) 以後版本。 如果沒有，則會發生錯誤。 這項變更移除了該相依性，並允許使用 SHA-256 憑證來簽署以 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] (含) 以前版本為目標的 ClickOnce 應用程式。|次要|  
  
<a name="RyuJIT"></a>   
## <a name="the-new-64-bit-jit-compiler"></a>新的 64 位元 JIT 編譯器  
  
|特殊功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|64 位元 JIT 編譯|從 .NET Framework 4.6 開始，使用新的 64 位元 JIT 編譯器來進行 Just-In-Time 編譯。 這項變更不會影響 32 位元 JIT 編譯器。|在某些情況下，如果使用 32 位元編譯器或舊版 64 位元 JIT 編譯器來執行應用程式，則會擲回非預期的例外狀況或遵守不同的行為。 **注意︰**上述所有問題都已在隨 .NET Framework 4.6.2 發行的新版 64 位元編譯器中解決。 大部分問題已在隨附於 Windows Update 的 .NET Framework 4.6 和 4.6.1 服務版本中解決。 <br /><br /> 如需詳細資訊，請參閱[風險降低：新的 64 位元 JIT 編譯器](../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)。|Edge|  
|例外狀況處理 (從 `try` 區域傳回)|不同於舊版 JIT64 Just-In-Time 編譯器，新版 64 位元 JIT 編譯器不允許在 `try` 區域中使用 IL `ret` 指令。|ECMA 335 規格不允許從 `try` 區域傳回，而且不會有已知的 Managed 編譯器產生這類 IL。 不過，如果這類 IL 是由反映發出所產生，則 JIT64 編譯器將會執行這類 IL。<br /><br /> 如果您的應用程式所產生的 IL 會在 `try` 區域中包含 `ret` 作業碼，您可以：<br /><br /> -   將目標設為 .NET Framework 4.5，或將 [\<useLegacyJIT>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) 項目新增至應用程式組態檔，以使用舊版 JIT 編譯器並避免這項變更。<br />-   更新所產生的 IL，以在 `try` 區域之後傳回。<br />-|Edge|
