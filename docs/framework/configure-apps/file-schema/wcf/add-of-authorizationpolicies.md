---
title: "&lt;authorizationPolicies&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d835d96c89e8b292fc2c038794aa4056fda3a095
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a>&lt;authorizationPolicies&gt; 的 &lt;add&gt;
指定用於宣告轉換的驗證原則。  
  
 \<系統。ServiceModel >  
\<行為 >  
\<行為 >  
\<serviceAuthorization >  
\<authorizationPolicies >  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`policyType`|必要的字串屬性。<br /><br /> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 存取控制模型支援提供一組授權原則做為型別。 此屬性會指定授權原則，可將一組輸入宣告轉換為另一組宣告。 它可以做為授與或拒絕存取控制 (Access Control) 的基礎。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<authorizationPolicies >](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|指定授權原則型別的集合。|  
  
## <a name="remarks"></a>備註  
 每個授權原則包含一個必要的 `policyType` 屬性字串。 該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。 它可以做為授與或拒絕存取控制 (Access Control) 的基礎。 如需有關授權原則的運作方式的詳細資訊，請參閱<xref:System.IdentityModel.Policy.IAuthorizationPolicy>和[授權原則](../../../../../docs/framework/wcf/samples/authorization-policy.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [授權存取服務作業](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [如何： 建立自訂授權管理員服務](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [授權原則](../../../../../docs/framework/wcf/samples/authorization-policy.md)
