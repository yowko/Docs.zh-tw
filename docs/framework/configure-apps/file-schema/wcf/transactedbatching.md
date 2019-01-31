---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 1e8ce41a27bd328c861f2f376a89c57bcd035389
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281290"
---
# <a name="transactedbatching"></a><span data-ttu-id="1e809-101">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="1e809-101">\<transactedBatching></span></span>
<span data-ttu-id="1e809-102">指定是否支援接收作業的異動批次處理。</span><span class="sxs-lookup"><span data-stu-id="1e809-102">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="1e809-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1e809-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1e809-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="1e809-104">\<behaviors></span></span>  
<span data-ttu-id="1e809-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1e809-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="1e809-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1e809-106">\<behavior></span></span>  
<span data-ttu-id="1e809-107">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="1e809-107">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e809-108">語法</span><span class="sxs-lookup"><span data-stu-id="1e809-108">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e809-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1e809-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1e809-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1e809-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e809-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1e809-111">Attributes</span></span>  
  
|<span data-ttu-id="1e809-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1e809-112">Attribute</span></span>|<span data-ttu-id="1e809-113">描述</span><span class="sxs-lookup"><span data-stu-id="1e809-113">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="1e809-114">整數，指定可在一個交易中批次處理的接收作業數目上限。</span><span class="sxs-lookup"><span data-stu-id="1e809-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="1e809-115">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="1e809-115">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e809-116">子元素</span><span class="sxs-lookup"><span data-stu-id="1e809-116">Child Elements</span></span>  
 <span data-ttu-id="1e809-117">無。</span><span class="sxs-lookup"><span data-stu-id="1e809-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e809-118">父項目</span><span class="sxs-lookup"><span data-stu-id="1e809-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1e809-119">項目</span><span class="sxs-lookup"><span data-stu-id="1e809-119">Element</span></span>|<span data-ttu-id="1e809-120">描述</span><span class="sxs-lookup"><span data-stu-id="1e809-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e809-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1e809-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1e809-122">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="1e809-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e809-123">備註</span><span class="sxs-lookup"><span data-stu-id="1e809-123">Remarks</span></span>  
 <span data-ttu-id="1e809-124">以異動批次設定的傳輸，會嘗試將數個接收作業批次到一個異動中。</span><span class="sxs-lookup"><span data-stu-id="1e809-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="1e809-125">如此一來，即可避免在每個接收作業中建立並認可異動時的相對高成本。</span><span class="sxs-lookup"><span data-stu-id="1e809-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e809-126">範例</span><span class="sxs-lookup"><span data-stu-id="1e809-126">Example</span></span>  
 <span data-ttu-id="1e809-127">下列範例會示範如何在組態檔中將交易的批次處理行為加入至服務。</span><span class="sxs-lookup"><span data-stu-id="1e809-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="1e809-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e809-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
