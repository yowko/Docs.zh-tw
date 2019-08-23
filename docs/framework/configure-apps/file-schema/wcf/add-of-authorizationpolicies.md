---
title: <add> 的 <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 65398c5afa9750f215c95899bb6004cae671123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920267"
---
# <a name="add-of-authorizationpolicies"></a>\<新增 authorizationPolicies > \<的 >
指定用於宣告轉換的驗證原則。  
  
 \<system.ServiceModel>  
\<行為 >  
\<行為 >  
\<serviceAuthorization>  
\<authorizationPolicies>  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`policyType`|必要的字串屬性。<br /><br /> Windows Communication Foundation (WCF) 存取控制模型支援提供一組授權原則做為類型。 此屬性會指定授權原則，可將一組輸入宣告轉換為另一組宣告。 它可以做為授與或拒絕存取控制 (Access Control) 的基礎。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|指定授權原則型別的集合。|  
  
## <a name="remarks"></a>備註  
 每個授權原則包含一個必要的 `policyType` 屬性字串。 該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。 它可以做為授與或拒絕存取控制 (Access Control) 的基礎。 如需授權原則運作方式的詳細資訊, 請<xref:System.IdentityModel.Policy.IAuthorizationPolicy>參閱和[授權原則](../../../wcf/samples/authorization-policy.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [授權存取服務作業](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [如何：為服務建立自訂授權管理員](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [授權原則](../../../wcf/samples/authorization-policy.md)
