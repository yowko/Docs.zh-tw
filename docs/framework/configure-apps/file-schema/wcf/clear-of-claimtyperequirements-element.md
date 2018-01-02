---
title: "&lt;claimTypeRequirements&gt; 項目的 &lt;clear&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71cc4516362691484408ae2f81dfee462bd560d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="46b26-102">&lt;claimTypeRequirements&gt; 項目的 &lt;clear&gt;</span><span class="sxs-lookup"><span data-stu-id="46b26-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="46b26-103">指定移除聯合認證中的所有宣告型別。</span><span class="sxs-lookup"><span data-stu-id="46b26-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="46b26-104">這個動作可確保集合啟動時是空的。</span><span class="sxs-lookup"><span data-stu-id="46b26-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="46b26-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="46b26-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="46b26-106">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="46b26-106">\<bindings></span></span>  
<span data-ttu-id="46b26-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="46b26-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="46b26-108">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="46b26-108">\<binding></span></span>  
<span data-ttu-id="46b26-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="46b26-109">\<security></span></span>  
<span data-ttu-id="46b26-110">\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="46b26-110">\<message></span></span>  
<span data-ttu-id="46b26-111">\<q ></span><span class="sxs-lookup"><span data-stu-id="46b26-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46b26-112">語法</span><span class="sxs-lookup"><span data-stu-id="46b26-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46b26-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="46b26-113">Attributes and Elements</span></span>  
 <span data-ttu-id="46b26-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="46b26-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46b26-115">屬性</span><span class="sxs-lookup"><span data-stu-id="46b26-115">Attributes</span></span>  
 <span data-ttu-id="46b26-116">無。</span><span class="sxs-lookup"><span data-stu-id="46b26-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="46b26-117">子元素</span><span class="sxs-lookup"><span data-stu-id="46b26-117">Child Elements</span></span>  
 <span data-ttu-id="46b26-118">無。</span><span class="sxs-lookup"><span data-stu-id="46b26-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46b26-119">父項目</span><span class="sxs-lookup"><span data-stu-id="46b26-119">Parent Elements</span></span>  
  
|<span data-ttu-id="46b26-120">項目</span><span class="sxs-lookup"><span data-stu-id="46b26-120">Element</span></span>|<span data-ttu-id="46b26-121">描述</span><span class="sxs-lookup"><span data-stu-id="46b26-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46b26-122">\<q ></span><span class="sxs-lookup"><span data-stu-id="46b26-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="46b26-123">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="46b26-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="46b26-124">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="46b26-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="46b26-125">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="46b26-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="46b26-126">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="46b26-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="46b26-127">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="46b26-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46b26-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="46b26-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
