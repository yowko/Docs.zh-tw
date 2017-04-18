---
title: "moduloObjectHashcode MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "managed debugging assistants (MDAs), hashcode modulus"
  - "Modulo object hash code"
  - "moduloObjectHashcode MDA"
  - "hashcode modulus"
  - "MDAs (managed debugging assistants), hashcode modulus"
  - "GetHashCode method"
  - "modulus of hashcodes"
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# moduloObjectHashcode MDA
`moduloObjectHashcode` Managed 偵錯助理 \(MDA\) 會變更 <xref:System.Object> 類別的行為，以在 <xref:System.Object.GetHashCode%2A> 方法傳回的雜湊程式碼上執行模數運算。  這個 MDA 的預設模數是 1，這樣會讓 <xref:System.Object.GetHashCode%2A> 針對所有物件傳回 0。  
  
## 症狀  
 在移到新版本的 Common Language Runtime \(CLR\) 之後，程式不再正確執行：  
  
-   程式從 <xref:System.Collections.Hashtable> 取得錯誤的物件。  
  
-   來自 <xref:System.Collections.Hashtable> 的列舉型別順序有一項會中斷程式的變更。  
  
-   之前相同的兩個物件目前不再相同。  
  
-   之前不相同的兩個物件目前是相同的。  
  
## 原因  
 您的程式可能從 <xref:System.Collections.Hashtable> 取得錯誤的物件，因為 <xref:System.Collections.Hashtable> 的索引鍵之類別上的 <xref:System.Object.Equals%2A> 方法實作會藉由比較 <xref:System.Object.GetHashCode%2A> 方法的呼叫結果來測試物件是否相同。  雜湊程式碼不應該用來測試物件是否相同，因為即使兩個物件各自的欄位有不同的值，還是可能會有相同的雜湊程式碼。  雖然這樣的雜湊程式碼衝突很罕見，但還是會發生。  這樣對於 <xref:System.Collections.Hashtable> 查詢的影響是兩個不相同的索引鍵看起來似乎相同，而且會從 <xref:System.Collections.Hashtable> 傳回錯誤的物件。  基於效能理由，<xref:System.Object.GetHashCode%2A> 實作可能會在不同的執行階段版本之間而有所不同，所以在某一個版本上可能不會發生的衝突情形，卻可能會發生在後續的版本上。  啟用這個 MDA 來測試，當雜湊程式碼發生衝突時，您的程式碼是否有錯誤。  當啟用這個 MDA 時，它會讓 <xref:System.Object.GetHashCode%2A> 方法傳回 0，造成所有雜湊程式碼發生衝突。  啟用這個 MDA 對於程式的唯一影響，應該是會讓程式的執行速度變慢。  
  
 如果用來計算索引鍵的雜湊程式碼之演算法有變更，則來自 <xref:System.Collections.Hashtable> 的列舉型別順序可能會因為不同的執行階段版本而不同。  若要測試程式是否採用了雜湊資料表中的索引鍵或值的列舉型別順序之相依性，您可啟用這個 MDA。  
  
## 解決方式  
 絕對不要使用雜湊程式碼來替代物件識別；  實作 <xref:System.Object.Equals%2A?displayProperty=fullName> 方法的覆寫，可以不用比較雜湊程式碼。  
  
 不要建立雜湊資料表中的索引鍵或值的列舉型別順序之相依性。  
  
## 對執行階段的影響  
 當啟用這個 MDA 時，應用程式執行的速度會比較慢。  這個 MDA 只會接受原本已經傳回的雜湊程式碼，而不是傳回除以模數時的餘數。  
  
## Output  
 沒有這個 MDA 的輸出。  
  
## 組態  
 `modulus` 屬性可指定用於雜湊程式碼上的模數，  預設值為 1。  
  
```  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)