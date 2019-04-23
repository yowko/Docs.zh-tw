---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 660497012dd057e4ecf95524833e2573fe03a8b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224545"
---
# <a name="headers"></a><span data-ttu-id="e5500-101">\<headers></span><span class="sxs-lookup"><span data-stu-id="e5500-101">\<headers></span></span>
<span data-ttu-id="e5500-102">端點除了可以由其基本 URI 定址之外，還可由一個或多個 SOAP 標頭定址。</span><span class="sxs-lookup"><span data-stu-id="e5500-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="e5500-103">有些情況適用這種方式，例如 SOAP 媒介，此時端點需要此端點的用戶端加入目標為媒介的 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="e5500-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="e5500-104">這個組態項目可用於定義此類自訂位址標題。</span><span class="sxs-lookup"><span data-stu-id="e5500-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="e5500-105">端點標頭集合中的項目是使用者定義的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="e5500-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="e5500-106">每個項目必須為格式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="e5500-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="e5500-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e5500-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="e5500-108">\<client></span><span class="sxs-lookup"><span data-stu-id="e5500-108">\<client></span></span>  
<span data-ttu-id="e5500-109">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="e5500-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5500-110">語法</span><span class="sxs-lookup"><span data-stu-id="e5500-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5500-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e5500-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e5500-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e5500-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5500-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e5500-113">Attributes</span></span>  
 <span data-ttu-id="e5500-114">無。</span><span class="sxs-lookup"><span data-stu-id="e5500-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5500-115">子元素</span><span class="sxs-lookup"><span data-stu-id="e5500-115">Child Elements</span></span>  
 <span data-ttu-id="e5500-116">使用者定義的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="e5500-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5500-117">父項目</span><span class="sxs-lookup"><span data-stu-id="e5500-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e5500-118">項目</span><span class="sxs-lookup"><span data-stu-id="e5500-118">Element</span></span>|<span data-ttu-id="e5500-119">描述</span><span class="sxs-lookup"><span data-stu-id="e5500-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5500-120">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="e5500-120">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="e5500-121">設定不同類型的端點。</span><span class="sxs-lookup"><span data-stu-id="e5500-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5500-122">備註</span><span class="sxs-lookup"><span data-stu-id="e5500-122">Remarks</span></span>  
 <span data-ttu-id="e5500-123">選用標頭會提供更多詳細的定址資訊來識別端點或與端點互動。</span><span class="sxs-lookup"><span data-stu-id="e5500-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="e5500-124">例如，標頭會指出如何處理傳入訊息、端點應該將回覆訊息傳送到哪裡，或是當有多個執行個體可用時，要使用哪個服務執行個體來處理來自特定使用者的傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="e5500-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5500-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5500-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="e5500-126">端點：位址、 繫結和合約</span><span class="sxs-lookup"><span data-stu-id="e5500-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
