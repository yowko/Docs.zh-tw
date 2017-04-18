---
title: "使用 HTTP、TCP 或具名管道的同步案例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 使用 HTTP、TCP 或具名管道的同步案例
本主題將說明不同的同步要求\/回覆案例中的各種活動與傳輸，以及使用 HTTP、TCP 或具名管道的單一執行緒用戶端。如需更多關於多執行緒要求的詳細資訊，請參閱[使用 HTTP、TCP 或具名管道的非同步案例](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md)。  
  
## 沒有錯誤的同步要求\/回覆  
 本節將說明有效的同步要求\/回覆案例的各種活動和傳輸 \(搭配單一執行緒用戶端\)。  
  
### 用戶端  
  
#### 建立服務端點的通訊  
 用戶端已建構並開啟。針對每一個步驟，環境活動 \(A\) 會分別傳送到「建構用戶端」\(B\) 和「開放式用戶端」\(C\) 活動。針對每一個傳送出去的活動，在傳回一個活動之前環境活動會暫停 \(亦即，直到執行 ServiceModel 程式碼為止\)。  
  
#### 向服務端點提出要求  
 環境活動會傳送到 ”ProcessAction” \(D\) 活動。在此活動中，會傳送要求訊息，同時收到回應訊息。當控制項傳回使用者程式碼時，活動會結束。由於這是一項同步要求，環境活動會在控制項傳回之前暫停。  
  
#### 關閉服務端點的通訊  
 用戶端的關閉活動 \(I\) 會從環境活動中建立。這與全新及開放項目相同。  
  
### 伺服器  
  
#### 設定服務主機  
 ServiceHost 的全新與開放活動 \(N 和 O\) 會從環境活動 \(M\) 中建立。  
  
 接聽項活動 \(P\) 是在開啟每個接聽項的 ServiceHost 時建立。接聽項活動會開始等候接收並處理資料。  
  
#### 接收網路上的資料  
 當資料抵達網路時，會建立 “ReceiveBytes” 活動 \(如果尚不存在的話\) \(Q\) 以處理接收的資料。此活動可以重複使用在同一個連線或佇列中的多個訊息上。  
  
 如果 ReceiveBytes 活動擁有足夠的資料來構成 SOAP 動作訊息的話，就會啟動 ProcessMessage 活動 \(R\)。  
  
 在活動 R 中，訊息標頭會經過處理，並確認 activityID 標頭。如果此標頭已存在，則活動識別碼會設定為 ProcessAction 活動，否則，會建立新的識別碼。  
  
 在處理呼叫時，會建立 ProcessAction 活動 \(S\) 並將之傳送出去。一旦完成所有與傳入訊息相關的處理之後，此活動就會結束，包括執行使用者程式碼 \(T\) 並傳送回應訊息 \(如果適用的話\)。  
  
#### 關閉服務主機  
 ServiceHost 的關閉活動 \(Z\) 會從環境活動中建立。  
  
 ![使用 HTTP&#47;TCP&#47;具名管道的同步情節](../../../../../docs/framework/wcf/diagnostics/tracing/media/sync.gif "Sync")  
  
 在 \<A: name\> 中，`A` 是捷徑符號，用來說明先前內容與表 3 中的活動。`Name` 是活動的名稱縮寫。  
  
 如果是 `propagateActivity`\=`true`，則用戶端與服務上的處理動作將同時具備相同的活動識別碼。  
  
## 具有錯誤的同步要求\/回覆  
 與先前案例的唯一不同點在於，SOAP 錯誤訊息將做為回應訊息傳回。如果是 `propagateActivity`\=`true`，則會將要求訊息的活動識別碼新增到 SOAP 錯誤訊息。  
  
## 不具有錯誤的同步單向  
 與第一個案例的唯一不同點在於，沒有任何訊息會傳回伺服器。如果是以 HTTP 為基礎的通訊協定，則仍舊會將狀態 \(有效或錯誤\) 傳回用戶端。這是因為 HTTP 是唯一使用要求\-回應語意 \(屬於 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 通訊協定堆疊的一部分\) 的通訊協定。由於 TCP 處理已隱藏起來不讓 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 看見，因此不會將任何認可傳送到用戶端。  
  
## 具有錯誤的同步單向  
 如果在處理訊息 \(Q 或更多\) 時發生錯誤，就不會將任何通知傳回用戶端。這個案例與「不具有錯誤的同步單向」案例相同。如果您想要收到錯誤訊息，就不應該使用單向案例。  
  
## 雙工  
 與先前案例的不同之處在於，用戶端會表現出服務行為並建立 ReceiveBytes 和 ProcessMessage 活動，這與非同步案例類似。