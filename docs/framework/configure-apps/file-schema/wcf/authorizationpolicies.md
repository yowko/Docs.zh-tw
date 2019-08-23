---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 38d123a53b344ff1e4d781115093d0d1de5ae679
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926453"
---
# <a name="authorizationpolicies"></a><span data-ttu-id="aefb7-101">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="aefb7-101">\<authorizationPolicies></span></span>
<span data-ttu-id="aefb7-102">這個組態區段包含授權原則型別的集合，使用 `add` 關鍵字可加入這些型別。</span><span class="sxs-lookup"><span data-stu-id="aefb7-102">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="aefb7-103">每個授權原則包含一個必要的 `policyType` 屬性字串。</span><span class="sxs-lookup"><span data-stu-id="aefb7-103">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="aefb7-104">該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="aefb7-104">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="aefb7-105">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="aefb7-105">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="aefb7-106">如需授權原則運作方式的詳細資訊, 請<xref:System.IdentityModel.Policy.IAuthorizationPolicy>參閱和[授權原則](../../../wcf/samples/authorization-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="aefb7-106">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefb7-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aefb7-107">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="aefb7-108">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="aefb7-108">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="aefb7-109">如何：為服務建立自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="aefb7-109">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="aefb7-110">\<add></span><span class="sxs-lookup"><span data-stu-id="aefb7-110">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="aefb7-111">授權原則</span><span class="sxs-lookup"><span data-stu-id="aefb7-111">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
