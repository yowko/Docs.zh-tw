---
title: "路由案例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "路由 [WCF], 案例"
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# 路由案例
若路由服務的自訂性相當高，在從頭建立新組態時設計足夠的路由邏輯可能會相當困難。  不過，大多數路由服務組態會遵循數種常見案例。  雖然這些案例可能無法直接套用於特定的組態，但若了解如何設定路由服務處理這些案例，就能協助您了解路由服務。  
  
## 常見案例  
 路由服務最基本的用法是彙總多個目的地端點，以減少對用戶端應用程式公開的端點數目，然後使用訊息篩選條件，將每個訊息路由至正確的目的地。  訊息可以根據邏輯或實體處理需求進行路由 \(例如必須由特定服務處理的訊息類型\)，也可以根據任何商務需求進行路由 \(例如優先處理來自特定來源的訊息\)。  下表列出一些常見的案例，以及發生這些案例的時機。  
  
|情節|使用時機|  
|--------|----------|  
|服務版本控制|您需要支援服務的多種版本，或者未來可能會需要部署更新服務|  
|服務資料分割|您必須跨多個主機分割服務|  
|動態更新|您必須在執行階段動態重新設定路由邏輯，以處理多變的服務部署|  
|多點傳送|您必須將一則訊息傳送至多個端點|  
|通訊協定橋接|您透過傳輸通訊協定接收訊息，而目的地端點使用不同的通訊協定|  
|錯誤處理|您需要提供恢復網路中斷與通訊失敗的能力|  
  
> [!NOTE]
>  以上許多案例適用於特定商務需求或處理條件，但規劃支援動態更新及利用錯誤處理往往會是最佳做法，因為這麼做可以讓您在執行階段修改路由邏輯，並且從暫時性的網路及通訊錯誤復原。  
  
### 服務版本控制  
 導入新版本的服務時，您往往必須維護舊版本，直到用戶端轉換至新服務為止。  如果服務是需要數天、數星期、甚或數個月才能完成的長期執行處理序，這一點更是重要。  此時往往需要為新服務實作新的端點位址，同時又要保留原本用於舊版的端點。  
  
 透過使用路由服務，您可以公開一個端點以接收來自用戶端應用程式的訊息，然後再根據訊息的內容，將每個訊息路由到正確的服務版本。  最基本的實作包括在訊息中加入自訂標頭，指出用於處理訊息的服務版本。  路由服務可以利用 XPathMessageFilter 檢查訊息中是否具有自訂標頭，並且將訊息路由至適當的目的地端點。  
  
 如需用於建立服務版本控制組態的步驟，請參閱 [HOW TO：服務版本控制](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)。  如需使用 XPathMessageFilter 根據自訂標頭路由訊息的範例，請參閱[進階篩選](../../../../docs/framework/wcf/samples/advanced-filters.md)範例。  
  
### 服務資料分割  
 設計分散式環境時，通常最好能夠跨多個電腦散播處理負載，以便提供高可用性、減少個別電腦的處理負載，或是針對特定的訊息子集提供專用資源。  雖然路由服務無法取代專用負載平衡解決方案，但它具備根據內容執行路由的功能，因此可用於將類似的訊息路由至特定的目的地。  例如，您可能必須將來自特定用戶端的訊息與來自其他用戶端的訊息分開處理。  
  
 如需用於建立服務資料分割組態的步驟，請參閱 [HOW TO：服務資料切割](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)。  如需使用篩選條件根據 URL 及自訂標頭分割資料的範例，請參閱[進階篩選](../../../../docs/framework/wcf/samples/advanced-filters.md)範例。  
  
### 動態路由  
 通常最好可以根據多變的商務需求修改路由組態，例如將路由加入至較新版的服務、變更路由準則，或者是變更篩選條件路由特定訊息的目的地端點。  路由服務可透過 <xref:System.ServiceModel.Routing.RoutingExtension>，讓您在執行階段提供新的 RoutingConfiguration，以達到這個目的。  新的組態會立即生效，但只會影響路由服務所處理的所有新工作階段。  
  
 如需用於實作動態路由的步驟，請參閱 [HOW TO：動態更新](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)。  如需使用動態路由的範例，請參閱[動態重新組態](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md)範例。  
  
### 多點傳送  
 路由訊息時，您通常會將每個訊息路由至一個特定的目的地端點。  不過，您偶爾可能需要將訊息複本路由至多個目的地端點。  若要執行多點傳送路由，必須滿足下列條件：  
  
-   通道類型不得為要求\-回覆 \(但可以是單向或雙向\)，因為查詢\-回覆會命令回應要求的用戶端應用程式只接收一個回覆。  
  
-   評估訊息時，必須有多個篩選條件傳回 **true**。  
  
 如果符合這些條件，每個與傳回 true 的篩選條件相關的端點都會收到一份訊息複本。  
  
### 通訊協定橋接  
 在不同的 SOAP 通訊協定之間路由訊息時，路由服務會利用 WCF API 來轉換在通訊協定之間傳遞的訊息。  當路由服務所公開的服務端點使用與用戶端端點 \(訊息傳送的位置\) 不同的通訊協定時，此情形便會自動發生。  如果使用中的通訊協定不是標準通訊協定，就可以停用這個行為。不過，停用此行為後，您必須自行提供橋接程式碼。  
  
 .  如需使用路由服務轉譯通訊協定之間的訊息的範例，請參閱[橋接及錯誤處理](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md)範例。  
  
### 錯誤處理  
 在分散式環境中，經常會發生暫時性的網路或通訊錯誤。  若未使用路由服務之類的媒介服務，就必須由用戶端應用程式負責處理此類錯誤。  如果用戶端應用程式不包含在網路或通訊失敗時重試的特定邏輯，也不具替代位置的知識，使用者可能會發生必須重新送出訊息多次，目的地服務才能順利處理該訊息的情形。  這種情形會讓客戶認為應用程式不可靠，進而感到不滿意。  
  
 路由服務會嘗試針對發生網路或通訊相關失敗的訊息提供強大的錯誤處理功能，以嘗試補救這種情形。  透過建立可能的目的地端點清單，並且將這份清單與每個訊息篩選條件產生關聯，您就可以排除因為只有一個可能的目的地所導致的單點錯誤。  一旦出現錯誤，路由服務會嘗試將訊息傳遞至清單中的下一個端點，直到順利傳遞訊息、發生非通訊錯誤，或者所有端點皆已用盡為止。  
  
 如需用於設定錯誤處理的步驟，請參閱 [HOW TO：錯誤處理](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)。  如需實作錯誤處理的範例，請參閱[橋接及錯誤處理](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md)與[進階的錯誤處理](../../../../docs/framework/wcf/samples/advanced-error-handling.md)範例。  
  
### 本章節內容  
 [HOW TO：服務版本控制](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [HOW TO：服務資料切割](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [HOW TO：動態更新](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [HOW TO：錯誤處理](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## 請參閱  
 [路由簡介](../../../../docs/framework/wcf/feature-details/routing-introduction.md)