---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: c208a6c7305ccbbe8efb10d071de29cf1bd2cc10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165139"
---
# \<custom>

<span data-ttu-id="6fd21-101">指定自訂對等解析程式服務的設定。</span><span class="sxs-lookup"><span data-stu-id="6fd21-101">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="6fd21-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="6fd21-102">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fd21-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6fd21-103">Attributes and Elements</span></span>  

 <span data-ttu-id="6fd21-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6fd21-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fd21-105">屬性</span><span class="sxs-lookup"><span data-stu-id="6fd21-105">Attributes</span></span>  
  
|<span data-ttu-id="6fd21-106">屬性</span><span class="sxs-lookup"><span data-stu-id="6fd21-106">Attribute</span></span>|<span data-ttu-id="6fd21-107">描述</span><span class="sxs-lookup"><span data-stu-id="6fd21-107">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="6fd21-108">URI，這個 URI 會指定裝載自訂解析程式服務之對等節點的端點位址。</span><span class="sxs-lookup"><span data-stu-id="6fd21-108">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="6fd21-109">字串，這個字串會指定自訂對等解析服務之型別。</span><span class="sxs-lookup"><span data-stu-id="6fd21-109">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fd21-110">子元素</span><span class="sxs-lookup"><span data-stu-id="6fd21-110">Child Elements</span></span>  
  
|<span data-ttu-id="6fd21-111">項目</span><span class="sxs-lookup"><span data-stu-id="6fd21-111">Element</span></span>|<span data-ttu-id="6fd21-112">描述</span><span class="sxs-lookup"><span data-stu-id="6fd21-112">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="6fd21-113">指定使用這個項目設定的自訂對等解析程式的身分識別。</span><span class="sxs-lookup"><span data-stu-id="6fd21-113">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="6fd21-114">此項目的型別為 <xref:System.ServiceModel.Configuration.IdentityElement>。</span><span class="sxs-lookup"><span data-stu-id="6fd21-114">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="6fd21-115">位址標頭的集合，用於自訂對等解析程式所處理的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="6fd21-115">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6fd21-116">父項目</span><span class="sxs-lookup"><span data-stu-id="6fd21-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6fd21-117">項目</span><span class="sxs-lookup"><span data-stu-id="6fd21-117">Element</span></span>|<span data-ttu-id="6fd21-118">描述</span><span class="sxs-lookup"><span data-stu-id="6fd21-118">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="6fd21-119">對等解析程式，這個程式可用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。</span><span class="sxs-lookup"><span data-stu-id="6fd21-119">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fd21-120">備註</span><span class="sxs-lookup"><span data-stu-id="6fd21-120">Remarks</span></span>  

 <span data-ttu-id="6fd21-121">這個項目定義自訂對等解析程式服務的基本設定，包括裝載服務之對等的端點位址以及任何特定繫結設定。</span><span class="sxs-lookup"><span data-stu-id="6fd21-121">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="6fd21-122">如需有關建立自訂解析程式的詳細資訊，請參閱 [將自訂解析程式新增至 PeerChannel 應用程式](/previous-versions/ms730105(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="6fd21-122">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd21-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fd21-123">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="6fd21-124">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="6fd21-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="6fd21-125">[將自訂解析程式新增至 PeerChannel 應用程式](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6fd21-125">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>
