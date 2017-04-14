---
title: "篩選 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 篩選
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 篩選系統可以使用宣告式篩選條件比對訊息，並做出作業決策。您可以使用篩選條件檢查訊息的部分，以判斷如何處理訊息。例如，佇列處理序可以使用 XPath 1.0 查詢檢查已知標頭的優先順序項目，以便決定是否要將訊息移到佇列前頭。  
  
 篩選系統由一組類別所組成，這組類別會有效地判斷哪一組篩選條件是針對特定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 訊息而設定為 `true`。  
  
 篩選系統是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 傳訊的核心元件，依極為快速的執行速度目標而設計。每個篩選條件實作都已針對對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 訊息進行的特定比對種類而最佳化。  
  
 篩選系統不具備執行緒安全。應用程式必須處理任何鎖定語意。不過，它確實支援多種讀取器和單一寫入器。  
  
## 篩選的用途  
 接收到訊息之後，就會執行篩選，篩選是分派訊息至適當應用程式元件的程序一部分。篩選系統的設計能夠滿足數個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 子系統的需求，包括傳訊、路由、安全性、事件處理和系統管理。  
  
## 篩選條件  
 篩選引擎有兩個主要元件：篩選條件和篩選資料表。篩選條件會根據使用者指定的邏輯條件，做出有關訊息的布林值決策。篩選條件會實作 <xref:System.ServiceModel.Dispatcher.MessageFilter> 類別。  
  
 <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> 方法會用於判斷訊息是否符合篩選條件。其中一個方法會測試訊息的標頭，但無法檢查訊息本文。其他方法則會將「*訊息緩衝區*」\(Message Buffer\) 當做輸入參數，而且可以檢查訊息本文。  
  
 篩選條件通常不會個別進行測試，而是以篩選資料表的一部分進行測試，篩選資料表是 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> 方法建立的一般類別。  
  
 每一種篩選條件都會特製化為比對特定種類的布林值條件。一旦建構篩選條件，您就無法變更篩選條件使用的準則。若要修改篩選條件的準則，請建構新的篩選條件並刪除現有的篩選條件。  
  
### 動作篩選條件  
 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> 包含動作字串的清單。如果篩選條件清單中的任何動作符合訊息或訊息緩衝區中的動作標頭，`Match` 方法就會傳回 `true`。如果清單是空白的，則篩選條件會被視為是全部符合的篩選條件，而任何訊息或訊息緩衝區相符，並且 `Match` 會傳回 `true`。如果篩選條件清單中沒有任何動作符合訊息或訊息緩衝區中的動作標頭，`Match` 方法就會傳回 `false`。如果訊息中沒有任何動作，而且篩選條件的清單不是空白，則 `Match` 會傳回 `false`。  
  
### 端點位址篩選條件  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> 會根據端點位址篩選訊息和訊息緩衝區 \(如標頭集合中所示\)。訊息若要通過這類篩選條件，必須符合下列條件：  
  
-   篩選器位址的統一資源識別項 \(URI\) 必須與訊息 To 標頭中的位址 URI 相同。  
  
-   篩選條件 \(`address.Headers` 條件\) 位址中的每個端點參數必須在要對應的訊息中找出標頭。不過，為了使符合項目維持為 `true`，仍接受訊息或訊息緩衝區中的額外標頭。  
  
### 前置詞端點位址篩選條件  
  
1.  <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> 的作用就像 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> 篩選條件，只除了符合項目可以在訊息 URI 的前置詞上之外。例如，指定 http:\/\/www.adatum.com 位址的篩選條件符合 http:\/\/www.adatum.com\/userA 位址的訊息。  
  
### XPath 訊息篩選條件  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 會使用 XPath 運算式來判斷 XML 文件是否包含特定項目、屬性、文字或其他 XML 語法結構。篩選條件經過最佳化，用於 XPath 的精簡子集時能夠發揮極佳的效率。XML 路徑語言在 [W3C XML 路徑語言 1.0 規格](http://go.microsoft.com/fwlink/?LinkId=94779) \(本頁面可能為英文\) 中會有詳盡的說明。  
  
 一般而言，應用程式會在端點使用 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 來查詢 SOAP 訊息的內容，然後根據查詢的結果採取適當的行動。例如，佇列處理序可能會使用 XPath 查詢來檢查已知標頭的優先順序項目，以便決定是否要將訊息移到佇列前頭。  
  
## 篩選資料表  
 篩選資料表是用來儲存索引鍵值組，其中篩選條件是索引鍵，而一些關聯的資料為值。篩選資料可以用來表示當訊息符合篩選條件，並且篩選資料的型別為篩選資料表類別的泛型參數時所要採取的動作。篩選資料可以由路由規則、工作階段安全性狀態、通道上的接聽項等項目而組成。此資料可以用在需要資料流程控制的位置中。  
  
 篩選資料表會實作泛型介面 <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>。  
  
 篩選資料表具有數個方法，這些方法會根據資料表中的所有篩選條件比對訊息，並且傳回符合篩選條件或資料的未排序集合。有些比對方法屬於多重比對，並且會傳回所有符合的項目。其他方法則是單一比對，只傳回一個項目，並且如果有一個以上的篩選條件相符，則會擲回 <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException>。  
  
### 訊息篩選資料表  
 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 是 <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601> 最普遍的實作。您可以在資料表中儲存所有類型的篩選條件。  
  
 您可以指派數值優先順序給篩選條件，其中最大數字表示最高優先順序。多種篩選條件類型可以具有相同的優先順序。特定類型的篩選條件可以顯示在一個以上的優先順序層級中。  
  
 比對會從最高優先順序開始進行，一旦以指定的優先順序找到符合的篩選條件，就不會檢查較低優先順序的篩選條件。因此，如果您正在使用單一篩選條件比對方法，並且有一個以上的篩選條件符合訊息，但每個符合的篩選條件具有不同的優先順序，那麼就不會擲回任何例外狀況，而是會傳回具有最高優先順序的篩選條件。同樣地，多重篩選條件比對方法只會傳回具有最高優先順序的符合篩選條件。  
  
### XPath 訊息篩選資料表  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> 已針對宣告式 XPath 篩選條件最佳化，因此資料表索引鍵為 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>。  
  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> 類別會最佳化適用於大部分傳訊案例的 XPath 子集的比對，並且支援完整的 XPath 1.0 文法。它具有最佳化的演算法，能夠有效地進行平行比對。  
  
 這個資料表有數個經過特製化的 `Match` 方法，這些方法可以在 <xref:System.Xml.XPath.XPathNavigator> 和 <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> 上操作。<xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> 透過新增 <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> 屬性來擴充 <xref:System.Xml.XPath.XPathNavigator> 類別。這個屬性允許儲存 XML 文件中的位置並迅速將其載入，而不需要複製 \(Clone\) 導覽；此類作業對 <xref:System.Xml.XPath.XPathNavigator> 而言，是非常耗費資源的記憶體配置。為了讓 <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> 針對訊息處理提供重要的最佳化效果，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] XPath 引擎必須經常記錄游標在 XML 文件查詢執行過程中的位置。  
  
## 客戶案例  
 您可以視訊息中包含的資料而定，隨時使用篩選將訊息傳送到不同的處理模組。根據訊息的動作程式碼路由訊息，以及根據訊息的端點位址分離訊息資料流的信號，即為兩個典型的案例。  
  
### 路由  
 端點的接聽項會接聽訊息 SOAP 標頭中有一或多個動作程式碼的訊息。透過將包含動作程式碼的陣列傳遞至其建構函式以建立 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter>，即可實作此動作。它會使用該篩選條件註冊 `ListenerFactory`，因此，只有動作符合篩選條件的其中一個動作的訊息，才會到達該特定端點。  
  
### 分離信號  
 當多個端點從網路外的相同 `ServiceListener` 上散開時，要分離訊息信號並確認這些端點是否屬於特定端點位址的唯一方法就是使用 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>，它會查詢儲存在標頭中的資訊，藉此選取送往已註冊之端點的訊息。在這些篩選條件中，只有通過的訊息具有對應至下列兩者的所有必要標頭：  
  
-   `EndpointAddress` 中的 URI。  
  
-   如 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> 所指定，`EndpointAddress` 中的其餘端點參數。  
  
## 請參閱  
 [資料傳輸與序列化](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)