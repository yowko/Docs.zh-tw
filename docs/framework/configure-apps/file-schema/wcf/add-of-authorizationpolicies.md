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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72af0529cea2e6810bdb7a518874a313e3ceab40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="b638d-102">&lt;authorizationPolicies&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="b638d-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="b638d-103">指定用於宣告轉換的驗證原則。</span><span class="sxs-lookup"><span data-stu-id="b638d-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="b638d-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b638d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b638d-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="b638d-105">\<behaviors></span></span>  
<span data-ttu-id="b638d-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="b638d-106">\<behavior></span></span>  
<span data-ttu-id="b638d-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="b638d-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="b638d-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="b638d-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="b638d-109">\<add></span><span class="sxs-lookup"><span data-stu-id="b638d-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b638d-110">語法</span><span class="sxs-lookup"><span data-stu-id="b638d-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="b638d-111">類型</span><span class="sxs-lookup"><span data-stu-id="b638d-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b638d-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b638d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b638d-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b638d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b638d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b638d-114">Attributes</span></span>  
  
|<span data-ttu-id="b638d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b638d-115">Attribute</span></span>|<span data-ttu-id="b638d-116">描述</span><span class="sxs-lookup"><span data-stu-id="b638d-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="b638d-117">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="b638d-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="b638d-118">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 存取控制模型支援提供一組授權原則做為型別。</span><span class="sxs-lookup"><span data-stu-id="b638d-118">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="b638d-119">此屬性會指定授權原則，可將一組輸入宣告轉換為另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="b638d-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="b638d-120">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="b638d-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b638d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="b638d-121">Child Elements</span></span>  
 <span data-ttu-id="b638d-122">無。</span><span class="sxs-lookup"><span data-stu-id="b638d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b638d-123">父項目</span><span class="sxs-lookup"><span data-stu-id="b638d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b638d-124">項目</span><span class="sxs-lookup"><span data-stu-id="b638d-124">Element</span></span>|<span data-ttu-id="b638d-125">描述</span><span class="sxs-lookup"><span data-stu-id="b638d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b638d-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="b638d-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="b638d-127">指定授權原則型別的集合。</span><span class="sxs-lookup"><span data-stu-id="b638d-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b638d-128">備註</span><span class="sxs-lookup"><span data-stu-id="b638d-128">Remarks</span></span>  
 <span data-ttu-id="b638d-129">每個授權原則包含一個必要的 `policyType` 屬性字串。</span><span class="sxs-lookup"><span data-stu-id="b638d-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="b638d-130">該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="b638d-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="b638d-131">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="b638d-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="b638d-132">如需有關授權原則的運作方式的詳細資訊，請參閱<xref:System.IdentityModel.Policy.IAuthorizationPolicy>和[授權原則](../../../../../docs/framework/wcf/samples/authorization-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="b638d-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b638d-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="b638d-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="b638d-134">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="b638d-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="b638d-135">如何：為服務建立自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="b638d-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="b638d-136">\<add></span><span class="sxs-lookup"><span data-stu-id="b638d-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="b638d-137">授權原則</span><span class="sxs-lookup"><span data-stu-id="b638d-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
