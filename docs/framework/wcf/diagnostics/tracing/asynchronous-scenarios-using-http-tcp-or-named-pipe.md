---
title: 使用 HTTP、TCP 或具名管道的非同步案例
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 00213c8d117f4319d7e29312dd0b9805d916231a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244141"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>使用 HTTP、TCP 或具名管道的非同步案例

本主題會說明各種非同步要求/回覆案例的活動和傳輸，以及使用 HTTP、TCP 或具名管道的執行緒要求。  
  
## <a name="asynchronous-requestreply-without-errors"></a>無錯誤的非同步要求/回覆  

 本章節會說明非同步要求/回覆案例的活動和傳輸，以及多執行緒的用戶端。  
  
 當 `beginCall` 傳回，而且 `endCall` 傳回時，呼叫端活動便會終止。 如果有呼叫回呼，該回呼就會傳回。  
  
 當 `beginCall` 傳回，而且 `endCall` 傳回，或是當回呼 (若有從活動呼叫) 傳回時，呼叫的活動便會終止。  
  
### <a name="asynchronous-client-without-callback"></a>沒有回呼的非同步用戶端  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>兩端皆啟用傳播，使用 HTTP  

 ![沒有回呼的非同步用戶端，其中 propagateActivity 在兩端都設為 true。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 如果 `propagateActivity=true` 為，則表示 ProcessMessage 會指出要傳送至哪個 ProcessAction 活動。  
  
 若是 HTTP 架構案例，ReceiveBytes 會叫用於第一個要傳送的訊息上，並隨該要求的存留期而保留。  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>任何一端的傳播已停用，使用 HTTP  

 如果 `propagateActivity=false` 任一側，ProcessMessage 就不會指出要傳送至哪個 ProcessAction 活動。 因此，這時會叫用含有新識別碼的新暫存 ProcessAction 活動。 當非同步回應符合 ServiceModel 程式碼中的要求時，該活動識別碼即可從本機內容進行擷取。 實際的 ProcessAction 活動可以透過該識別碼加以傳輸。  
  
 ![沒有回呼的非同步用戶端，其中任何一端的 propagateActivity 都設定為 false。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 若是 HTTP 架構案例，ReceiveBytes 會叫用於第一個要傳送的訊息上，並隨該要求的存留期而保留。  
  
 當 `propagateActivity=false` 呼叫端或被呼叫端時，以及當回應訊息不包含動作標頭時，會在非同步用戶端上建立處理動作活動。  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>兩端皆啟用傳播，使用 TCP 或具名管道  

 ![沒有回呼的非同步用戶端，其中 propagateActivity 會在兩端和具名管道/TCP 上設定為 true。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 若是具名管道或 TCP 架構案例，ReceiveBytes 會叫用於用戶端開啟時，並隨該連線的存留期而保留。  
  
 類似于第一個影像，如果 `propagateActivity=true` ，ProcessMessage 會指出要傳送至哪個 ProcessAction 活動。  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>任何一端的傳播已停用，使用 TCP 或具名管道  

 若是具名管道或 TCP 架構案例，ReceiveBytes 會叫用於用戶端開啟時，並隨該連線的存留期而保留。  
  
 類似于第二個映射，如果 `propagateActivity=false` 任一側，ProcessMessage 就不會指出要傳送至哪個 ProcessAction 活動。 因此，這時會叫用含有新識別碼的新暫存 ProcessAction 活動。 當非同步回應符合 ServiceModel 程式碼中的要求時，該活動識別碼即可從本機內容進行擷取。 實際的 ProcessAction 活動可以透過該識別碼加以傳輸。  
  
 ![沒有回呼的非同步用戶端，其中 propagateActivity 會在側邊和具名管道/TCP 上設定為 false。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a>有回呼的非同步用戶端  

 這個案例會為回呼和 `endCall` 新增活動 G 和 A’，及其傳入/傳出。  
  
 本節僅示範如何搭配使用 HTTP 和 `propagateActivity` = `true` 。 不過，其他的活動和傳輸也適用于其他情況 (也就是 `propagateActivity` = `false` 使用 TCP 或具名管道) 。  
  
 當用戶端呼叫使用者程式碼以通知結果已準備好時，該回呼就會建立新活動 (G)。 然後，使用者程式碼便會從回呼內部 (如圖 5 所示) 或回呼外部 (圖 6) 呼叫 `endCall`。 因為它不知道要呼叫哪一個使用者活動 `endCall` ，所以此活動會標示為 `A’` 。 A’ 有可能相同或不同於 A。  
  
 ![顯示具有回呼的非同步用戶端，endcall 在回呼中。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![顯示具有回呼、endcall 外部回呼的非同步用戶端。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a>有回呼的非同步伺服器  

 ![顯示具有回呼的非同步伺服器。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 通道堆疊會在訊息接收時回呼用戶端：這個處理的追蹤會由 ProcessRequest 活動本身發出。  
  
## <a name="asynchronous-requestreply-with-errors"></a>含有錯誤的非同步要求/回覆  

 `endCall` 期間會收到錯誤 (Fault) 訊息錯誤 (Error)。 在其他方面，活動和傳輸都與上述案例相似。  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>不一定具有錯誤的非同步單向  

 沒有任何回應或錯誤傳回到用戶端。
