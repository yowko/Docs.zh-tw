---
title: "使用 HTTP、TCP 或具名管道的非同步案例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ad7159e63b472b4ef30189cc36e1a0c493c9c1c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="9fbb7-102">使用 HTTP、TCP 或具名管道的非同步案例</span><span class="sxs-lookup"><span data-stu-id="9fbb7-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>
<span data-ttu-id="9fbb7-103">本主題會說明各種非同步要求/回覆案例的活動和傳輸，以及使用 HTTP、TCP 或具名管道的執行緒要求。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="9fbb7-104">無錯誤的非同步要求/回覆</span><span class="sxs-lookup"><span data-stu-id="9fbb7-104">Asynchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="9fbb7-105">本章節會說明非同步要求/回覆案例的活動和傳輸，以及多執行緒的用戶端。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="9fbb7-106">當 `beginCall` 傳回，而且 `endCall` 傳回時，呼叫端活動便會終止。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="9fbb7-107">如果有呼叫回呼，該回呼就會傳回。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="9fbb7-108">當 `beginCall` 傳回，而且 `endCall` 傳回，或是當回呼 (若有從活動呼叫) 傳回時，呼叫的活動便會終止。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="9fbb7-109">沒有回呼的非同步用戶端</span><span class="sxs-lookup"><span data-stu-id="9fbb7-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="9fbb7-110">兩端皆啟用傳播，使用 HTTP</span><span class="sxs-lookup"><span data-stu-id="9fbb7-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  
 <span data-ttu-id="9fbb7-111">![非同步案例](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")</span><span class="sxs-lookup"><span data-stu-id="9fbb7-111">![Asynchronous scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")</span></span>  
  
 <span data-ttu-id="9fbb7-112">圖 1。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-112">Figure 1.</span></span> <span data-ttu-id="9fbb7-113">非同步用戶端，沒有回呼， `propagateActivity` = `true`兩端，HTTP</span><span class="sxs-lookup"><span data-stu-id="9fbb7-113">Asynchronous client, no callback, `propagateActivity`=`true` on both sides, HTTP</span></span>  
  
 <span data-ttu-id="9fbb7-114">如果`propagateActivity` = `true`，ProcessMessage 會指示要傳輸哪一個 ProcessAction 活動。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-114">If `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="9fbb7-115">若是 HTTP 架構案例，ReceiveBytes 會叫用於第一個要傳送的訊息上，並隨該要求的存留期而保留。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-115">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="9fbb7-116">任何一端的傳播已停用，使用 HTTP</span><span class="sxs-lookup"><span data-stu-id="9fbb7-116">Propagation is Disabled on Either Sides, using HTTP</span></span>  
 <span data-ttu-id="9fbb7-117">如果`propagateActivity` = `false`任一邊，ProcessMessage 不會指示要傳輸哪一個 ProcessAction 活動。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-117">If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="9fbb7-118">因此，這時會叫用含有新識別碼的新暫存 ProcessAction 活動。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-118">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="9fbb7-119">當非同步回應符合 ServiceModel 程式碼中的要求時，該活動識別碼即可從本機內容進行擷取。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-119">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="9fbb7-120">實際的 ProcessAction 活動可以透過該識別碼加以傳輸。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-120">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 <span data-ttu-id="9fbb7-121">![使用 HTTP &#47; 的非同步情節TCP &#47;具名管道](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")</span><span class="sxs-lookup"><span data-stu-id="9fbb7-121">![Asynchronous scenarios using HTTP&#47;TCP&#47;Named Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")</span></span>  
  
 <span data-ttu-id="9fbb7-122">圖 2。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-122">Figure 2.</span></span> <span data-ttu-id="9fbb7-123">非同步用戶端，沒有回呼， `propagateActivity` = `false`任一端，HTTP</span><span class="sxs-lookup"><span data-stu-id="9fbb7-123">Asynchronous client, no callback, `propagateActivity`=`false` on either side, HTTP</span></span>  
  
 <span data-ttu-id="9fbb7-124">若是 HTTP 架構案例，ReceiveBytes 會叫用於第一個要傳送的訊息上，並隨該要求的存留期而保留。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-124">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="9fbb7-125">非同步用戶端上建立 「 處理動作 」 活動時`propagateActivity` = `false`呼叫端或被呼叫端，和回應訊息不包含動作標頭。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-125">A Process Action activity is created on an asynchronous client when `propagateActivity`=`false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="9fbb7-126">兩端皆啟用傳播，使用 TCP 或具名管道</span><span class="sxs-lookup"><span data-stu-id="9fbb7-126">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="9fbb7-127">![使用 HTTP &#47; 的非同步情節TCP &#47;具名管道](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")</span><span class="sxs-lookup"><span data-stu-id="9fbb7-127">![Asynchronous scenarios using HTTP&#47;TCP&#47;Named Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")</span></span>  
  
 <span data-ttu-id="9fbb7-128">圖 3.</span><span class="sxs-lookup"><span data-stu-id="9fbb7-128">Figure 3.</span></span> <span data-ttu-id="9fbb7-129">非同步用戶端，沒有回呼， `propagateActivity` = `true`雙方具名管道 /TCP</span><span class="sxs-lookup"><span data-stu-id="9fbb7-129">Asynchronous client, no callback, `propagateActivity`=`true` on both sides, Named-Pipe/TCP</span></span>  
  
 <span data-ttu-id="9fbb7-130">若是具名管道或 TCP 架構案例，ReceiveBytes 會叫用於用戶端開啟時，並隨該連線的存留期而保留。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-130">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="9fbb7-131">類似於圖 1，如果`propagateActivity` = `true`，ProcessMessage 會指示要傳輸哪一個 ProcessAction 活動。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-131">Similar to Figure 1, if `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="9fbb7-132">任何一端的傳播已停用，使用 TCP 或具名管道</span><span class="sxs-lookup"><span data-stu-id="9fbb7-132">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="9fbb7-133">若是具名管道或 TCP 架構案例，ReceiveBytes 會叫用於用戶端開啟時，並隨該連線的存留期而保留。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-133">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="9fbb7-134">類似於 Fig.2，如果`propagateActivity` = `false`任一邊，ProcessMessage 不會指示要傳輸哪一個 ProcessAction 活動。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-134">Similar to Fig.2, If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="9fbb7-135">因此，這時會叫用含有新識別碼的新暫存 ProcessAction 活動。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-135">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="9fbb7-136">當非同步回應符合 ServiceModel 程式碼中的要求時，該活動識別碼即可從本機內容進行擷取。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-136">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="9fbb7-137">實際的 ProcessAction 活動可以透過該識別碼加以傳輸。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-137">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 <span data-ttu-id="9fbb7-138">![使用 HTTP &#47; 的非同步情節TCP &#47;具名管道](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")</span><span class="sxs-lookup"><span data-stu-id="9fbb7-138">![Asynchronous scenarios using HTTP&#47;TCP&#47; Named Pipes](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")</span></span>  
  
 <span data-ttu-id="9fbb7-139">圖 4。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-139">Figure 4.</span></span> <span data-ttu-id="9fbb7-140">非同步用戶端，沒有回呼， `propagateActivity` = `false`任一端、 具名管道 /TCP</span><span class="sxs-lookup"><span data-stu-id="9fbb7-140">Asynchronous client, no callback, `propagateActivity`=`false` on either side, Named-Pipe/TCP</span></span>  
  
### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="9fbb7-141">有回呼的非同步用戶端</span><span class="sxs-lookup"><span data-stu-id="9fbb7-141">Asynchronous client with Callback</span></span>  
 <span data-ttu-id="9fbb7-142">這個案例會為回呼和 `endCall` 新增活動 G 和 A’，及其傳入/傳出。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-142">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="9fbb7-143">本章節只有示範使用 HTTP 與`propragateActivity` = `true`。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-143">This section only demonstrates using HTTP with `propragateActivity`=`true`.</span></span> <span data-ttu-id="9fbb7-144">不過，其他的活動和傳輸也適用於其他情況 (也就是`propagateActivity` = `false`，使用 TCP 或具名管道)。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-144">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="9fbb7-145">當用戶端呼叫使用者程式碼以通知結果已準備好時，該回呼就會建立新活動 (G)。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-145">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="9fbb7-146">然後，使用者程式碼便會從回呼內部 (如圖 5 所示) 或回呼外部 (圖 6) 呼叫 `endCall`。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-146">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="9fbb7-147">因為不知道哪個使用者活動`endCall`呼叫，此活動會標示為`A’`。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-147">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="9fbb7-148">A’ 有可能相同或不同於 A。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-148">It is possible that A’ can be identical to or different from A.</span></span>  
  
 <span data-ttu-id="9fbb7-149">![非同步案例](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")</span><span class="sxs-lookup"><span data-stu-id="9fbb7-149">![Asynchronous scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")</span></span>  
  
 <span data-ttu-id="9fbb7-150">圖 5。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-150">Figure 5.</span></span> <span data-ttu-id="9fbb7-151">具有回呼的非同步用戶端，從回呼呼叫 `endCall`</span><span class="sxs-lookup"><span data-stu-id="9fbb7-151">Asynchronous client with callback, `endCall` in Callback</span></span>  
  
 <span data-ttu-id="9fbb7-152">![非同步案例](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")</span><span class="sxs-lookup"><span data-stu-id="9fbb7-152">![Asynchronous Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")</span></span>  
  
 <span data-ttu-id="9fbb7-153">圖 6。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-153">Figure 6.</span></span> <span data-ttu-id="9fbb7-154">具有回呼的非同步用戶端，從回呼外部呼叫 `endCall`</span><span class="sxs-lookup"><span data-stu-id="9fbb7-154">Asynchronous client with callback, `endCall` outside of Callback</span></span>  
  
### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="9fbb7-155">有回呼的非同步伺服器</span><span class="sxs-lookup"><span data-stu-id="9fbb7-155">Asynchronous Server with Callback</span></span>  
 <span data-ttu-id="9fbb7-156">![使用 HTTP &#47; 的非同步情節TCP &#47;名為 &#45;管道](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")</span><span class="sxs-lookup"><span data-stu-id="9fbb7-156">![Asynchronous scenarios using HTTP&#47;TCP&#47; Named&#45;Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")</span></span>  
  
 <span data-ttu-id="9fbb7-157">圖 7。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-157">Figure 7.</span></span> <span data-ttu-id="9fbb7-158">有回呼的非同步伺服器</span><span class="sxs-lookup"><span data-stu-id="9fbb7-158">Asynchronous server, with callback</span></span>  
  
 <span data-ttu-id="9fbb7-159">通道堆疊會在訊息接收時回呼用戶端：這個處理的追蹤會由 ProcessRequest 活動本身發出。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-159">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="9fbb7-160">含有錯誤的非同步要求/回覆</span><span class="sxs-lookup"><span data-stu-id="9fbb7-160">Asynchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="9fbb7-161">`endCall` 期間會收到錯誤 (Fault) 訊息錯誤 (Error)。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-161">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="9fbb7-162">在其他方面，活動和傳輸都與上述案例相似。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-162">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="9fbb7-163">不一定具有錯誤的非同步單向</span><span class="sxs-lookup"><span data-stu-id="9fbb7-163">Asynchronous One-Way with or without Errors</span></span>  
 <span data-ttu-id="9fbb7-164">沒有任何回應或錯誤傳回到用戶端。</span><span class="sxs-lookup"><span data-stu-id="9fbb7-164">No response or fault is returned to the client.</span></span>
