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
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="6628d-102">\<新增 authorizationPolicies > \<的 ></span><span class="sxs-lookup"><span data-stu-id="6628d-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="6628d-103">指定用於宣告轉換的驗證原則。</span><span class="sxs-lookup"><span data-stu-id="6628d-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="6628d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6628d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6628d-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="6628d-105">\<behaviors></span></span>  
<span data-ttu-id="6628d-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="6628d-106">\<behavior></span></span>  
<span data-ttu-id="6628d-107">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="6628d-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="6628d-108">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="6628d-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="6628d-109">\<add></span><span class="sxs-lookup"><span data-stu-id="6628d-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6628d-110">語法</span><span class="sxs-lookup"><span data-stu-id="6628d-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="6628d-111">類型</span><span class="sxs-lookup"><span data-stu-id="6628d-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6628d-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6628d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6628d-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6628d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6628d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="6628d-114">Attributes</span></span>  
  
|<span data-ttu-id="6628d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="6628d-115">Attribute</span></span>|<span data-ttu-id="6628d-116">說明</span><span class="sxs-lookup"><span data-stu-id="6628d-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="6628d-117">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="6628d-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="6628d-118">Windows Communication Foundation (WCF) 存取控制模型支援提供一組授權原則做為類型。</span><span class="sxs-lookup"><span data-stu-id="6628d-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="6628d-119">此屬性會指定授權原則，可將一組輸入宣告轉換為另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="6628d-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="6628d-120">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="6628d-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6628d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="6628d-121">Child Elements</span></span>  
 <span data-ttu-id="6628d-122">無。</span><span class="sxs-lookup"><span data-stu-id="6628d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6628d-123">父項目</span><span class="sxs-lookup"><span data-stu-id="6628d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6628d-124">項目</span><span class="sxs-lookup"><span data-stu-id="6628d-124">Element</span></span>|<span data-ttu-id="6628d-125">說明</span><span class="sxs-lookup"><span data-stu-id="6628d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6628d-126">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="6628d-126">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="6628d-127">指定授權原則型別的集合。</span><span class="sxs-lookup"><span data-stu-id="6628d-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6628d-128">備註</span><span class="sxs-lookup"><span data-stu-id="6628d-128">Remarks</span></span>  
 <span data-ttu-id="6628d-129">每個授權原則包含一個必要的 `policyType` 屬性字串。</span><span class="sxs-lookup"><span data-stu-id="6628d-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="6628d-130">該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="6628d-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="6628d-131">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="6628d-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="6628d-132">如需授權原則運作方式的詳細資訊, 請<xref:System.IdentityModel.Policy.IAuthorizationPolicy>參閱和[授權原則](../../../wcf/samples/authorization-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="6628d-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6628d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6628d-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="6628d-134">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="6628d-134">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="6628d-135">如何：為服務建立自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="6628d-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="6628d-136">\<add></span><span class="sxs-lookup"><span data-stu-id="6628d-136">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="6628d-137">授權原則</span><span class="sxs-lookup"><span data-stu-id="6628d-137">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
