---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 12369f1053638583a3864fab396869d0e7045732
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918669"
---
# <a name="transactedbatching"></a><span data-ttu-id="9c8fc-101">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="9c8fc-101">\<transactedBatching></span></span>

<span data-ttu-id="9c8fc-102">指定是否支援接收作業的交易批次處理。</span><span class="sxs-lookup"><span data-stu-id="9c8fc-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="9c8fc-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9c8fc-103">\<system.ServiceModel></span></span>\
<span data-ttu-id="9c8fc-104">\<行為 > </span><span class="sxs-lookup"><span data-stu-id="9c8fc-104">\<behaviors></span></span>\
<span data-ttu-id="9c8fc-105">\<endpointBehaviors > </span><span class="sxs-lookup"><span data-stu-id="9c8fc-105">\<endpointBehaviors></span></span>\
<span data-ttu-id="9c8fc-106">\<行為 > </span><span class="sxs-lookup"><span data-stu-id="9c8fc-106">\<behavior></span></span>\
<span data-ttu-id="9c8fc-107">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="9c8fc-107">\<transactedBatching></span></span>

## <a name="syntax"></a><span data-ttu-id="9c8fc-108">語法</span><span class="sxs-lookup"><span data-stu-id="9c8fc-108">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c8fc-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9c8fc-109">Attributes and Elements</span></span>

<span data-ttu-id="9c8fc-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9c8fc-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c8fc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9c8fc-111">Attributes</span></span>

|<span data-ttu-id="9c8fc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9c8fc-112">Attribute</span></span>|<span data-ttu-id="9c8fc-113">說明</span><span class="sxs-lookup"><span data-stu-id="9c8fc-113">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="9c8fc-114">整數，指定可在一個異動中批次處理的接收作業數目上限。</span><span class="sxs-lookup"><span data-stu-id="9c8fc-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="9c8fc-115">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="9c8fc-115">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9c8fc-116">子元素</span><span class="sxs-lookup"><span data-stu-id="9c8fc-116">Child Elements</span></span>

<span data-ttu-id="9c8fc-117">無。</span><span class="sxs-lookup"><span data-stu-id="9c8fc-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9c8fc-118">父項目</span><span class="sxs-lookup"><span data-stu-id="9c8fc-118">Parent Elements</span></span>

|<span data-ttu-id="9c8fc-119">項目</span><span class="sxs-lookup"><span data-stu-id="9c8fc-119">Element</span></span>|<span data-ttu-id="9c8fc-120">描述</span><span class="sxs-lookup"><span data-stu-id="9c8fc-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c8fc-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="9c8fc-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="9c8fc-122">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="9c8fc-122">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9c8fc-123">備註</span><span class="sxs-lookup"><span data-stu-id="9c8fc-123">Remarks</span></span>

<span data-ttu-id="9c8fc-124">以異動批次設定的傳輸，會嘗試將數個接收作業批次到一個異動中。</span><span class="sxs-lookup"><span data-stu-id="9c8fc-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="9c8fc-125">如此一來，即可避免在每個接收作業中建立並認可異動時的相對高成本。</span><span class="sxs-lookup"><span data-stu-id="9c8fc-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="9c8fc-126">範例</span><span class="sxs-lookup"><span data-stu-id="9c8fc-126">Example</span></span>

<span data-ttu-id="9c8fc-127">下列範例會示範如何在組態檔中將交易的批次處理行為加入至服務。</span><span class="sxs-lookup"><span data-stu-id="9c8fc-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
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

## <a name="see-also"></a><span data-ttu-id="9c8fc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c8fc-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
