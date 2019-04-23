---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 2404f00b2a3ba03e89c1e21fb25e13cabb8feed3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214049"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="dc58b-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="dc58b-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="dc58b-102">指定對等名稱解析通訊協定 (Peer Name Resolution Protocol，PNRP) 解析程式做為解析程式使用。</span><span class="sxs-lookup"><span data-stu-id="dc58b-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="dc58b-103">這是一個選擇性的項目，因為 PNRP 是預設的解析程式。</span><span class="sxs-lookup"><span data-stu-id="dc58b-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="dc58b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dc58b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="dc58b-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="dc58b-105">\<bindings></span></span>  
<span data-ttu-id="dc58b-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="dc58b-106">\<customBinding></span></span>  
<span data-ttu-id="dc58b-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="dc58b-107">\<binding></span></span>  
<span data-ttu-id="dc58b-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="dc58b-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc58b-109">語法</span><span class="sxs-lookup"><span data-stu-id="dc58b-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc58b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dc58b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dc58b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dc58b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc58b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="dc58b-112">Attributes</span></span>  
  
|<span data-ttu-id="dc58b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="dc58b-113">Attribute</span></span>|<span data-ttu-id="dc58b-114">描述</span><span class="sxs-lookup"><span data-stu-id="dc58b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc58b-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="dc58b-115">resolverType</span></span>|<span data-ttu-id="dc58b-116">字串，指定要使用的解析程式。</span><span class="sxs-lookup"><span data-stu-id="dc58b-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="dc58b-117">這是一個選擇性的屬性。</span><span class="sxs-lookup"><span data-stu-id="dc58b-117">This attribute is optional.</span></span> <span data-ttu-id="dc58b-118">如果未設定，或如果設定為空字串，則使用 PNRP。</span><span class="sxs-lookup"><span data-stu-id="dc58b-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc58b-119">子元素</span><span class="sxs-lookup"><span data-stu-id="dc58b-119">Child Elements</span></span>  
 <span data-ttu-id="dc58b-120">None</span><span class="sxs-lookup"><span data-stu-id="dc58b-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc58b-121">父項目</span><span class="sxs-lookup"><span data-stu-id="dc58b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dc58b-122">項目</span><span class="sxs-lookup"><span data-stu-id="dc58b-122">Element</span></span>|<span data-ttu-id="dc58b-123">描述</span><span class="sxs-lookup"><span data-stu-id="dc58b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc58b-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="dc58b-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="dc58b-125">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="dc58b-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dc58b-126">範例</span><span class="sxs-lookup"><span data-stu-id="dc58b-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="dc58b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc58b-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="dc58b-128">繫結</span><span class="sxs-lookup"><span data-stu-id="dc58b-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="dc58b-129">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="dc58b-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="dc58b-130">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="dc58b-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="dc58b-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="dc58b-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="dc58b-132">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="dc58b-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
