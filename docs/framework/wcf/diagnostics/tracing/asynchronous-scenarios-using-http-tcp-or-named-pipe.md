---
title: "使用 HTTP、TCP 或具名管道的非同步案例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 使用 HTTP、TCP 或具名管道的非同步案例
本主題會說明各種非同步要求\/回覆案例的活動和傳輸，以及使用 HTTP、TCP 或具名管道的執行緒要求。  
  
## 無錯誤的非同步要求\/回覆  
 本章節會說明非同步要求\/回覆案例的活動和傳輸，以及多執行緒的用戶端。  
  
 當 `beginCall` 傳回，而且 `endCall` 傳回時，呼叫端活動便會終止。如果有呼叫回呼，該回呼就會傳回。  
  
 當 `beginCall` 傳回，而且 `endCall` 傳回，或是當回呼 \(若有從活動呼叫\) 傳回時，呼叫的活動便會終止。  
  
### 沒有回呼的非同步用戶端  
  
#### 兩端皆啟用傳播，使用 HTTP  
 ![非同步情節](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")  
  
 圖 1。非同步用戶端，沒有回呼，兩端的 `propagateActivity`\=`true`，HTTP 架構  
  
 如果 `propagateActivity`\=`true`，ProcessMessage 會指示要傳輸哪一個 ProcessAction 活動。  
  
 若是 HTTP 架構案例，ReceiveBytes 會叫用於第一個要傳送的訊息上，並隨該要求的存留期而保留。  
  
#### 任何一端的傳播已停用，使用 HTTP  
 如果任何一端的 `propagateActivity`\=`false`，ProcessMessage 不會指示要傳輸哪一個 ProcessAction 活動。因此，這時會叫用含有新識別碼的新暫存 ProcessAction 活動。當非同步回應符合 ServiceModel 程式碼中的要求時，該活動識別碼即可從本機內容進行擷取。實際的 ProcessAction 活動可以透過該識別碼加以傳輸。  
  
 ![使用 HTTP&#47;TCP&#47;具名管道的非同步情節](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")  
  
 圖 2。非同步用戶端，沒有回呼，任一端的 `propagateActivity`\=`false`，HTTP 架構  
  
 若是 HTTP 架構案例，ReceiveBytes 會叫用於第一個要傳送的訊息上，並隨該要求的存留期而保留。  
  
 當呼叫端或被呼叫端的 `propagateActivity`\=`false`，而且回應訊息不包含動作標頭時，非同步用戶端上就會建立「處理動作」活動。  
  
#### 兩端皆啟用傳播，使用 TCP 或具名管道  
 ![使用 HTTP&#47;TCP&#47;具名管道的非同步情節](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")  
  
 圖 3。非同步用戶端，沒有回呼，兩端的 `propagateActivity`\=`true`，具名管道\/TCP 架構  
  
 若是具名管道或 TCP 架構案例，ReceiveBytes 會叫用於用戶端開啟時，並隨該連線的存留期而保留。  
  
 類似於圖 1，如果 `propagateActivity`\=`true`，ProcessMessage 會指示要傳輸哪一個 ProcessAction 活動。  
  
#### 任何一端的傳播已停用，使用 TCP 或具名管道  
 若是具名管道或 TCP 架構案例，ReceiveBytes 會叫用於用戶端開啟時，並隨該連線的存留期而保留。  
  
 類似於圖 2，如果任何一端的 `propagateActivity`\=`false`，ProcessMessage 不會指示要傳輸哪一個 ProcessAction 活動。因此，這時會叫用含有新識別碼的新暫存 ProcessAction 活動。當非同步回應符合 ServiceModel 程式碼中的要求時，該活動識別碼即可從本機內容進行擷取。實際的 ProcessAction 活動可以透過該識別碼加以傳輸。  
  
 ![使用 HTTP&#47;TCP&#47;具名管道的非同步情節](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")  
  
 圖 4。非同步用戶端，沒有回呼，任一端的 `propagateActivity`\=`false`，具名管道\/TCP 架構  
  
### 有回呼的非同步用戶端  
 這個案例會為回呼和 `endCall` 新增活動 G 和 A’，及其傳入\/傳出。  
  
 本章節只有示範搭配 `propragateActivity`\=`true` 來使用 HTTP。不過，另外增加的活動和傳輸也適用於其他情況 \(也就是 `propagateActivity`\=`false`，使用 TCP 或具名管道\)。  
  
 當用戶端呼叫使用者程式碼以通知結果已準備好時，該回呼就會建立新活動 \(G\)。然後，使用者程式碼便會從回呼內部 \(如圖 5 所示\) 或回呼外部 \(圖 6\) 呼叫 `endCall`。由於不知道是從哪個使用者活動呼叫 `endCall`，因此這個活動會標記為 `A’`。A’ 有可能相同或不同於 A。  
  
 ![非同步情節](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")  
  
 圖 5。具有回呼的非同步用戶端，從回呼呼叫 `endCall`  
  
 ![非同步情節](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")  
  
 圖 6。具有回呼的非同步用戶端，從回呼外部呼叫 `endCall`  
  
### 有回呼的非同步伺服器  
 ![使用 HTTP&#47;TCP&#47;具名管道的非同步情節](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")  
  
 圖 7。有回呼的非同步伺服器  
  
 通道堆疊會在訊息接收時回呼用戶端：這個處理的追蹤會由 ProcessRequest 活動本身發出。  
  
## 含有錯誤的非同步要求\/回覆  
 `endCall` 期間會收到錯誤 \(Fault\) 訊息錯誤 \(Error\)。在其他方面，活動和傳輸都與上述案例相似。  
  
## 不一定具有錯誤的非同步單向  
 沒有任何回應或錯誤傳回到用戶端。