---
title: "WIF 3.5 和 WIF 4.5 之間的命名空間對應 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# WIF 3.5 和 WIF 4.5 之間的命名空間對應
從 .NET Framework 4.5 開始， Windows 識別基礎 \(WIF\) 完全整合了 .NET Framework。  這項整合可讓已變更和 WIF 命名空間和 API 介面的某些彙總。  本主題提供某些指引與一個永遠圖表 WIF 3.5 命名空間和 WIF 4.5 命名空間之間。  中不是要詳盡，，而是提供陣列的一般資訊、尋找 WIF 4.5 的常見 WIF 3.5 類別。  如需在 WIF WIF 3.5 和 4.5 之間差異的詳細資訊，請參閱 [Windows Identity Foundation 4.5 的新功能](../../../docs/framework/security/whats-new-in-wif.md)。  如需的相關指引移轉使用 WIF 3.5 到 WIF 所建置的應用程式 4.5，請參閱 [將使用 WIF 3.5 建置的應用程式移轉至 WIF 4.5 的方針](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)。  
  
## WIF WIF 3.5 至 4.5 命名空間對應。  
 WIF 類別，收集在 WIF 3.5 的 `Microsoft.IdentityModel` 命名空間中，以下列命名空間中出現在發出: `System.Security.Claims`、 `System.ServiceModel.Security`和 `System.IdentityModel` 命名空間在 WIF 4.5。  另外 \+ 某一 WIF 3.5 命名空間在 WIF 4.5 合併後或完全拒絕。  
  
> [!IMPORTANT]
>  下列 `System.IdentityModel` 命名空間包含實作 WCF 根據要求的識別模型的類別: <xref:System.IdentityModel.Claims?displayProperty=fullName>、 <xref:System.IdentityModel.Policy?displayProperty=fullName>和 <xref:System.IdentityModel.Selectors?displayProperty=fullName>。  WCF 根據要求的識別 20 世紀 WIF 替換。  表示建立根據 WIF 時，的方案在這三個命名空間不應該使用類別。  
  
 下表提供的 WIF 3.5 類別可以在 WIF 4.5 找到的資訊。  
  
||||  
|-|-|-|  
|**WIF 3.5 命名空間**|**WIF 4.5 命名空間**|**註解**|  
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=fullName>|-   表示常數的大部分類別沒有實作。<br />-   用來建立安全性權杖服務的類別從 `Microsoft.IdentityModel.SecurityTokenService` 已經移至 <xref:System.IdentityModel?displayProperty=fullName>。<br />-   在 `Microsoft.IdentityModel.Threading` 的類別移動到 <xref:System.IdentityModel?displayProperty=fullName>。<br />-   `ExceptionMapper` 和 `MruSecurityTokenCache` 類別沒有實作。|  
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=fullName>|-   `IClaimsPrincipal` 和 `IClaimsIdentity` 介面在 WIF 4.5 未實作。  相反地 <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName> 和 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> 現在是大部分 .NET Principal 和 Identity 類別衍生的基底類別。  這表示對於特定要求 Principal 和 Identity 類別的需求。 `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` 和 `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` WIF 在 4.5 中，使用 <xref:System.Security.Principal.WindowsPrincipal?displayProperty=fullName> 和 <xref:System.Security.Principal.WindowsIdentity?displayProperty=fullName> 。  對於其他存在於 WIF 3.5 的其他特定要求 Principal 和 Identity 類別的。<br />-   `Microsoft.IdentityModel.Claims.ClaimsCollection` 類別在 WIF 4.5 未實作。  相反地，要求的集合公開為型別 <xref:System.Security.Claims.Claim?displayProperty=fullName>的可列舉集合。<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName> 和 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> 提供完整現在支援 LINQ 的方法。|  
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=fullName>|陣列元素和類別所執行的變更，而另一些則 WIF 4.5 拒絕;例如 `Microsoft.IdentityModel.Configuraiton.ServiceConfiguration` 現在是 <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=fullName>。|  
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Protocols.WSIdentity`|未實作於 WIF 4.5|在 WIF 3.5 包含類別支援， CardSpace 未實作於 WIF 4.5。|  
|`Microsoft.IdentityModel.Protocols.WSTrust`|在 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName> 和 <xref:System.ServiceModel.Security?displayProperty=fullName> 命名空間之間加以劃分。|表示 WS\-Security 信任成品的類別在 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName> 命名空間;例如， <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> 類別。  表示 WCF 服務合約、服務主機和通道使 WCF 服務通訊 WS\-Security 信任通訊協定的類別在 <xref:System.ServiceModel.Security?displayProperty=fullName> 命名空間;例如， <xref:System.ServiceModel.Security.WSTrustServiceHost> 類別。|  
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|未實作於 WIF 4.5|\-|  
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|未實作於 WIF 4.5|表示 XML 加密中 WIF 3.5 的常數所包含的類別。  這些常數在 WIF 4.5 未實作。|  
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=fullName>|表示常數的 `EnvelopingSignature` 類別和類別沒有實作。|  
|`Microsoft.IdentityModel.SecurityTokenService`|若要分割 <xref:System.IdentityModel?displayProperty=fullName>、 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName>和 <xref:System.IdentityModel.Tokens?displayProperty=fullName> 命名空間之間。|\-|  
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>|針對現有類別 \(WS\-Security \(W3C\)\) 案例提供設定主要已經移至 <xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>;不過，其中有些類別在 <xref:System.IdentityModel.Services?displayProperty=fullName>。|  
|`Microsoft.IdentityModel.Web.Controls`|未實作於 WIF 4.5|在 `Microsoft.IdentityModel.Web.Controls` 的類別實作了 \(W3C\) 的被動登入控制項，不存在於 WIF 4.5。|  
|`Microsoft.IdentityModel.WindowsTokenService`|未實作於 WIF 4.5|\-|  
  
## 請參閱  
 [Windows Identity Foundation 4.5 的新功能](../../../docs/framework/security/whats-new-in-wif.md)   
 [將使用 WIF 3.5 建置的應用程式移轉至 WIF 4.5 的方針](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)