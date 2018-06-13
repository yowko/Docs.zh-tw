---
title: '&lt;claimTypeRequirements&gt; 項目的 &lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 5d1f9c963792336f0938113beefbdef770831e9d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753237"
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="d3089-102">&lt;claimTypeRequirements&gt; 項目的 &lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="d3089-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="d3089-103">指定聯合認證中要移除的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="d3089-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="d3089-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d3089-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d3089-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="d3089-105">\<bindings></span></span>  
<span data-ttu-id="d3089-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="d3089-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d3089-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="d3089-107">\<binding></span></span>  
<span data-ttu-id="d3089-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="d3089-108">\<security></span></span>  
<span data-ttu-id="d3089-109">\<message></span><span class="sxs-lookup"><span data-stu-id="d3089-109">\<message></span></span>  
<span data-ttu-id="d3089-110">\<q ></span><span class="sxs-lookup"><span data-stu-id="d3089-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3089-111">語法</span><span class="sxs-lookup"><span data-stu-id="d3089-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3089-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d3089-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d3089-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d3089-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3089-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d3089-114">Attributes</span></span>  
  
|<span data-ttu-id="d3089-115">屬性</span><span class="sxs-lookup"><span data-stu-id="d3089-115">Attribute</span></span>|<span data-ttu-id="d3089-116">描述</span><span class="sxs-lookup"><span data-stu-id="d3089-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3089-117">claimType</span><span class="sxs-lookup"><span data-stu-id="d3089-117">claimType</span></span>|<span data-ttu-id="d3089-118">定義要移除之宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="d3089-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3089-119">子項目</span><span class="sxs-lookup"><span data-stu-id="d3089-119">Child Elements</span></span>  
 <span data-ttu-id="d3089-120">無。</span><span class="sxs-lookup"><span data-stu-id="d3089-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3089-121">父項目</span><span class="sxs-lookup"><span data-stu-id="d3089-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d3089-122">項目</span><span class="sxs-lookup"><span data-stu-id="d3089-122">Element</span></span>|<span data-ttu-id="d3089-123">描述</span><span class="sxs-lookup"><span data-stu-id="d3089-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3089-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d3089-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="d3089-125">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="d3089-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d3089-126">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="d3089-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d3089-127">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="d3089-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d3089-128">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="d3089-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d3089-129">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="d3089-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3089-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3089-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
