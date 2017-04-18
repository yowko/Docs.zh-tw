---
title: "如何：在 ConcurrentDictionary 中加入和移除項目 | Microsoft Docs"
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
  - "安全執行緒集合，並行字典"
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：在 ConcurrentDictionary 中加入和移除項目
這個範例將示範如何在 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> 中加入、擷取、更新和移除項目。  這個集合類別是安全執行緒實作。  每當多個執行緒可能會嘗試以並行方式存取項目時，我們建議您使用此集合類別。  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 提供了許多簡便方法，可讓程式碼不需要先檢查機碼是否存在，然後再嘗試加入或移除資料。  下表列出這些簡便方法並描述它們的使用時機。  
  
|方法|使用時機...|  
|--------|-------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|您想要針對指定的機碼加入新的值，而且如果機碼已經存在，您想要取代其值。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|您想要針對指定的機碼擷取現有的值，而且如果機碼不存在，您想要指定機碼值組。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|您想要加入、取得、擷取或移除機碼值組，而且如果機碼已經存在或嘗試由於任何其他原因而失敗，您想要採取某個替代動作。|  
  
## 範例  
 下列範例會使用兩個 <xref:System.Threading.Tasks.Task> 執行個體，以並行方式將某些項目加入至 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>，然後輸出所有內容，以便顯示是否成功加入這些項目。  此範例也會示範如何使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>方法、<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>方法、<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 方法，在集合中加入、更新、擷取項目。  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 是針對多執行緒案例所設計的。  您不需要在程式碼中使用鎖定，即可在集合中加入或移除項目。  不過，下列情況永遠可能會發生：某個執行緒擷取值，而另一個執行緒提供新的值給相同的機碼，藉以立即更新集合。  
  
 另外，雖然 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 的所有方法都具備執行緒安全，但並非所有方法都不可部分完成，特別是 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>。  傳遞至這些方法的使用者委派會在字典之內部鎖定的外部叫用。這樣做能防止未知的程式碼封鎖所有執行緒。因此可能發生下列事件序列：  
  
 1\) threadA 呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>，發現沒有任何項目，並且建立要藉由叫用 valueFactory 委派加入的新項目。  
  
 2\) threadB 同時呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>，其 valueFactory 委派會被叫用並且在 threadA 之前抵達內部鎖定，因此它的新機碼值組會加入字典中。  
  
 3\) threadA 的使用者委派完成，且該執行緒抵達鎖定，但是現在發現該項目已存在  
  
 4\) threadA 執行 "Get"，並且傳回之前由 threadB 加入的資料。  
  
 因此並不保證 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 傳回的資料就是執行緒的 valueFactory 所建立的資料。  呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> 時，也可能發生類似的事件序列。  
  
## 請參閱  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [安全執行緒集合](../../../../docs/standard/collections/thread-safe/index.md)