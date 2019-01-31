---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: f98c358cc9891e9d7223d280fc8e50c19aad9759
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260643"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="b3f86-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="b3f86-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="b3f86-102">指定對等名稱解析通訊協定 (Peer Name Resolution Protocol，PNRP) 解析程式做為解析程式使用。</span><span class="sxs-lookup"><span data-stu-id="b3f86-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="b3f86-103">這是一個選擇性的項目，因為 PNRP 是預設的解析程式。</span><span class="sxs-lookup"><span data-stu-id="b3f86-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="b3f86-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b3f86-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b3f86-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b3f86-105">\<bindings></span></span>  
<span data-ttu-id="b3f86-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b3f86-106">\<customBinding></span></span>  
<span data-ttu-id="b3f86-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="b3f86-107">\<binding></span></span>  
<span data-ttu-id="b3f86-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="b3f86-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f86-109">語法</span><span class="sxs-lookup"><span data-stu-id="b3f86-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3f86-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b3f86-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b3f86-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b3f86-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3f86-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b3f86-112">Attributes</span></span>  
  
|<span data-ttu-id="b3f86-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b3f86-113">Attribute</span></span>|<span data-ttu-id="b3f86-114">描述</span><span class="sxs-lookup"><span data-stu-id="b3f86-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3f86-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="b3f86-115">resolverType</span></span>|<span data-ttu-id="b3f86-116">字串，指定要使用的解析程式。</span><span class="sxs-lookup"><span data-stu-id="b3f86-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="b3f86-117">這是一個選擇性的屬性。</span><span class="sxs-lookup"><span data-stu-id="b3f86-117">This attribute is optional.</span></span> <span data-ttu-id="b3f86-118">如果未設定，或如果設定為空字串，則使用 PNRP。</span><span class="sxs-lookup"><span data-stu-id="b3f86-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3f86-119">子元素</span><span class="sxs-lookup"><span data-stu-id="b3f86-119">Child Elements</span></span>  
 <span data-ttu-id="b3f86-120">無</span><span class="sxs-lookup"><span data-stu-id="b3f86-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3f86-121">父項目</span><span class="sxs-lookup"><span data-stu-id="b3f86-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b3f86-122">項目</span><span class="sxs-lookup"><span data-stu-id="b3f86-122">Element</span></span>|<span data-ttu-id="b3f86-123">描述</span><span class="sxs-lookup"><span data-stu-id="b3f86-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3f86-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="b3f86-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b3f86-125">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="b3f86-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b3f86-126">範例</span><span class="sxs-lookup"><span data-stu-id="b3f86-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b3f86-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3f86-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b3f86-128">繫結</span><span class="sxs-lookup"><span data-stu-id="b3f86-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b3f86-129">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="b3f86-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b3f86-130">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="b3f86-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b3f86-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b3f86-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="b3f86-132">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="b3f86-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
