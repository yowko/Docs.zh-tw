---
title: '&lt;標頭&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 84b9a9437d4b0dfae72a6e625b21f2b830eb28d8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147859"
---
# <a name="ltheadersgt"></a><span data-ttu-id="c46fa-102">&lt;標頭&gt;</span><span class="sxs-lookup"><span data-stu-id="c46fa-102">&lt;headers&gt;</span></span>
<span data-ttu-id="c46fa-103">端點除了可以由其基本 URI 定址之外，還可由一個或多個 SOAP 標頭定址。</span><span class="sxs-lookup"><span data-stu-id="c46fa-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="c46fa-104">有些情況適用這種方式，例如 SOAP 媒介，此時端點需要此端點的用戶端加入目標為媒介的 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="c46fa-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="c46fa-105">這個組態項目可用於定義此類自訂位址標題。</span><span class="sxs-lookup"><span data-stu-id="c46fa-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="c46fa-106">端點標頭集合中的項目是使用者定義的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="c46fa-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="c46fa-107">每個項目必須為格式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="c46fa-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="c46fa-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c46fa-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="c46fa-109">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="c46fa-109">\<client></span></span>  
<span data-ttu-id="c46fa-110">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="c46fa-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c46fa-111">語法</span><span class="sxs-lookup"><span data-stu-id="c46fa-111">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c46fa-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c46fa-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c46fa-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c46fa-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c46fa-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c46fa-114">Attributes</span></span>  
 <span data-ttu-id="c46fa-115">無。</span><span class="sxs-lookup"><span data-stu-id="c46fa-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c46fa-116">子元素</span><span class="sxs-lookup"><span data-stu-id="c46fa-116">Child Elements</span></span>  
  
|<span data-ttu-id="c46fa-117">項目</span><span class="sxs-lookup"><span data-stu-id="c46fa-117">Element</span></span>|<span data-ttu-id="c46fa-118">描述</span><span class="sxs-lookup"><span data-stu-id="c46fa-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c46fa-119">Region</span><span class="sxs-lookup"><span data-stu-id="c46fa-119">Region</span></span>||  
|<span data-ttu-id="c46fa-120">成員</span><span class="sxs-lookup"><span data-stu-id="c46fa-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="c46fa-121">父項目</span><span class="sxs-lookup"><span data-stu-id="c46fa-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c46fa-122">項目</span><span class="sxs-lookup"><span data-stu-id="c46fa-122">Element</span></span>|<span data-ttu-id="c46fa-123">描述</span><span class="sxs-lookup"><span data-stu-id="c46fa-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c46fa-124">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="c46fa-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="c46fa-125">設定不同類型的端點。</span><span class="sxs-lookup"><span data-stu-id="c46fa-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c46fa-126">備註</span><span class="sxs-lookup"><span data-stu-id="c46fa-126">Remarks</span></span>  
 <span data-ttu-id="c46fa-127">選用標頭會提供更多詳細的定址資訊來識別端點或與端點互動。</span><span class="sxs-lookup"><span data-stu-id="c46fa-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="c46fa-128">例如，標頭會指出如何處理傳入訊息、端點應該將回覆訊息傳送到哪裡，或是當有多個執行個體可用時，要使用哪個服務執行個體來處理來自特定使用者的傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="c46fa-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c46fa-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c46fa-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="c46fa-130">端點：位址、 繫結和合約</span><span class="sxs-lookup"><span data-stu-id="c46fa-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
