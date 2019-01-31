---
title: <clear> 項目的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: b20d5c1808bf41d1ecd6b3e3a61606ae45b0fbdd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270334"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="b8d48-102">\<清除 > 的\<claimTypeRequirements > 項目</span><span class="sxs-lookup"><span data-stu-id="b8d48-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="b8d48-103">指定移除聯合認證中的所有宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b8d48-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="b8d48-104">這個動作可確保集合啟動時是空的。</span><span class="sxs-lookup"><span data-stu-id="b8d48-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="b8d48-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8d48-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8d48-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b8d48-106">\<bindings></span></span>  
<span data-ttu-id="b8d48-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="b8d48-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="b8d48-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="b8d48-108">\<binding></span></span>  
<span data-ttu-id="b8d48-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="b8d48-109">\<security></span></span>  
<span data-ttu-id="b8d48-110">\<message></span><span class="sxs-lookup"><span data-stu-id="b8d48-110">\<message></span></span>  
<span data-ttu-id="b8d48-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="b8d48-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8d48-112">語法</span><span class="sxs-lookup"><span data-stu-id="b8d48-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8d48-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8d48-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b8d48-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b8d48-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8d48-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b8d48-115">Attributes</span></span>  
 <span data-ttu-id="b8d48-116">無。</span><span class="sxs-lookup"><span data-stu-id="b8d48-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8d48-117">子元素</span><span class="sxs-lookup"><span data-stu-id="b8d48-117">Child Elements</span></span>  
 <span data-ttu-id="b8d48-118">無。</span><span class="sxs-lookup"><span data-stu-id="b8d48-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8d48-119">父項目</span><span class="sxs-lookup"><span data-stu-id="b8d48-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b8d48-120">項目</span><span class="sxs-lookup"><span data-stu-id="b8d48-120">Element</span></span>|<span data-ttu-id="b8d48-121">描述</span><span class="sxs-lookup"><span data-stu-id="b8d48-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8d48-122">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="b8d48-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="b8d48-123">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="b8d48-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="b8d48-124">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="b8d48-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="b8d48-125">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="b8d48-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b8d48-126">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b8d48-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b8d48-127">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b8d48-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8d48-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8d48-128">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
