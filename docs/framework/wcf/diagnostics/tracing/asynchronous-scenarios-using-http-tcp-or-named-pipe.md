---
title: 使用 HTTP、TCP 或具名管道的非同步案例
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 6ae96c0aac5010adf37eb78ed57d1549885ece58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185777"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="36816-102">使用 HTTP、TCP 或具名管道的非同步案例</span><span class="sxs-lookup"><span data-stu-id="36816-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>
<span data-ttu-id="36816-103">本主題會說明各種非同步要求/回覆案例的活動和傳輸，以及使用 HTTP、TCP 或具名管道的執行緒要求。</span><span class="sxs-lookup"><span data-stu-id="36816-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="36816-104">無錯誤的非同步要求/回覆</span><span class="sxs-lookup"><span data-stu-id="36816-104">Asynchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="36816-105">本章節會說明非同步要求/回覆案例的活動和傳輸，以及多執行緒的用戶端。</span><span class="sxs-lookup"><span data-stu-id="36816-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="36816-106">當 `beginCall` 傳回，而且 `endCall` 傳回時，呼叫端活動便會終止。</span><span class="sxs-lookup"><span data-stu-id="36816-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="36816-107">如果有呼叫回呼，該回呼就會傳回。</span><span class="sxs-lookup"><span data-stu-id="36816-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="36816-108">當 `beginCall` 傳回，而且 `endCall` 傳回，或是當回呼 (若有從活動呼叫) 傳回時，呼叫的活動便會終止。</span><span class="sxs-lookup"><span data-stu-id="36816-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="36816-109">沒有回呼的非同步用戶端</span><span class="sxs-lookup"><span data-stu-id="36816-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="36816-110">兩端皆啟用傳播，使用 HTTP</span><span class="sxs-lookup"><span data-stu-id="36816-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  
 ![無回檔的非同步用戶端，其中傳播活動在兩側設置為 true。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 <span data-ttu-id="36816-112">如果`propagateActivity=true`，進程消息指示要傳輸到哪個進程操作活動。</span><span class="sxs-lookup"><span data-stu-id="36816-112">If `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="36816-113">若是 HTTP 架構案例，ReceiveBytes 會叫用於第一個要傳送的訊息上，並隨該要求的存留期而保留。</span><span class="sxs-lookup"><span data-stu-id="36816-113">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="36816-114">任何一端的傳播已停用，使用 HTTP</span><span class="sxs-lookup"><span data-stu-id="36816-114">Propagation is Disabled on Either Sides, using HTTP</span></span>  
 <span data-ttu-id="36816-115">如果`propagateActivity=false`任一方面，ProcessMessage 並不指示要傳輸到哪個 ProcessAction 活動。</span><span class="sxs-lookup"><span data-stu-id="36816-115">If `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="36816-116">因此，這時會叫用含有新識別碼的新暫存 ProcessAction 活動。</span><span class="sxs-lookup"><span data-stu-id="36816-116">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="36816-117">當非同步回應符合 ServiceModel 程式碼中的要求時，該活動識別碼即可從本機內容進行擷取。</span><span class="sxs-lookup"><span data-stu-id="36816-117">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="36816-118">實際的 ProcessAction 活動可以透過該識別碼加以傳輸。</span><span class="sxs-lookup"><span data-stu-id="36816-118">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![無回檔的非同步用戶端，其中傳播活動設置為 false。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 <span data-ttu-id="36816-120">若是 HTTP 架構案例，ReceiveBytes 會叫用於第一個要傳送的訊息上，並隨該要求的存留期而保留。</span><span class="sxs-lookup"><span data-stu-id="36816-120">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="36816-121">當調用方或被呼叫者時，以及回應訊息`propagateActivity=false`不包含操作標頭時，在非同步用戶端上創建進程操作活動。</span><span class="sxs-lookup"><span data-stu-id="36816-121">A Process Action activity is created on an asynchronous client when `propagateActivity=false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="36816-122">兩端皆啟用傳播，使用 TCP 或具名管道</span><span class="sxs-lookup"><span data-stu-id="36816-122">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  
 ![無回檔的非同步用戶端，其中傳播活動在兩側設置為 true，並命名為管道/TCP。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 <span data-ttu-id="36816-124">若是具名管道或 TCP 架構案例，ReceiveBytes 會叫用於用戶端開啟時，並隨該連線的存留期而保留。</span><span class="sxs-lookup"><span data-stu-id="36816-124">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="36816-125">與第一個圖像類似，如果`propagateActivity=true`"進程消息"指示要傳輸到哪個進程操作活動。</span><span class="sxs-lookup"><span data-stu-id="36816-125">Similar to the first image, if `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="36816-126">任何一端的傳播已停用，使用 TCP 或具名管道</span><span class="sxs-lookup"><span data-stu-id="36816-126">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="36816-127">若是具名管道或 TCP 架構案例，ReceiveBytes 會叫用於用戶端開啟時，並隨該連線的存留期而保留。</span><span class="sxs-lookup"><span data-stu-id="36816-127">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="36816-128">與第二個映射類似，如果`propagateActivity=false`任一方面，ProcessMessage 不會指示要傳輸到哪個 ProcessAction 活動。</span><span class="sxs-lookup"><span data-stu-id="36816-128">Similar to the second image, if `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="36816-129">因此，這時會叫用含有新識別碼的新暫存 ProcessAction 活動。</span><span class="sxs-lookup"><span data-stu-id="36816-129">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="36816-130">當非同步回應符合 ServiceModel 程式碼中的要求時，該活動識別碼即可從本機內容進行擷取。</span><span class="sxs-lookup"><span data-stu-id="36816-130">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="36816-131">實際的 ProcessAction 活動可以透過該識別碼加以傳輸。</span><span class="sxs-lookup"><span data-stu-id="36816-131">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![無回檔的非同步用戶端，其中傳播活動設置為 false，並且具名管道/TCP。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="36816-133">有回呼的非同步用戶端</span><span class="sxs-lookup"><span data-stu-id="36816-133">Asynchronous client with Callback</span></span>  
 <span data-ttu-id="36816-134">這個案例會為回呼和 `endCall` 新增活動 G 和 A’，及其傳入/傳出。</span><span class="sxs-lookup"><span data-stu-id="36816-134">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="36816-135">本節僅演示使用 HTTP`propagateActivity`=`true`與 。</span><span class="sxs-lookup"><span data-stu-id="36816-135">This section only demonstrates using HTTP with `propagateActivity`=`true`.</span></span> <span data-ttu-id="36816-136">但是，其他活動和傳輸也適用于其他情況（即`propagateActivity`=`false`，使用 TCP 或具名管道）。</span><span class="sxs-lookup"><span data-stu-id="36816-136">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="36816-137">當用戶端呼叫使用者程式碼以通知結果已準備好時，該回呼就會建立新活動 (G)。</span><span class="sxs-lookup"><span data-stu-id="36816-137">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="36816-138">然後，使用者程式碼便會從回呼內部 (如圖 5 所示) 或回呼外部 (圖 6) 呼叫 `endCall`。</span><span class="sxs-lookup"><span data-stu-id="36816-138">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="36816-139">由於不知道從哪個使用者活動`endCall`調用，因此此活動被標記為`A’`。</span><span class="sxs-lookup"><span data-stu-id="36816-139">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="36816-140">A’ 有可能相同或不同於 A。</span><span class="sxs-lookup"><span data-stu-id="36816-140">It is possible that A’ can be identical to or different from A.</span></span>  
  
 ![顯示具有回檔的非同步用戶端，在回檔中顯示結束調用。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![顯示具有回檔的非同步用戶端，在外部回檔結束調用。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="36816-143">有回呼的非同步伺服器</span><span class="sxs-lookup"><span data-stu-id="36816-143">Asynchronous Server with Callback</span></span>  
 ![顯示帶回檔的非同步伺服器。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 <span data-ttu-id="36816-145">通道堆疊會在訊息接收時回呼用戶端：這個處理的追蹤會由 ProcessRequest 活動本身發出。</span><span class="sxs-lookup"><span data-stu-id="36816-145">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="36816-146">含有錯誤的非同步要求/回覆</span><span class="sxs-lookup"><span data-stu-id="36816-146">Asynchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="36816-147">`endCall` 期間會收到錯誤 (Fault) 訊息錯誤 (Error)。</span><span class="sxs-lookup"><span data-stu-id="36816-147">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="36816-148">在其他方面，活動和傳輸都與上述案例相似。</span><span class="sxs-lookup"><span data-stu-id="36816-148">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="36816-149">不一定具有錯誤的非同步單向</span><span class="sxs-lookup"><span data-stu-id="36816-149">Asynchronous One-Way with or without Errors</span></span>  
 <span data-ttu-id="36816-150">沒有任何回應或錯誤傳回到用戶端。</span><span class="sxs-lookup"><span data-stu-id="36816-150">No response or fault is returned to the client.</span></span>
