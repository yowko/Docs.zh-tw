---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399405"
---
# \<transactedBatching>

<span data-ttu-id="82210-101">指定是否支援接收作業的交易批次處理。</span><span class="sxs-lookup"><span data-stu-id="82210-101">Specifies whether transaction batching is supported for receive operations.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**  

## <a name="syntax"></a><span data-ttu-id="82210-102">語法</span><span class="sxs-lookup"><span data-stu-id="82210-102">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="82210-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="82210-103">Attributes and Elements</span></span>

<span data-ttu-id="82210-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="82210-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="82210-105">屬性</span><span class="sxs-lookup"><span data-stu-id="82210-105">Attributes</span></span>

|<span data-ttu-id="82210-106">屬性</span><span class="sxs-lookup"><span data-stu-id="82210-106">Attribute</span></span>|<span data-ttu-id="82210-107">描述</span><span class="sxs-lookup"><span data-stu-id="82210-107">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="82210-108">整數，指定可在一個異動中批次處理的接收作業數目上限。</span><span class="sxs-lookup"><span data-stu-id="82210-108">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="82210-109">預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="82210-109">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="82210-110">子元素</span><span class="sxs-lookup"><span data-stu-id="82210-110">Child Elements</span></span>

<span data-ttu-id="82210-111">無。</span><span class="sxs-lookup"><span data-stu-id="82210-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="82210-112">父項目</span><span class="sxs-lookup"><span data-stu-id="82210-112">Parent Elements</span></span>

|<span data-ttu-id="82210-113">元素</span><span class="sxs-lookup"><span data-stu-id="82210-113">Element</span></span>|<span data-ttu-id="82210-114">描述</span><span class="sxs-lookup"><span data-stu-id="82210-114">Description</span></span>|
|-------------|-----------------|
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="82210-115">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="82210-115">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="82210-116">備註</span><span class="sxs-lookup"><span data-stu-id="82210-116">Remarks</span></span>

<span data-ttu-id="82210-117">以異動批次設定的傳輸，會嘗試將數個接收作業批次到一個異動中。</span><span class="sxs-lookup"><span data-stu-id="82210-117">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="82210-118">如此一來，即可避免在每個接收作業中建立並認可異動時的相對高成本。</span><span class="sxs-lookup"><span data-stu-id="82210-118">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="82210-119">範例</span><span class="sxs-lookup"><span data-stu-id="82210-119">Example</span></span>

<span data-ttu-id="82210-120">下列範例會示範如何在組態檔中將交易的批次處理行為加入至服務。</span><span class="sxs-lookup"><span data-stu-id="82210-120">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="82210-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82210-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
