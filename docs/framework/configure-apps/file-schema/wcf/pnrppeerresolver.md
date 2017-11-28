---
title: '&lt;pnrpPeerResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cd93bdadec120050813fcc1097d3041d6be94f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="602bc-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="602bc-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="602bc-103">指定對等名稱解析通訊協定 (Peer Name Resolution Protocol，PNRP) 解析程式做為解析程式使用。</span><span class="sxs-lookup"><span data-stu-id="602bc-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="602bc-104">這是一個選擇性的項目，因為 PNRP 是預設的解析程式。</span><span class="sxs-lookup"><span data-stu-id="602bc-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="602bc-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="602bc-105">\<system.serviceModel></span></span>  
<span data-ttu-id="602bc-106">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="602bc-106">\<bindings></span></span>  
<span data-ttu-id="602bc-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="602bc-107">\<customBinding></span></span>  
<span data-ttu-id="602bc-108">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="602bc-108">\<binding></span></span>  
<span data-ttu-id="602bc-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="602bc-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="602bc-110">語法</span><span class="sxs-lookup"><span data-stu-id="602bc-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="602bc-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="602bc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="602bc-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="602bc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="602bc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="602bc-113">Attributes</span></span>  
  
|<span data-ttu-id="602bc-114">屬性</span><span class="sxs-lookup"><span data-stu-id="602bc-114">Attribute</span></span>|<span data-ttu-id="602bc-115">描述</span><span class="sxs-lookup"><span data-stu-id="602bc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="602bc-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="602bc-116">resolverType</span></span>|<span data-ttu-id="602bc-117">字串，指定要使用的解析程式。</span><span class="sxs-lookup"><span data-stu-id="602bc-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="602bc-118">這是一個選擇性的屬性。</span><span class="sxs-lookup"><span data-stu-id="602bc-118">This attribute is optional.</span></span> <span data-ttu-id="602bc-119">如果未設定，或如果設定為空字串，則使用 PNRP。</span><span class="sxs-lookup"><span data-stu-id="602bc-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="602bc-120">子元素</span><span class="sxs-lookup"><span data-stu-id="602bc-120">Child Elements</span></span>  
 <span data-ttu-id="602bc-121">無</span><span class="sxs-lookup"><span data-stu-id="602bc-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="602bc-122">父項目</span><span class="sxs-lookup"><span data-stu-id="602bc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="602bc-123">項目</span><span class="sxs-lookup"><span data-stu-id="602bc-123">Element</span></span>|<span data-ttu-id="602bc-124">說明</span><span class="sxs-lookup"><span data-stu-id="602bc-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="602bc-125">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="602bc-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="602bc-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="602bc-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="602bc-127">範例</span><span class="sxs-lookup"><span data-stu-id="602bc-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="602bc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="602bc-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="602bc-129">繫結</span><span class="sxs-lookup"><span data-stu-id="602bc-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="602bc-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="602bc-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="602bc-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="602bc-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="602bc-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="602bc-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="602bc-133">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="602bc-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
