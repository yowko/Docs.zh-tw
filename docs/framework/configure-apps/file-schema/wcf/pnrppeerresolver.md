---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 0a8cc60226b13552d47faec3a156ed1f59acacb9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181397"
---
# \<pnrpPeerResolver>

<span data-ttu-id="f3b12-101">指定對等名稱解析通訊協定 (Peer Name Resolution Protocol，PNRP) 解析程式做為解析程式使用。</span><span class="sxs-lookup"><span data-stu-id="f3b12-101">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="f3b12-102">這是一個選擇性的項目，因為 PNRP 是預設的解析程式。</span><span class="sxs-lookup"><span data-stu-id="f3b12-102">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="f3b12-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3b12-103">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3b12-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f3b12-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f3b12-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f3b12-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3b12-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f3b12-106">Attributes</span></span>  
  
|<span data-ttu-id="f3b12-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f3b12-107">Attribute</span></span>|<span data-ttu-id="f3b12-108">描述</span><span class="sxs-lookup"><span data-stu-id="f3b12-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3b12-109">resolverType</span><span class="sxs-lookup"><span data-stu-id="f3b12-109">resolverType</span></span>|<span data-ttu-id="f3b12-110">字串，指定要使用的解析程式。</span><span class="sxs-lookup"><span data-stu-id="f3b12-110">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="f3b12-111">此屬性是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="f3b12-111">This attribute is optional.</span></span> <span data-ttu-id="f3b12-112">如果未設定，或如果設定為空字串，則使用 PNRP。</span><span class="sxs-lookup"><span data-stu-id="f3b12-112">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3b12-113">子元素</span><span class="sxs-lookup"><span data-stu-id="f3b12-113">Child Elements</span></span>  

 <span data-ttu-id="f3b12-114">無</span><span class="sxs-lookup"><span data-stu-id="f3b12-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3b12-115">父項目</span><span class="sxs-lookup"><span data-stu-id="f3b12-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f3b12-116">項目</span><span class="sxs-lookup"><span data-stu-id="f3b12-116">Element</span></span>|<span data-ttu-id="f3b12-117">描述</span><span class="sxs-lookup"><span data-stu-id="f3b12-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f3b12-118">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="f3b12-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f3b12-119">範例</span><span class="sxs-lookup"><span data-stu-id="f3b12-119">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f3b12-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3b12-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f3b12-121">繫結</span><span class="sxs-lookup"><span data-stu-id="f3b12-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f3b12-122">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="f3b12-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f3b12-123">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="f3b12-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="f3b12-124">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="f3b12-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
