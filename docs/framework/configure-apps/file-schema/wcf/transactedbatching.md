---
title: '&lt;transactedBatching&gt;'
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: f0cf0b78ddcbd3214e30a36ce7641d115275a265
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="c51b4-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="c51b4-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="c51b4-103">指定是否支援接收作業的異動批次處理。</span><span class="sxs-lookup"><span data-stu-id="c51b4-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="c51b4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c51b4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c51b4-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c51b4-105">\<behaviors></span></span>  
<span data-ttu-id="c51b4-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c51b4-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="c51b4-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c51b4-107">\<behavior></span></span>  
<span data-ttu-id="c51b4-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="c51b4-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c51b4-109">語法</span><span class="sxs-lookup"><span data-stu-id="c51b4-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c51b4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c51b4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c51b4-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c51b4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c51b4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c51b4-112">Attributes</span></span>  
  
|<span data-ttu-id="c51b4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c51b4-113">Attribute</span></span>|<span data-ttu-id="c51b4-114">描述</span><span class="sxs-lookup"><span data-stu-id="c51b4-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="c51b4-115">整數，指定可在一個交易中批次處理的接收作業數目上限。</span><span class="sxs-lookup"><span data-stu-id="c51b4-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="c51b4-116">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="c51b4-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c51b4-117">子項目</span><span class="sxs-lookup"><span data-stu-id="c51b4-117">Child Elements</span></span>  
 <span data-ttu-id="c51b4-118">無。</span><span class="sxs-lookup"><span data-stu-id="c51b4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c51b4-119">父項目</span><span class="sxs-lookup"><span data-stu-id="c51b4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c51b4-120">項目</span><span class="sxs-lookup"><span data-stu-id="c51b4-120">Element</span></span>|<span data-ttu-id="c51b4-121">描述</span><span class="sxs-lookup"><span data-stu-id="c51b4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c51b4-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c51b4-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c51b4-123">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="c51b4-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c51b4-124">備註</span><span class="sxs-lookup"><span data-stu-id="c51b4-124">Remarks</span></span>  
 <span data-ttu-id="c51b4-125">以異動批次設定的傳輸，會嘗試將數個接收作業批次到一個異動中。</span><span class="sxs-lookup"><span data-stu-id="c51b4-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="c51b4-126">如此一來，即可避免在每個接收作業中建立並認可異動時的相對高成本。</span><span class="sxs-lookup"><span data-stu-id="c51b4-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c51b4-127">範例</span><span class="sxs-lookup"><span data-stu-id="c51b4-127">Example</span></span>  
 <span data-ttu-id="c51b4-128">下列範例會示範如何在組態檔中將交易的批次處理行為加入至服務。</span><span class="sxs-lookup"><span data-stu-id="c51b4-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <host>  
        <baseAddresses>  
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="c51b4-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c51b4-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
