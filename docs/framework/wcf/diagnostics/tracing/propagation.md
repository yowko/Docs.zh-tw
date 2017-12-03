---
title: "傳播"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a993ec836417906229e47b7f415f4aee8b1a9eb1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="propagation"></a><span data-ttu-id="ae119-102">傳播</span><span class="sxs-lookup"><span data-stu-id="ae119-102">Propagation</span></span>
<span data-ttu-id="ae119-103">本主題描述 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 追蹤模型中的活動傳播。</span><span class="sxs-lookup"><span data-stu-id="ae119-103">This topic describes activity propagation in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="ae119-104">使用傳播將端點上的活動相互關聯</span><span class="sxs-lookup"><span data-stu-id="ae119-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="ae119-105">傳播會針對應用程式端點間的相同處理單位 (例如，要求)，將錯誤追蹤的直接相互關聯提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="ae119-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="ae119-106">在不同端點針對相同處理單位發出的錯誤會組成相同的活動群組，即使是跨應用程式定義域亦然。</span><span class="sxs-lookup"><span data-stu-id="ae119-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="ae119-107">這項工作是藉由傳播訊息標頭中的活動識別碼來達成。</span><span class="sxs-lookup"><span data-stu-id="ae119-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="ae119-108">因此，如果用戶端因為伺服器發生內部錯誤而逾時，則基於直接的相互關聯，這兩個錯誤都會出現在相同的活動中。</span><span class="sxs-lookup"><span data-stu-id="ae119-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="ae119-109">若要執行這項工作，請使用 `ActivityTracing` 設定，如前述範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae119-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="ae119-110">此外，還要在所有端點上設定 `propagateActivity` 追蹤來源的 `System.ServiceModel` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ae119-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="ae119-111">活動傳播是可設定的功能，這項功能會促使 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 將標頭新增至傳出訊息，而其中會包含 TLS 上的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="ae119-111">Activity propagation is a configurable capability that causes [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="ae119-112">將這個識別碼包含在對伺服器端的後續追蹤中，我們就可以將用戶端和伺服器活動相互關聯起來。</span><span class="sxs-lookup"><span data-stu-id="ae119-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="ae119-113">傳播定義</span><span class="sxs-lookup"><span data-stu-id="ae119-113">Propagation Definition</span></span>  
 <span data-ttu-id="ae119-114">如果下列所有條件都成立，就會將活動 M 的 gAId 傳播至活動 N。</span><span class="sxs-lookup"><span data-stu-id="ae119-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
-   <span data-ttu-id="ae119-115">N 是因為 M 而建立的</span><span class="sxs-lookup"><span data-stu-id="ae119-115">N is created because of M</span></span>  
  
-   <span data-ttu-id="ae119-116">N 知道 M 的 gAId</span><span class="sxs-lookup"><span data-stu-id="ae119-116">M’s gAId is known to N</span></span>  
  
-   <span data-ttu-id="ae119-117">N 的 gAId 等於 M 的 gAId。</span><span class="sxs-lookup"><span data-stu-id="ae119-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="ae119-118">gAId 是透過 ActivityId 訊息標頭所傳播，如下列 XML 結構描述所示。</span><span class="sxs-lookup"><span data-stu-id="ae119-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="ae119-119">下列是訊息標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="ae119-119">The following is an example of the message header.</span></span>  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"     
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"   
  
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous  
          </a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="ae119-120">傳播和活動界限</span><span class="sxs-lookup"><span data-stu-id="ae119-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="ae119-121">在端點之間傳播活動識別碼時，訊息接收者會將「開始」和「停止」追蹤與這個 (傳播) 活動識別碼一起發出。</span><span class="sxs-lookup"><span data-stu-id="ae119-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="ae119-122">因此，會有包含來自每個追蹤來源之 gAId 的「開始」和「停止」追蹤。</span><span class="sxs-lookup"><span data-stu-id="ae119-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="ae119-123">如果數個端點位於相同的處理序且使用相同的追蹤來源名稱，就會建立多個具有相同 lAId (相同 gAId、相同追蹤來源、相同處理序) 的「開始」和「停止」追蹤。</span><span class="sxs-lookup"><span data-stu-id="ae119-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="ae119-124">同步處理</span><span class="sxs-lookup"><span data-stu-id="ae119-124">Synchronization</span></span>  
 <span data-ttu-id="ae119-125">若要在執行於不同電腦的端點之間同步處理事件，請將 CorrelationId 新增至訊息中所傳播的 ActivityId 標頭。</span><span class="sxs-lookup"><span data-stu-id="ae119-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="ae119-126">工具可以使用這個識別碼，在時鐘不一致的電腦之間同步處理事件。</span><span class="sxs-lookup"><span data-stu-id="ae119-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="ae119-127">具體來說，「服務追蹤檢視器」工具會使用這個識別碼來顯示端點之間的訊息流動。</span><span class="sxs-lookup"><span data-stu-id="ae119-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae119-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae119-128">See Also</span></span>  
 [<span data-ttu-id="ae119-129">設定追蹤</span><span class="sxs-lookup"><span data-stu-id="ae119-129">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="ae119-130">使用服務追蹤檢視器檢視相關追蹤並進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="ae119-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="ae119-131">端對端追蹤案例</span><span class="sxs-lookup"><span data-stu-id="ae119-131">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="ae119-132">服務追蹤檢視器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="ae119-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
