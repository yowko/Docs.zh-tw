---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d3e88d7f2dd991091d3d7abdc715e125ddc9ac56
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738775"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="cb468-101">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="cb468-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="cb468-102">指定對等名稱解析通訊協定 (Peer Name Resolution Protocol，PNRP) 解析程式做為解析程式使用。</span><span class="sxs-lookup"><span data-stu-id="cb468-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="cb468-103">這是一個選擇性的項目，因為 PNRP 是預設的解析程式。</span><span class="sxs-lookup"><span data-stu-id="cb468-103">This element is optional because PNRP is the default resolver.</span></span>  
  
<span data-ttu-id="cb468-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cb468-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cb468-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="cb468-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cb468-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="cb468-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="cb468-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="cb468-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="cb468-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="cb468-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="cb468-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pnrpResolver >**</span><span class="sxs-lookup"><span data-stu-id="cb468-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb468-110">語法</span><span class="sxs-lookup"><span data-stu-id="cb468-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb468-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cb468-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cb468-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cb468-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb468-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cb468-113">Attributes</span></span>  
  
|<span data-ttu-id="cb468-114">屬性</span><span class="sxs-lookup"><span data-stu-id="cb468-114">Attribute</span></span>|<span data-ttu-id="cb468-115">描述</span><span class="sxs-lookup"><span data-stu-id="cb468-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb468-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="cb468-116">resolverType</span></span>|<span data-ttu-id="cb468-117">字串，指定要使用的解析程式。</span><span class="sxs-lookup"><span data-stu-id="cb468-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="cb468-118">這是一個選擇性的屬性。</span><span class="sxs-lookup"><span data-stu-id="cb468-118">This attribute is optional.</span></span> <span data-ttu-id="cb468-119">如果未設定，或如果設定為空字串，則使用 PNRP。</span><span class="sxs-lookup"><span data-stu-id="cb468-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb468-120">子項目</span><span class="sxs-lookup"><span data-stu-id="cb468-120">Child Elements</span></span>  
 <span data-ttu-id="cb468-121">None</span><span class="sxs-lookup"><span data-stu-id="cb468-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb468-122">父項目</span><span class="sxs-lookup"><span data-stu-id="cb468-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cb468-123">項目</span><span class="sxs-lookup"><span data-stu-id="cb468-123">Element</span></span>|<span data-ttu-id="cb468-124">描述</span><span class="sxs-lookup"><span data-stu-id="cb468-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb468-125">\<binding ></span><span class="sxs-lookup"><span data-stu-id="cb468-125">\<binding></span></span>](bindings.md)|<span data-ttu-id="cb468-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="cb468-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cb468-127">範例</span><span class="sxs-lookup"><span data-stu-id="cb468-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="cb468-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="cb468-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="cb468-129">繫結</span><span class="sxs-lookup"><span data-stu-id="cb468-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cb468-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="cb468-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cb468-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="cb468-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="cb468-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cb468-132">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="cb468-133">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="cb468-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
