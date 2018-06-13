---
title: WIF 3.5 和 WIF 4.5 之間的命名空間對應
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a120347d20de5b881ccb60d03da482856d9e68a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407978"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>WIF 3.5 和 WIF 4.5 之間的命名空間對應
從 .NET 4.5 開始，Windows Identity Foundation (WIF) 已與 .NET Framework 完全整合。 這項整合已引起名稱變更以及某項 WIF 命名空間和 API 介面合併。 本主題提供某個指引以及 WIF 3.5 命名空間與 WIF 4.5 命名空間之間的一般對應。 它的目的不是要提供詳盡資訊，而是提供可在 WIF 4.5 的何處找到熟悉 WIF 3.5 類別的一些一般資訊。 如需 WIF 3.5 與 WIF 4.5 差異的詳細資訊，請參閱 [Windows Identity Foundation 4.5 的新功能](../../../docs/framework/security/whats-new-in-wif.md)。 如需如何將使用 WIF 3.5 所建置的應用程式移轉至 WIF 4.5 的指引，請參閱[將使用 WIF 3.5 建置的應用程式移轉至 WIF 4.5 的方針](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)。  
  
## <a name="wif-35-to-wif-45-namespace-map"></a>WIF 3.5 到 WIF 4.5 命名空間對應  
 在 WIF 3.5 的 `Microsoft.IdentityModel` 命名空間下收集到的 WIF 類別，現在會散發到下列命名空間：WIF 4.5 中的 `System.Security.Claims`、`System.ServiceModel.Security` 和 `System.IdentityModel` 命名空間。 此外，在 WIF 4.5 中，已合併或卸除部分 WIF 3.5 命名空間。  
  
> [!IMPORTANT]
>  下列 `System.IdentityModel` 命名空間包含的類別可實作 WCF 宣告式身分識別模型：<xref:System.IdentityModel.Claims?displayProperty=nameWithType>、<xref:System.IdentityModel.Policy?displayProperty=nameWithType> 和 <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>。 WIF 已取代 WCF 宣告式識別模型。 在建置以 WIF 為基礎的解決方案時，您不應該使用這三個命名空間中的類別。  
  
 下表提供可在 WIF 4.5 的何處找到 WIF 3.5 類別的相關資訊。  
  
|**WIF 3.5 命名空間**|**WIF 4.5 命名空間**|**註解**|  
|-|-|-|  
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|-   未實作代表常數的大部分類別。<br />-   用來建置安全性權杖服務的類別已從 `Microsoft.IdentityModel.SecurityTokenService` 移動至 <xref:System.IdentityModel?displayProperty=nameWithType>。<br />-   `Microsoft.IdentityModel.Threading` 中的類別已移至 <xref:System.IdentityModel?displayProperty=nameWithType>。<br />-   未實作 `ExceptionMapper` 和 `MruSecurityTokenCache` 類別。|  
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|-   在 WIF 4.5 中，未實作 `IClaimsPrincipal` 和 `IClaimsIdentity` 介面。 相反地，<xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> 和 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> 現在是大部分.NET 主體和身分識別類別衍生自的基底類別。 這表示不需要特殊宣告主體和身分識別類別 (例如 WIF 4.5 中的 `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` 和 `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity`)，請改成使用 <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> 和 <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType>。 這適用於 WIF 3.5 中的其他特殊宣告主體和身分識別類別。<br />-   在 WIF 4.5 中，未實作 `Microsoft.IdentityModel.Claims.ClaimsCollection` 類別。 相反地，宣告集合會公開為類型 <xref:System.Security.Claims.Claim?displayProperty=nameWithType> 的可列舉集合。<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> 和 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> 提供現在完全支援 LINQ 的方法。|  
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|一些項目和類別已進行名稱變更，一些則已在 WIF 4.5 中予以卸除；例如 `Microsoft.IdentityModel.Configuraiton.ServiceConfiguration` 現在是 <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>。|  
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSIdentity`|尚未在 WIF 4.5 中實作|在支援 CardSpace 的 WIF 3.5 包含類別中，尚未在 WIF 4.5 中實作。|  
|`Microsoft.IdentityModel.Protocols.WSTrust`|在 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> 與 <xref:System.ServiceModel.Security?displayProperty=nameWithType> 命名空間之間分割。|代表 WS-Trust 成品的類別位於 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> 命名空間中；例如，<xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> 類別。 代表可讓 WCF 服務使用 WS-Trust 通訊協定進行通訊之 WCF 服務合約、服務主機和通道的類別，位於 <xref:System.ServiceModel.Security?displayProperty=nameWithType> 命名空間中；例如，<xref:System.ServiceModel.Security.WSTrustServiceHost> 類別。|  
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|尚未在 WIF 4.5 中實作|-|  
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|尚未在 WIF 4.5 中實作|WIF 3.5 中代表 XML 加密常數的包含類別。 這些常數尚未在 WIF 4.5 中實作。|  
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|未實作 `EnvelopingSignature` 類別以及代表常數的類別。|  
|`Microsoft.IdentityModel.SecurityTokenService`|在 <xref:System.IdentityModel?displayProperty=nameWithType>、<xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> 與 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType> 命名空間之間分割。|-|  
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|提供被動 (WS-同盟) 案例組態的類別主要移至 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>；不過，其中一些類別是在 <xref:System.IdentityModel.Services?displayProperty=nameWithType> 中。|  
|`Microsoft.IdentityModel.Web.Controls`|尚未在 WIF 4.5 中實作|`Microsoft.IdentityModel.Web.Controls` 中的類別已實作同盟被動登入控制項，而這不存在於 WIF 4.5 中。|  
|`Microsoft.IdentityModel.WindowsTokenService`|尚未在 WIF 4.5 中實作|-|  
  
## <a name="see-also"></a>另請參閱  
 [Windows Identity Foundation 4.5 的新功能](../../../docs/framework/security/whats-new-in-wif.md)  
 [將使用 WIF 3.5 建置的應用程式移轉至 WIF 4.5 的方針](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
