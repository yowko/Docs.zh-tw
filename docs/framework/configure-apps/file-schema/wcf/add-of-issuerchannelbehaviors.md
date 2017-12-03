---
title: "&lt;issuerChannelBehaviors&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ea76a96597796b10c97ea57ca38c3bda453468c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a>&lt;issuerChannelBehaviors&gt; 的 &lt;add&gt;
新增與 STS 通訊時要使用的端點行為。  
  
> [!NOTE]
>  如果任何端點行為包含[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目，將會擲回例外狀況。  
  
 \<系統。ServiceModel >  
\<行為 >  
endpointBehaviors 區段  
\<行為 >  
\<clientCredentials >  
\<issuedToken >  
\<h > 項目  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|issuerAddress|要與其進行通訊之安全性權杖簽發者的 URI。|  
|behaviorConfiguration|相同組態檔中定義之端點行為的名稱。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<h >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|包含要在與指定安全性權杖服務通訊時使用的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 用戶端端點行為集合。|  
  
## <a name="remarks"></a>備註  
 `issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。 `behaviorConfiguration` 會指向端點行為，而應用程式會在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 建立的通道中使用該行為取得 Security Token Service 發出的權杖。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [同盟與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [保護服務和用戶端](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [保護用戶端安全](../../../../../docs/framework/wcf/securing-clients.md)  
 [如何： 建立聯合用戶端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [如何： 設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [同盟與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [\<h >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
