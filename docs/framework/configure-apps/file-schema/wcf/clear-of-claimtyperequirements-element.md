---
title: <clear> 項目的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 35d0391951204bd352918d3004f0cc4f9480b0e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090313"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="25303-102">\<清除 > 的\<claimTypeRequirements > 項目</span><span class="sxs-lookup"><span data-stu-id="25303-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="25303-103">指定移除聯合認證中的所有宣告型別。</span><span class="sxs-lookup"><span data-stu-id="25303-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="25303-104">這個動作可確保集合啟動時是空的。</span><span class="sxs-lookup"><span data-stu-id="25303-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="25303-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="25303-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="25303-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="25303-106">\<bindings></span></span>  
<span data-ttu-id="25303-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="25303-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="25303-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="25303-108">\<binding></span></span>  
<span data-ttu-id="25303-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="25303-109">\<security></span></span>  
<span data-ttu-id="25303-110">\<message></span><span class="sxs-lookup"><span data-stu-id="25303-110">\<message></span></span>  
<span data-ttu-id="25303-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="25303-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25303-112">語法</span><span class="sxs-lookup"><span data-stu-id="25303-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25303-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="25303-113">Attributes and Elements</span></span>  
 <span data-ttu-id="25303-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="25303-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25303-115">屬性</span><span class="sxs-lookup"><span data-stu-id="25303-115">Attributes</span></span>  
 <span data-ttu-id="25303-116">無。</span><span class="sxs-lookup"><span data-stu-id="25303-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25303-117">子元素</span><span class="sxs-lookup"><span data-stu-id="25303-117">Child Elements</span></span>  
 <span data-ttu-id="25303-118">無。</span><span class="sxs-lookup"><span data-stu-id="25303-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25303-119">父項目</span><span class="sxs-lookup"><span data-stu-id="25303-119">Parent Elements</span></span>  
  
|<span data-ttu-id="25303-120">項目</span><span class="sxs-lookup"><span data-stu-id="25303-120">Element</span></span>|<span data-ttu-id="25303-121">描述</span><span class="sxs-lookup"><span data-stu-id="25303-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25303-122">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="25303-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="25303-123">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="25303-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="25303-124">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="25303-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="25303-125">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="25303-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="25303-126">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="25303-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="25303-127">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="25303-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25303-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25303-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
