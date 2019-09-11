---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855179"
---
# <a name="headers"></a><span data-ttu-id="9243d-101">\<標頭 ></span><span class="sxs-lookup"><span data-stu-id="9243d-101">\<headers></span></span>
<span data-ttu-id="9243d-102">端點除了可以由其基本 URI 定址之外，還可由一個或多個 SOAP 標頭定址。</span><span class="sxs-lookup"><span data-stu-id="9243d-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="9243d-103">有些情況適用這種方式，例如 SOAP 媒介，此時端點需要此端點的用戶端加入目標為媒介的 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="9243d-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="9243d-104">這個組態項目可用於定義此類自訂位址標題。</span><span class="sxs-lookup"><span data-stu-id="9243d-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="9243d-105">端點標頭集合中的項目是使用者定義的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="9243d-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="9243d-106">每個項目必須為格式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="9243d-106">Each element has to be well-formed XML.</span></span>  
  
<span data-ttu-id="9243d-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9243d-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9243d-108">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9243d-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9243d-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<用戶端 >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="9243d-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="9243d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<端點 >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="9243d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="9243d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<標頭 >**</span><span class="sxs-lookup"><span data-stu-id="9243d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9243d-112">語法</span><span class="sxs-lookup"><span data-stu-id="9243d-112">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9243d-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9243d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9243d-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9243d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9243d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="9243d-115">Attributes</span></span>  
 <span data-ttu-id="9243d-116">無。</span><span class="sxs-lookup"><span data-stu-id="9243d-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9243d-117">子元素</span><span class="sxs-lookup"><span data-stu-id="9243d-117">Child Elements</span></span>  
 <span data-ttu-id="9243d-118">使用者定義的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="9243d-118">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9243d-119">父項目</span><span class="sxs-lookup"><span data-stu-id="9243d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9243d-120">項目</span><span class="sxs-lookup"><span data-stu-id="9243d-120">Element</span></span>|<span data-ttu-id="9243d-121">描述</span><span class="sxs-lookup"><span data-stu-id="9243d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9243d-122">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="9243d-122">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="9243d-123">設定不同類型的端點。</span><span class="sxs-lookup"><span data-stu-id="9243d-123">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9243d-124">備註</span><span class="sxs-lookup"><span data-stu-id="9243d-124">Remarks</span></span>  
 <span data-ttu-id="9243d-125">選用標頭會提供更多詳細的定址資訊來識別端點或與端點互動。</span><span class="sxs-lookup"><span data-stu-id="9243d-125">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="9243d-126">例如，標頭會指出如何處理傳入訊息、端點應該將回覆訊息傳送到哪裡，或是當有多個執行個體可用時，要使用哪個服務執行個體來處理來自特定使用者的傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="9243d-126">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9243d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9243d-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="9243d-128">終點位址、系結和合約</span><span class="sxs-lookup"><span data-stu-id="9243d-128">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
