---
title: "單向服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d023d3623777a93cf72715410aed87fe8a63ee5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="one-way-services"></a><span data-ttu-id="9f0bb-102">單向服務</span><span class="sxs-lookup"><span data-stu-id="9f0bb-102">One-Way Services</span></span>
<span data-ttu-id="9f0bb-103">服務作業的預設行為是要求-回覆模式。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-103">The default behavior of a service operation is the request-reply pattern.</span></span> <span data-ttu-id="9f0bb-104">在要求-回覆模式中，用戶端也都會等候回覆訊息，即使該服務作業已透過程式碼表示為 `void` 方法也是如此。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-104">In a request-reply pattern, the client waits for the reply message, even if the service operation is represented in code as a `void` method.</span></span> <span data-ttu-id="9f0bb-105">在單向作業中，只會傳輸一則訊息。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-105">With a one-way operation, only one message is transmitted.</span></span> <span data-ttu-id="9f0bb-106">接收者不會傳送回覆訊息，傳送者也不會期待回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-106">The receiver does not send a reply message, nor does the sender expect one.</span></span>  
  
 <span data-ttu-id="9f0bb-107">使用單向設計模式：</span><span class="sxs-lookup"><span data-stu-id="9f0bb-107">Use the one-way design pattern:</span></span>  
  
-   <span data-ttu-id="9f0bb-108">當用戶端必須呼叫作業，而且不受作業層級之作業結果影響時。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-108">When the client must call operations and is not affected by the result of the operation at the operation level.</span></span>  
  
-   <span data-ttu-id="9f0bb-109">當使用 <xref:System.ServiceModel.NetMsmqBinding> 或 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 類別時。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-109">When using the <xref:System.ServiceModel.NetMsmqBinding> or the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> class.</span></span> <span data-ttu-id="9f0bb-110">([!INCLUDE[crabout](../../../../includes/crabout-md.md)]此案例中，請參閱[WCF 中的佇列](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)。)</span><span class="sxs-lookup"><span data-stu-id="9f0bb-110">([!INCLUDE[crabout](../../../../includes/crabout-md.md)] this scenario, see [Queues in WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)</span></span>  
  
 <span data-ttu-id="9f0bb-111">當作業為單向時，就不存在將錯誤資訊帶回到用戶端的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-111">When an operation is one-way, there is no response message to carry error information back to the client.</span></span> <span data-ttu-id="9f0bb-112">錯誤狀況的偵測方式，可以是透過使用基礎繫結的功能 (例如可靠工作階段)，或是設計使用兩個單向作業的雙工服務合約來進行，而前述的雙工服務會包含一個會從用戶端到服務來呼叫服務作業的單向合約，另一個介於服務與用戶端之間的單向合約，則可讓服務使用用戶端所實作的回呼來將錯誤傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-112">You can detect error conditions by using features of the underlying binding, such as reliable sessions, or by designing a duplex service contract that uses two one-way operations—a one-way contract from the client to the service to call service operation and another one-way contract between the service and the client so that the service can send back faults to the client using a callback that the client implements.</span></span>  
  
 <span data-ttu-id="9f0bb-113">若要建立單向服務合約，請定義您的服務合約，將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到每個作業，並將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 屬性設定為 `true`，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-113">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="9f0bb-114">如需完整範例，請參閱[單向](../../../../docs/framework/wcf/samples/one-way.md)範例。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-114">For a complete example, see the [One-Way](../../../../docs/framework/wcf/samples/one-way.md) sample.</span></span>  
  
## <a name="clients-blocking-with-one-way-operations"></a><span data-ttu-id="9f0bb-115">用戶端封鎖使用單向作業</span><span class="sxs-lookup"><span data-stu-id="9f0bb-115">Clients Blocking with One-Way Operations</span></span>  
 <span data-ttu-id="9f0bb-116">您必須瞭解，儘管有些單向應用程式會在傳出資料寫入至網路連線時立即傳回，但在許多狀況下，繫結或服務的實作可能會導致 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端封鎖使用單向作業。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-116">It is important to realize that while some one-way applications return as soon as the outbound data is written to the network connection, in several scenarios the implementation of a binding or of a service can cause a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client to block using one-way operations.</span></span> <span data-ttu-id="9f0bb-117">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式中，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件必須等到傳出資料已經寫入網路連線之後才會傳回。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-117">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client applications, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client object does not return until the outbound data has been written to the network connection.</span></span> <span data-ttu-id="9f0bb-118">包括單向作業的所有訊息交換模式都是如此；這表示在將資料寫入至傳輸時所發生的任何問題，都會導致用戶端無法傳回。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-118">This is true for all message exchange patterns, including one-way operations; this means that any problem writing the data to the transport prevents the client from returning.</span></span> <span data-ttu-id="9f0bb-119">根據不同的問題，此結果可能會是在傳送訊息至服務時發生例外狀況或延遲。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-119">Depending upon the problem, the result could be an exception or a delay in sending messages to the service.</span></span>  
  
 <span data-ttu-id="9f0bb-120">例如，如果傳輸找不到該端點，便會擲回 <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> 例外狀況而不會發生什麼延遲。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-120">For example, if the transport cannot find the endpoint, a <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> exception is thrown without much delay.</span></span> <span data-ttu-id="9f0bb-121">然而，服務也可能因為某些原因而無法從線上讀取資料，進而導致用戶端傳輸傳送作業無法傳回。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-121">However, it is also possible that the service is unable to read the data off the wire for some reason, which prevents the client transport send operation from returning.</span></span> <span data-ttu-id="9f0bb-122">在這些情況下，如果超過用戶端傳輸繫結上的 <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> 期限，便會擲回 <xref:System.TimeoutException?displayProperty=nameWithType>，但是必須等到已經超過逾時期限才會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-122">In these cases, if the <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> period on the client transport binding is exceeded, a <xref:System.TimeoutException?displayProperty=nameWithType> is thrown—but not until the timeout period has been exceeded.</span></span> <span data-ttu-id="9f0bb-123">另外一種可能情形，則是出現在服務位置上的訊息多到服務無法將其處理成通過特定點。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-123">It is also possible to fire so many messages at a service that the service cannot process them past a certain point.</span></span> <span data-ttu-id="9f0bb-124">在此情況下，單向用戶端會進行封鎖，直到服務能夠處理訊息，或是擲回例外狀況為止。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-124">In this case, too, the one-way client blocks until the service can process the messages or until an exception is thrown.</span></span>  
  
 <span data-ttu-id="9f0bb-125">類似的情況會發生在服務 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.ServiceModel.ConcurrencyMode.Single>，而繫結使用工作階段的狀況下。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-125">Another variation is the situation in which the service <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> property is set to <xref:System.ServiceModel.ConcurrencyMode.Single> and the binding uses sessions.</span></span> <span data-ttu-id="9f0bb-126">在此情況下，發送器會強制排序傳入訊息 (工作階段的需求)，進而阻止從網路讀取後來的訊息，直到服務已處理過該工作階段的先前訊息才會停止此狀況。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-126">In this case, the dispatcher enforces ordering on the incoming messages (a requirement of sessions), which prevents subsequent messages from being read off the network until the service has processed the preceding message for that session.</span></span> <span data-ttu-id="9f0bb-127">同樣地，用戶端會進行封鎖，不過是否會發生例外狀況則取決於服務是否能在用戶端的逾時設定前處理等候中的資料。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-127">Again, the client blocks, but whether an exception occurs depends upon whether the service is able to process the waiting data prior to the timeout settings on the client.</span></span>  
  
 <span data-ttu-id="9f0bb-128">您可以在用戶端物件與用戶端傳輸的傳送作業之間插入緩衝區，以便稍微緩解這個問題。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-128">You can mitigate some of this problem by inserting a buffer between the client object and the client transport's send operation.</span></span> <span data-ttu-id="9f0bb-129">例如，使用非同步呼叫或使用記憶體中的訊息佇列，都可讓用戶端物件能夠快速傳回。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-129">For example, using asynchronous calls or using an in-memory message queue can enable the client object to return quickly.</span></span> <span data-ttu-id="9f0bb-130">兩種處理方法都可以增加功能，不過執行緒集區與訊息佇列的大小仍然會強制執行限制。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-130">Both approaches may increase functionality, but the size of the thread pool and the message queue still enforce limits.</span></span>  
  
 <span data-ttu-id="9f0bb-131">因此，建議的做法是檢查服務及用戶端上的各種控制項，然後測試您的應用程式案例以判斷兩端的最佳組態。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-131">It is recommended, instead, that you examine the various controls on the service as well as on the client, and then test your application scenarios to determine the best configuration on either side.</span></span> <span data-ttu-id="9f0bb-132">例如，如果使用工作階段會封鎖服務上的訊息處理，您可以將 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.ServiceModel.InstanceContextMode.PerCall> 以使每則訊息都能由不同的服務執行個體處理，並將 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設定為 <xref:System.ServiceModel.ConcurrencyMode.Multiple>，以便一次讓一個以上的執行緒發送訊息。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-132">For example, if the use of sessions is blocking the processing of messages on your service, you can set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.InstanceContextMode.PerCall> so that each message can be processed by a different service instance, and set the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> to <xref:System.ServiceModel.ConcurrencyMode.Multiple> in order to allow more than one thread to dispatch messages at a time.</span></span> <span data-ttu-id="9f0bb-133">另一種處理方法則是增加服務與用戶端繫結的讀取配額。</span><span class="sxs-lookup"><span data-stu-id="9f0bb-133">Another approach is to increase the read quotas of the service and client bindings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f0bb-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="9f0bb-134">See Also</span></span>  
 [<span data-ttu-id="9f0bb-135">單向</span><span class="sxs-lookup"><span data-stu-id="9f0bb-135">One-Way</span></span>](../../../../docs/framework/wcf/samples/one-way.md)
