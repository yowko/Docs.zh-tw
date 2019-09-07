---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 598b341e8b09acd11ba215e6add3adf9e44b2b81
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400457"
---
# <a name="custom"></a><span data-ttu-id="800df-101">\<custom></span><span class="sxs-lookup"><span data-stu-id="800df-101">\<custom></span></span>
<span data-ttu-id="800df-102">指定自訂對等解析程式服務的設定。</span><span class="sxs-lookup"><span data-stu-id="800df-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="800df-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="800df-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="800df-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="800df-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="800df-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="800df-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="800df-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="800df-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="800df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="800df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="800df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<解析程式 >** ](resolver.md)</span><span class="sxs-lookup"><span data-stu-id="800df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)</span></span>\
<span data-ttu-id="800df-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<自訂 >**</span><span class="sxs-lookup"><span data-stu-id="800df-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="800df-110">語法</span><span class="sxs-lookup"><span data-stu-id="800df-110">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="800df-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="800df-111">Attributes and Elements</span></span>  
 <span data-ttu-id="800df-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="800df-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="800df-113">屬性</span><span class="sxs-lookup"><span data-stu-id="800df-113">Attributes</span></span>  
  
|<span data-ttu-id="800df-114">屬性</span><span class="sxs-lookup"><span data-stu-id="800df-114">Attribute</span></span>|<span data-ttu-id="800df-115">描述</span><span class="sxs-lookup"><span data-stu-id="800df-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="800df-116">URI，這個 URI 會指定裝載自訂解析程式服務之對等節點的端點位址。</span><span class="sxs-lookup"><span data-stu-id="800df-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="800df-117">字串，這個字串會指定自訂對等解析服務之型別。</span><span class="sxs-lookup"><span data-stu-id="800df-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="800df-118">子元素</span><span class="sxs-lookup"><span data-stu-id="800df-118">Child Elements</span></span>  
  
|<span data-ttu-id="800df-119">項目</span><span class="sxs-lookup"><span data-stu-id="800df-119">Element</span></span>|<span data-ttu-id="800df-120">描述</span><span class="sxs-lookup"><span data-stu-id="800df-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="800df-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="800df-121">\<identity></span></span>](identity.md)|<span data-ttu-id="800df-122">指定使用這個項目設定的自訂對等解析程式的身分識別。</span><span class="sxs-lookup"><span data-stu-id="800df-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="800df-123">此項目的型別為 <xref:System.ServiceModel.Configuration.IdentityElement>。</span><span class="sxs-lookup"><span data-stu-id="800df-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="800df-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="800df-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="800df-125">位址標頭的集合，用於自訂對等解析程式所處理的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="800df-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="800df-126">父項目</span><span class="sxs-lookup"><span data-stu-id="800df-126">Parent Elements</span></span>  
  
|<span data-ttu-id="800df-127">項目</span><span class="sxs-lookup"><span data-stu-id="800df-127">Element</span></span>|<span data-ttu-id="800df-128">描述</span><span class="sxs-lookup"><span data-stu-id="800df-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="800df-129">\<resolver></span><span class="sxs-lookup"><span data-stu-id="800df-129">\<resolver></span></span>](resolver.md)|<span data-ttu-id="800df-130">對等解析程式，這個程式可用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。</span><span class="sxs-lookup"><span data-stu-id="800df-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="800df-131">備註</span><span class="sxs-lookup"><span data-stu-id="800df-131">Remarks</span></span>  
 <span data-ttu-id="800df-132">這個項目定義自訂對等解析程式服務的基本設定，包括裝載服務之對等的端點位址以及任何特定繫結設定。</span><span class="sxs-lookup"><span data-stu-id="800df-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="800df-133">如需建立自訂解析程式的詳細資訊，請參閱[將自訂解決器新增至 PeerChannel 應用程式](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="800df-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="800df-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="800df-134">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="800df-135">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="800df-135">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="800df-136">[將自訂解決器新增至 PeerChannel 應用程式](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="800df-136">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
