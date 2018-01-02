---
title: "&lt;claimTypeRequirements&gt; 項目的 &lt;remove&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49009cb7e988c27ccc426e29c6ac973e553a0f73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="7c273-102">&lt;claimTypeRequirements&gt; 項目的 &lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="7c273-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="7c273-103">指定聯合認證中要移除的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="7c273-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="7c273-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7c273-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7c273-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7c273-105">\<bindings></span></span>  
<span data-ttu-id="7c273-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="7c273-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="7c273-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7c273-107">\<binding></span></span>  
<span data-ttu-id="7c273-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="7c273-108">\<security></span></span>  
<span data-ttu-id="7c273-109">\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="7c273-109">\<message></span></span>  
<span data-ttu-id="7c273-110">\<q ></span><span class="sxs-lookup"><span data-stu-id="7c273-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c273-111">語法</span><span class="sxs-lookup"><span data-stu-id="7c273-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c273-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7c273-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7c273-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7c273-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c273-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7c273-114">Attributes</span></span>  
  
|<span data-ttu-id="7c273-115">屬性</span><span class="sxs-lookup"><span data-stu-id="7c273-115">Attribute</span></span>|<span data-ttu-id="7c273-116">描述</span><span class="sxs-lookup"><span data-stu-id="7c273-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c273-117">claimType</span><span class="sxs-lookup"><span data-stu-id="7c273-117">claimType</span></span>|<span data-ttu-id="7c273-118">定義要移除之宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="7c273-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c273-119">子元素</span><span class="sxs-lookup"><span data-stu-id="7c273-119">Child Elements</span></span>  
 <span data-ttu-id="7c273-120">無。</span><span class="sxs-lookup"><span data-stu-id="7c273-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c273-121">父項目</span><span class="sxs-lookup"><span data-stu-id="7c273-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7c273-122">項目</span><span class="sxs-lookup"><span data-stu-id="7c273-122">Element</span></span>|<span data-ttu-id="7c273-123">描述</span><span class="sxs-lookup"><span data-stu-id="7c273-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c273-124">\<q ></span><span class="sxs-lookup"><span data-stu-id="7c273-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="7c273-125">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="7c273-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="7c273-126">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="7c273-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="7c273-127">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="7c273-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="7c273-128">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="7c273-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="7c273-129">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="7c273-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c273-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="7c273-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
