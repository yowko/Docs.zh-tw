---
title: ".NET Framework 4.6.2 中的重定目標變更 | Microsoft Docs"
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
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6.2
- application compatibility
ms.assetid: 76dc6849-8210-4e41-8731-20828c98b282
caps.latest.revision: 26
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 229ccf3fa4ff1029334641da350cfd040e4b286e
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="retargeting-changes-in-the-net-framework-462"></a>.NET Framework 4.6.2 中的重定目標變更
在某些罕見的情況下，重定目標變更可能會影響以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標來重新編譯的應用程式。 這些變更不會影響以舊版 .NET Framework 為目標但在 4.6.2 版下執行的二進位檔。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 包含下列區域的重定目標變更：  
  
-   [核心](#Core)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Forms](#WinForms)  
  
 下表中的 [範圍] 一欄指定每項變更的重要性：  
  
-   主要。 影響大量應用程式或需要大幅修改程式碼的重大變更。 請注意，重定目標變更不屬於此分類。  
  
-   次要。 影響少量應用程式或需要稍微修改程式碼的變更。  
  
-   邊緣。 在非常特定 (罕見) 的情況下影響應用程式的變更。  
  
-   透明。 此變更對應用程式的開發人員或使用者的影響不明顯。 發生此變更的應用程式應該不需要修改。  
  
<a name="Core"></a>   
## <a name="core"></a>核心  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|長路徑支援|從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，可支援長路徑 (最多 32K 字元)，並已移除 260 個字元 (或 `MAX_PATH`) 的路徑長度限制。|對於以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式，先前會擲回 <xref:System.IO.PathTooLongException> 的程式碼路徑不再擲回例外狀況。 如需詳細資訊，請參閱[風險降低：長路徑支援](~/docs/framework/migration-guide/mitigation-long-path-support.md)。|次要|  
|路徑正規化|從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，已變更正規畫路徑的方式，以延後至作業系統並提供更好的方式讓您存取 DOS 裝置路徑。|這項變更能夠存取先前不支援的有效裝置路徑。 如需詳細資訊，請參閱[風險降低：路徑正規化](~/docs/framework/migration-guide/mitigation-path-normalization.md)。|次要|  
|<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> 和 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName>|從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，為了支援先前所不支援的路徑 (就長度和格式兩方面) 而有數項變更。 特別是提供更正確的適當磁碟機分隔符號語法 (冒號) 檢查。|這些變更會封鎖這兩種方法先前支援的一些 URI 路徑。 如需詳細資訊，請參閱[風險降低：路徑冒號檢查](~/docs/framework/migration-guide/mitigation-path-colon-checks.md)。|Edge|  
|<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> 建構函式|從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，藉由呼叫 <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> 方法所建立的 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> 屬性會是新的 <xref:System.Security.Claims.ClaimsIdentity> 執行個體。 在舊版的 .NET Framework 中，<xref:System.Security.Claims.ClaimsIdentity.Actor%2A> 是現有的參考。|在某些情況下，針對 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> 屬性和建構函式的 <xref:System.Security.Principal.IIdentity> 之 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> 屬性所進行的比較，會傳回不同的值。<br /><br /> 如需詳細資訊，請參閱[風險降低︰ClaimsIdentity 建構函式](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md)。|Edge|  
|<xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor%2A?displayProperty=fullName>|從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，<xref:System.Security.Cryptography.AesCryptoServiceProvider> 解密程式會提供可重複使用的轉換。   呼叫 <xref:System.Security.Cryptography.ICryptoTransform.TransformFinalBlock%2A> 之後，轉換就會重新初始化並且可重複使用。<br /><br /> 對於目標為舊版 .NET Framework 的應用程式，嘗試透過在呼叫 <xref:System.Security.Cryptography.ICryptoTransform.TransformFinalBlock%2A> 之後呼叫 <xref:System.Security.Cryptography.ICryptoTransform.TransformBlock%2A> 來重複使用解密程式，會擲回 <xref:System.Security.Cryptography.CryptographicException> 或產生損毀的資料。|由於這是預期的行為，影響應該很小。<br /><br /> 倚賴舊行為的應用程式可以選擇不使用，可以藉由將下列組態設定加入應用程式組態檔的 [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段：<br /><br /> `<runtime>    <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/> </runtime>`<br /><br /> 此外，以舊版 .NET Framework 為目標，但從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始在 .NET Framework 版本執行的應用程式，可以藉由將下列組態設定新增至應用程式組態檔的 [\<執行階段>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，來選擇使用：<br /><br /> `<runtime>    <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/> </runtime>`|次要|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|使用 CNG 儲存之憑證的 WCF 傳輸安全性支援|從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，WCF 傳輸安全性支援使用 Windows 密碼編譯程式庫 (CNG) 儲存的憑證。 這項支援僅限於具有公開金鑰的憑證，且指數長度不能超過 32 位元。 當應用程式以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標時，這項功能預設為開啟。<br /><br /> 在舊版 .NET Framework 中，嘗試搭配 CSG 金鑰儲存提供者使用 X509 憑證會擲回例外狀況。|應用程式是以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和舊版為目標，但卻執行於 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 當中，則可將下列這一行加入 app.config 或 web.config 檔的 runtime 區段，來啟用支援 CNG 憑證。<br /><br /> `<AppContextSwitchOverrides     value="Switch.System.ServiceModel.DisableCngCertificates=false" />`<br /><br /> 這也可以用程式設計方式，以下列程式碼完成︰<br /><br /> `private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate"; AppContext.SetSwitch(disableCngCertificates, false);`<br /><br /> `Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates" AppContext.SetSwitch(disableCngCertificates, False)`<br /><br /> 請注意，由於這項變更，將不再執行任何倚賴使用 CNG 憑證嘗試起始安全通訊失敗的任何例外住況處理程式碼。|次要|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows Form  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName>、`System.ComponentModel.EventDescriptor.Equals` 和 `System.ComponentModel.PropertyDescriptor.Equals`|從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，基底類別 <xref:System.ComponentModel.MemberDescriptor.Equals%2A> 方法的實作已經變更。|由於相等測試現在會產生預期的結果，這項變更應該不會造成太大影響。<br /><br /> 不過，以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標和倚賴先前行為的應用程式可以選擇不使用這項變更。 同樣地，以舊版 .NET Framework 為目標，但在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 下執行的應用程式，可以選擇使用這項變更。 如需詳細資訊，請參閱[風險降低：MemberDescriptor.Equals](~/docs/framework/migration-guide/mitigation-memberdescriptor-equals.md)。|Edge|  
  
## <a name="see-also"></a>另請參閱  
 [4.6.2 中的應用程式相容性](~/docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
