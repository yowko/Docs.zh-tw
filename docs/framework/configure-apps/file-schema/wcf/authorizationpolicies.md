---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 7d8eb27b8a569b1ca6b65a7c8c70c6fb82f701a4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201573"
---
# \<authorizationPolicies>

這個組態區段包含授權原則型別的集合，使用 `add` 關鍵字可加入這些型別。 每個授權原則包含一個必要的 `policyType` 屬性字串。 該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。 它可以做為授與或拒絕存取控制 (Access Control) 的基礎。 如需授權原則運作方式的詳細資訊，請參閱 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 和 [授權原則](../../../wcf/samples/authorization-policy.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [授權存取服務作業](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [作法：為服務建立自訂授權管理員](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [授權原則](../../../wcf/samples/authorization-policy.md)
