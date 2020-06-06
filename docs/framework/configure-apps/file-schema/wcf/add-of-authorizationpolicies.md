---
title: <add> 的 <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400692"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="e0f97-102">\<add> 的 \<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="e0f97-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="e0f97-103">指定用於宣告轉換的驗證原則。</span><span class="sxs-lookup"><span data-stu-id="e0f97-103">Specifies an authorization policy for claim transformation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="e0f97-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0f97-104">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="e0f97-105">類型</span><span class="sxs-lookup"><span data-stu-id="e0f97-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0f97-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e0f97-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e0f97-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e0f97-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0f97-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e0f97-108">Attributes</span></span>  
  
|<span data-ttu-id="e0f97-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e0f97-109">Attribute</span></span>|<span data-ttu-id="e0f97-110">描述</span><span class="sxs-lookup"><span data-stu-id="e0f97-110">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="e0f97-111">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="e0f97-111">A required String attribute.</span></span><br /><br /> <span data-ttu-id="e0f97-112">Windows Communication Foundation （WCF）存取控制模型支援提供一組授權原則做為類型。</span><span class="sxs-lookup"><span data-stu-id="e0f97-112">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="e0f97-113">此屬性會指定授權原則，可將一組輸入宣告轉換為另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="e0f97-113">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="e0f97-114">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="e0f97-114">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0f97-115">子元素</span><span class="sxs-lookup"><span data-stu-id="e0f97-115">Child Elements</span></span>  
 <span data-ttu-id="e0f97-116">無。</span><span class="sxs-lookup"><span data-stu-id="e0f97-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0f97-117">父項目</span><span class="sxs-lookup"><span data-stu-id="e0f97-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e0f97-118">元素</span><span class="sxs-lookup"><span data-stu-id="e0f97-118">Element</span></span>|<span data-ttu-id="e0f97-119">描述</span><span class="sxs-lookup"><span data-stu-id="e0f97-119">Description</span></span>|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|<span data-ttu-id="e0f97-120">指定授權原則型別的集合。</span><span class="sxs-lookup"><span data-stu-id="e0f97-120">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0f97-121">備註</span><span class="sxs-lookup"><span data-stu-id="e0f97-121">Remarks</span></span>  
 <span data-ttu-id="e0f97-122">每個授權原則包含一個必要的 `policyType` 屬性字串。</span><span class="sxs-lookup"><span data-stu-id="e0f97-122">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="e0f97-123">該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="e0f97-123">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="e0f97-124">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="e0f97-124">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="e0f97-125">如需授權原則運作方式的詳細資訊，請參閱 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 和[授權原則](../../../wcf/samples/authorization-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f97-125">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f97-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0f97-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="e0f97-127">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="e0f97-127">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="e0f97-128">如何：為服務建立自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="e0f97-128">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="e0f97-129">授權原則</span><span class="sxs-lookup"><span data-stu-id="e0f97-129">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
