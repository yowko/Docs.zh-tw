---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 347a08a35ff898ab7037c11d3c87fda73c3ab2ab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178095"
---
# \<headers>

<span data-ttu-id="d82fc-101">端點除了可以由其基本 URI 定址之外，還可由一個或多個 SOAP 標頭定址。</span><span class="sxs-lookup"><span data-stu-id="d82fc-101">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="d82fc-102">有些情況適用這種方式，例如 SOAP 媒介，此時端點需要此端點的用戶端加入目標為媒介的 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="d82fc-102">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="d82fc-103">這個組態項目可用於定義此類自訂位址標題。</span><span class="sxs-lookup"><span data-stu-id="d82fc-103">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="d82fc-104">端點標頭集合中的項目是使用者定義的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="d82fc-104">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="d82fc-105">每個項目必須為格式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="d82fc-105">Each element has to be well-formed XML.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**  
  
## <a name="syntax"></a><span data-ttu-id="d82fc-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d82fc-106">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d82fc-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d82fc-107">Attributes and Elements</span></span>  

 <span data-ttu-id="d82fc-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d82fc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d82fc-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d82fc-109">Attributes</span></span>  

 <span data-ttu-id="d82fc-110">無。</span><span class="sxs-lookup"><span data-stu-id="d82fc-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d82fc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d82fc-111">Child Elements</span></span>  

 <span data-ttu-id="d82fc-112">使用者定義的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="d82fc-112">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d82fc-113">父項目</span><span class="sxs-lookup"><span data-stu-id="d82fc-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d82fc-114">項目</span><span class="sxs-lookup"><span data-stu-id="d82fc-114">Element</span></span>|<span data-ttu-id="d82fc-115">描述</span><span class="sxs-lookup"><span data-stu-id="d82fc-115">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="d82fc-116">設定不同類型的端點。</span><span class="sxs-lookup"><span data-stu-id="d82fc-116">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d82fc-117">備註</span><span class="sxs-lookup"><span data-stu-id="d82fc-117">Remarks</span></span>  

 <span data-ttu-id="d82fc-118">選用標頭會提供更多詳細的定址資訊來識別端點或與端點互動。</span><span class="sxs-lookup"><span data-stu-id="d82fc-118">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="d82fc-119">例如，標頭會指出如何處理傳入訊息、端點應該將回覆訊息傳送到哪裡，或是當有多個執行個體可用時，要使用哪個服務執行個體來處理來自特定使用者的傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="d82fc-119">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82fc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d82fc-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="d82fc-121">端點：位址、繫結和合約</span><span class="sxs-lookup"><span data-stu-id="d82fc-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
