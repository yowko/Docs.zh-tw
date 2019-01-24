---
title: '&lt;claimTypeRequirements&gt; 項目的 &lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 33c6b935bb8d39f05e26646d4731ce1459beba81
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702141"
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="0a7c7-102">&lt;claimTypeRequirements&gt; 項目的 &lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="0a7c7-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="0a7c7-103">指定聯合認證中要移除的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="0a7c7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0a7c7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0a7c7-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0a7c7-105">\<bindings></span></span>  
<span data-ttu-id="0a7c7-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="0a7c7-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="0a7c7-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="0a7c7-107">\<binding></span></span>  
<span data-ttu-id="0a7c7-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="0a7c7-108">\<security></span></span>  
<span data-ttu-id="0a7c7-109">\<message></span><span class="sxs-lookup"><span data-stu-id="0a7c7-109">\<message></span></span>  
<span data-ttu-id="0a7c7-110">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="0a7c7-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a7c7-111">語法</span><span class="sxs-lookup"><span data-stu-id="0a7c7-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a7c7-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0a7c7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0a7c7-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a7c7-114">屬性</span><span class="sxs-lookup"><span data-stu-id="0a7c7-114">Attributes</span></span>  
  
|<span data-ttu-id="0a7c7-115">屬性</span><span class="sxs-lookup"><span data-stu-id="0a7c7-115">Attribute</span></span>|<span data-ttu-id="0a7c7-116">描述</span><span class="sxs-lookup"><span data-stu-id="0a7c7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a7c7-117">claimType</span><span class="sxs-lookup"><span data-stu-id="0a7c7-117">claimType</span></span>|<span data-ttu-id="0a7c7-118">定義要移除之宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a7c7-119">子元素</span><span class="sxs-lookup"><span data-stu-id="0a7c7-119">Child Elements</span></span>  
 <span data-ttu-id="0a7c7-120">無。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a7c7-121">父項目</span><span class="sxs-lookup"><span data-stu-id="0a7c7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0a7c7-122">項目</span><span class="sxs-lookup"><span data-stu-id="0a7c7-122">Element</span></span>|<span data-ttu-id="0a7c7-123">描述</span><span class="sxs-lookup"><span data-stu-id="0a7c7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a7c7-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="0a7c7-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="0a7c7-125">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="0a7c7-126">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="0a7c7-127">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="0a7c7-128">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="0a7c7-129">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a7c7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a7c7-130">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
