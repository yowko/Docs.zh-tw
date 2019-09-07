---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d7c6c8efa971fb60f0257cc1c74ceda72e31cb84
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400040"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="45cfb-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="45cfb-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="45cfb-102">指定對等名稱解析通訊協定 (Peer Name Resolution Protocol，PNRP) 解析程式做為解析程式使用。</span><span class="sxs-lookup"><span data-stu-id="45cfb-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="45cfb-103">這是一個選擇性的項目，因為 PNRP 是預設的解析程式。</span><span class="sxs-lookup"><span data-stu-id="45cfb-103">This element is optional because PNRP is the default resolver.</span></span>  
  
<span data-ttu-id="45cfb-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="45cfb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="45cfb-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="45cfb-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="45cfb-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="45cfb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="45cfb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="45cfb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="45cfb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="45cfb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="45cfb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pnrpResolver >**</span><span class="sxs-lookup"><span data-stu-id="45cfb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45cfb-110">語法</span><span class="sxs-lookup"><span data-stu-id="45cfb-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45cfb-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="45cfb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="45cfb-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="45cfb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45cfb-113">屬性</span><span class="sxs-lookup"><span data-stu-id="45cfb-113">Attributes</span></span>  
  
|<span data-ttu-id="45cfb-114">屬性</span><span class="sxs-lookup"><span data-stu-id="45cfb-114">Attribute</span></span>|<span data-ttu-id="45cfb-115">說明</span><span class="sxs-lookup"><span data-stu-id="45cfb-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45cfb-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="45cfb-116">resolverType</span></span>|<span data-ttu-id="45cfb-117">字串，指定要使用的解析程式。</span><span class="sxs-lookup"><span data-stu-id="45cfb-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="45cfb-118">這是一個選擇性的屬性。</span><span class="sxs-lookup"><span data-stu-id="45cfb-118">This attribute is optional.</span></span> <span data-ttu-id="45cfb-119">如果未設定，或如果設定為空字串，則使用 PNRP。</span><span class="sxs-lookup"><span data-stu-id="45cfb-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45cfb-120">子元素</span><span class="sxs-lookup"><span data-stu-id="45cfb-120">Child Elements</span></span>  
 <span data-ttu-id="45cfb-121">無</span><span class="sxs-lookup"><span data-stu-id="45cfb-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45cfb-122">父項目</span><span class="sxs-lookup"><span data-stu-id="45cfb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="45cfb-123">項目</span><span class="sxs-lookup"><span data-stu-id="45cfb-123">Element</span></span>|<span data-ttu-id="45cfb-124">描述</span><span class="sxs-lookup"><span data-stu-id="45cfb-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45cfb-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="45cfb-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="45cfb-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="45cfb-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="45cfb-127">範例</span><span class="sxs-lookup"><span data-stu-id="45cfb-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="45cfb-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45cfb-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="45cfb-129">繫結</span><span class="sxs-lookup"><span data-stu-id="45cfb-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="45cfb-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="45cfb-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="45cfb-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="45cfb-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="45cfb-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="45cfb-132">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="45cfb-133">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="45cfb-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
