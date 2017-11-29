---
title: "&lt;issuerChannelBehaviors&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 051525738f0138955358587a8fd25272dfdb9d28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuerchannelbehaviorsgt-element"></a>&lt;issuerChannelBehaviors&gt; 項目
包含 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 用戶端端點行為 (於組態中定義) 的集合，與指定的服務權杖服務通訊時，會使用此行為。 已定義的行為不能包含任何[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目。  
  
 \<系統。ServiceModel >  
\<行為 >  
endpointBehaviors 區段  
\<行為 >  
\<clientCredentials >  
\<issuedToken >  
\<h >  
  
## <a name="syntax"></a>語法  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|將行為新增至集合中。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|指定用來向服務驗證用戶端的自訂權杖。|  
  
## <a name="remarks"></a>備註  
 當在必須使用任何行為 (包含 `<clientCredentials>` 項目之行為以外的任何行為) 與服務進行通訊時，請使用此項目。 例如，如果[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)行為項目必須包含。  
  
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
