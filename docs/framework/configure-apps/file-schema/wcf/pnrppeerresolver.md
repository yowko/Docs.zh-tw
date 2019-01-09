---
title: '&lt;pnrpPeerResolver&gt;'
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 882974ea29804c7218d4c6c21da2b9ddd7551c54
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150134"
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="96ab3-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="96ab3-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="96ab3-103">指定對等名稱解析通訊協定 (Peer Name Resolution Protocol，PNRP) 解析程式做為解析程式使用。</span><span class="sxs-lookup"><span data-stu-id="96ab3-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="96ab3-104">這是一個選擇性的項目，因為 PNRP 是預設的解析程式。</span><span class="sxs-lookup"><span data-stu-id="96ab3-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="96ab3-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="96ab3-105">\<system.serviceModel></span></span>  
<span data-ttu-id="96ab3-106">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="96ab3-106">\<bindings></span></span>  
<span data-ttu-id="96ab3-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="96ab3-107">\<customBinding></span></span>  
<span data-ttu-id="96ab3-108">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="96ab3-108">\<binding></span></span>  
<span data-ttu-id="96ab3-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="96ab3-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ab3-110">語法</span><span class="sxs-lookup"><span data-stu-id="96ab3-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96ab3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="96ab3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="96ab3-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="96ab3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96ab3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="96ab3-113">Attributes</span></span>  
  
|<span data-ttu-id="96ab3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="96ab3-114">Attribute</span></span>|<span data-ttu-id="96ab3-115">描述</span><span class="sxs-lookup"><span data-stu-id="96ab3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96ab3-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="96ab3-116">resolverType</span></span>|<span data-ttu-id="96ab3-117">字串，指定要使用的解析程式。</span><span class="sxs-lookup"><span data-stu-id="96ab3-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="96ab3-118">這是一個選擇性的屬性。</span><span class="sxs-lookup"><span data-stu-id="96ab3-118">This attribute is optional.</span></span> <span data-ttu-id="96ab3-119">如果未設定，或如果設定為空字串，則使用 PNRP。</span><span class="sxs-lookup"><span data-stu-id="96ab3-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96ab3-120">子元素</span><span class="sxs-lookup"><span data-stu-id="96ab3-120">Child Elements</span></span>  
 <span data-ttu-id="96ab3-121">無</span><span class="sxs-lookup"><span data-stu-id="96ab3-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96ab3-122">父項目</span><span class="sxs-lookup"><span data-stu-id="96ab3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="96ab3-123">項目</span><span class="sxs-lookup"><span data-stu-id="96ab3-123">Element</span></span>|<span data-ttu-id="96ab3-124">描述</span><span class="sxs-lookup"><span data-stu-id="96ab3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96ab3-125">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="96ab3-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="96ab3-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="96ab3-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="96ab3-127">範例</span><span class="sxs-lookup"><span data-stu-id="96ab3-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="96ab3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96ab3-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="96ab3-129">繫結</span><span class="sxs-lookup"><span data-stu-id="96ab3-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="96ab3-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="96ab3-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="96ab3-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="96ab3-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="96ab3-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="96ab3-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="96ab3-133">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="96ab3-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
