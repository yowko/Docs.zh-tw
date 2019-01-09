---
title: '&lt;claimTypeRequirements&gt; 項目的 &lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 7610a8e95996f15133ae58ec33c4afd9e2309cac
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146208"
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="2c5ed-102">&lt;claimTypeRequirements&gt; 項目的 &lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="2c5ed-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="2c5ed-103">指定聯合認證中要移除的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="2c5ed-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="2c5ed-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2c5ed-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2c5ed-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2c5ed-105">\<bindings></span></span>  
<span data-ttu-id="2c5ed-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="2c5ed-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="2c5ed-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2c5ed-107">\<binding></span></span>  
<span data-ttu-id="2c5ed-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="2c5ed-108">\<security></span></span>  
<span data-ttu-id="2c5ed-109">\<message></span><span class="sxs-lookup"><span data-stu-id="2c5ed-109">\<message></span></span>  
<span data-ttu-id="2c5ed-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="2c5ed-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c5ed-111">語法</span><span class="sxs-lookup"><span data-stu-id="2c5ed-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c5ed-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2c5ed-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2c5ed-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2c5ed-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c5ed-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2c5ed-114">Attributes</span></span>  
  
|<span data-ttu-id="2c5ed-115">屬性</span><span class="sxs-lookup"><span data-stu-id="2c5ed-115">Attribute</span></span>|<span data-ttu-id="2c5ed-116">描述</span><span class="sxs-lookup"><span data-stu-id="2c5ed-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c5ed-117">claimType</span><span class="sxs-lookup"><span data-stu-id="2c5ed-117">claimType</span></span>|<span data-ttu-id="2c5ed-118">定義要移除之宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="2c5ed-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c5ed-119">子元素</span><span class="sxs-lookup"><span data-stu-id="2c5ed-119">Child Elements</span></span>  
 <span data-ttu-id="2c5ed-120">無。</span><span class="sxs-lookup"><span data-stu-id="2c5ed-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c5ed-121">父項目</span><span class="sxs-lookup"><span data-stu-id="2c5ed-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2c5ed-122">項目</span><span class="sxs-lookup"><span data-stu-id="2c5ed-122">Element</span></span>|<span data-ttu-id="2c5ed-123">描述</span><span class="sxs-lookup"><span data-stu-id="2c5ed-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c5ed-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="2c5ed-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="2c5ed-125">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="2c5ed-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="2c5ed-126">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="2c5ed-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="2c5ed-127">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="2c5ed-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2c5ed-128">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="2c5ed-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2c5ed-129">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="2c5ed-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c5ed-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c5ed-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
