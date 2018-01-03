---
title: '&lt;transactedBatching&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fc5d5cc77fcb227efd36106f1f8cb31efad24cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="cf008-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="cf008-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="cf008-103">指定是否支援接收作業的異動批次處理。</span><span class="sxs-lookup"><span data-stu-id="cf008-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="cf008-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cf008-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf008-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cf008-105">\<behaviors></span></span>  
<span data-ttu-id="cf008-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cf008-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="cf008-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cf008-107">\<behavior></span></span>  
<span data-ttu-id="cf008-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="cf008-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf008-109">語法</span><span class="sxs-lookup"><span data-stu-id="cf008-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf008-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cf008-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cf008-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cf008-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf008-112">屬性</span><span class="sxs-lookup"><span data-stu-id="cf008-112">Attributes</span></span>  
  
|<span data-ttu-id="cf008-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cf008-113">Attribute</span></span>|<span data-ttu-id="cf008-114">描述</span><span class="sxs-lookup"><span data-stu-id="cf008-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="cf008-115">整數，指定可在一個交易中批次處理的接收作業數目上限。</span><span class="sxs-lookup"><span data-stu-id="cf008-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="cf008-116">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="cf008-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf008-117">子元素</span><span class="sxs-lookup"><span data-stu-id="cf008-117">Child Elements</span></span>  
 <span data-ttu-id="cf008-118">無。</span><span class="sxs-lookup"><span data-stu-id="cf008-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf008-119">父項目</span><span class="sxs-lookup"><span data-stu-id="cf008-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cf008-120">項目</span><span class="sxs-lookup"><span data-stu-id="cf008-120">Element</span></span>|<span data-ttu-id="cf008-121">描述</span><span class="sxs-lookup"><span data-stu-id="cf008-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf008-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cf008-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cf008-123">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="cf008-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf008-124">備註</span><span class="sxs-lookup"><span data-stu-id="cf008-124">Remarks</span></span>  
 <span data-ttu-id="cf008-125">以異動批次設定的傳輸，會嘗試將數個接收作業批次到一個異動中。</span><span class="sxs-lookup"><span data-stu-id="cf008-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="cf008-126">如此一來，即可避免在每個接收作業中建立並認可交易時的相對高成本。</span><span class="sxs-lookup"><span data-stu-id="cf008-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf008-127">範例</span><span class="sxs-lookup"><span data-stu-id="cf008-127">Example</span></span>  
 <span data-ttu-id="cf008-128">下列範例會示範如何在組態檔中將交易的批次處理行為加入至服務。</span><span class="sxs-lookup"><span data-stu-id="cf008-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf008-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf008-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
