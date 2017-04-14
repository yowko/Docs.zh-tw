---
title: "Using an AsyncCallback Delegate and State Object | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "asynchronous programming, delegates"
  - "AsyncCallback delegate, samples"
  - "asynchronous programming, state objects"
  - "IAsyncResult interface, samples"
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Using an AsyncCallback Delegate and State Object
當您使用<xref:System.AsyncCallback>是委派給另一個執行緒處理一非同步作業的結果，您可以使用狀態物件在回呼之間傳遞資訊，也可以擷取最後的結果。  這個主題會以延伸的範例示範[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。  
  
## 範例  
 下列程式碼範例會示範使用 <xref:System.Net.Dns> 類別中的非同步方法，以擷取使用者指定之電腦的網域名稱系統 \(DNS\) 資訊。  這個範例會定義並使用 `HostRequest` 類別以儲存狀態資訊。  使用者輸入的每個電腦名稱都會建立 `HostRequest` 物件。  這個物件會傳遞至 <xref:System.Net.Dns.BeginGetHostByName%2A> 方法。  每次有要求完成時，都會呼叫 `ProcessDnsInformation` 方法。  `HostRequest` 物件是使用 <xref:System.IAsyncResult.AsyncState%2A> 屬性來擷取的。  `ProcessDnsInformation` 方法會使用 `HostRequest` 物件來儲存要求所傳回的 <xref:System.Net.IPHostEntry>，或要求所擲回的 <xref:System.Net.Sockets.SocketException>。  當所有的要求都完成之後，應用程式會逐一查看 `HostRequest` 物件，並顯示 DNS 資訊或 <xref:System.Net.Sockets.SocketException> 錯誤訊息。  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## 請參閱  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)