---
title: <add> 的 <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400692"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="0ac7d-102">\<新增 authorizationPolicies > \<的 ></span><span class="sxs-lookup"><span data-stu-id="0ac7d-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="0ac7d-103">指定用於宣告轉換的驗證原則。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-103">Specifies an authorization policy for claim transformation.</span></span>  
  
<span data-ttu-id="0ac7d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ac7d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0ac7d-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0ac7d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0ac7d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0ac7d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="0ac7d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0ac7d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="0ac7d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0ac7d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="0ac7d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceAuthorization >** ](serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ac7d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)</span></span>\
<span data-ttu-id="0ac7d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authorizationPolicies >** ](authorizationpolicies.md)</span><span class="sxs-lookup"><span data-stu-id="0ac7d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)</span></span>\
<span data-ttu-id="0ac7d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="0ac7d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ac7d-112">語法</span><span class="sxs-lookup"><span data-stu-id="0ac7d-112">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="0ac7d-113">類型</span><span class="sxs-lookup"><span data-stu-id="0ac7d-113">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ac7d-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0ac7d-114">Attributes and Elements</span></span>  
 <span data-ttu-id="0ac7d-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ac7d-116">屬性</span><span class="sxs-lookup"><span data-stu-id="0ac7d-116">Attributes</span></span>  
  
|<span data-ttu-id="0ac7d-117">屬性</span><span class="sxs-lookup"><span data-stu-id="0ac7d-117">Attribute</span></span>|<span data-ttu-id="0ac7d-118">描述</span><span class="sxs-lookup"><span data-stu-id="0ac7d-118">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="0ac7d-119">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-119">A required String attribute.</span></span><br /><br /> <span data-ttu-id="0ac7d-120">Windows Communication Foundation （WCF）存取控制模型支援提供一組授權原則做為類型。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-120">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="0ac7d-121">此屬性會指定授權原則，可將一組輸入宣告轉換為另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-121">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="0ac7d-122">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-122">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ac7d-123">子元素</span><span class="sxs-lookup"><span data-stu-id="0ac7d-123">Child Elements</span></span>  
 <span data-ttu-id="0ac7d-124">無。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ac7d-125">父項目</span><span class="sxs-lookup"><span data-stu-id="0ac7d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="0ac7d-126">項目</span><span class="sxs-lookup"><span data-stu-id="0ac7d-126">Element</span></span>|<span data-ttu-id="0ac7d-127">說明</span><span class="sxs-lookup"><span data-stu-id="0ac7d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ac7d-128">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="0ac7d-128">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="0ac7d-129">指定授權原則型別的集合。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-129">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ac7d-130">備註</span><span class="sxs-lookup"><span data-stu-id="0ac7d-130">Remarks</span></span>  
 <span data-ttu-id="0ac7d-131">每個授權原則包含一個必要的 `policyType` 屬性字串。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-131">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="0ac7d-132">該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-132">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="0ac7d-133">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-133">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="0ac7d-134">如需授權原則運作方式的詳細資訊，請<xref:System.IdentityModel.Policy.IAuthorizationPolicy>參閱和[授權原則](../../../wcf/samples/authorization-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="0ac7d-134">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ac7d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ac7d-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="0ac7d-136">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="0ac7d-136">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="0ac7d-137">如何：為服務建立自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="0ac7d-137">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="0ac7d-138">\<add></span><span class="sxs-lookup"><span data-stu-id="0ac7d-138">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="0ac7d-139">授權原則</span><span class="sxs-lookup"><span data-stu-id="0ac7d-139">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
