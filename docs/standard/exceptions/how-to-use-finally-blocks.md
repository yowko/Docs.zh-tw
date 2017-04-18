---
title: "如何：使用 Finally 區塊 | Microsoft Docs"
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
  - "ArgumentOutOfRangeException 類別"
  - "例外狀況, finally 區塊"
  - "例外狀況, try/catch 區塊"
  - "finally 區塊"
  - "try/catch 區塊"
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用 Finally 區塊
當例外狀況發生時，執行會停止，而控制權會交給最接近的例外處理常式。  這通常意謂著，有幾行您期待一定會被呼叫的程式碼沒有執行。  某些資源清除 \(例如關閉檔案\) 必須一定要執行，即使擲回例外狀況。  若要達成這點，您可以使用 Finally 區塊。  不論是否擲回例外狀況，都一定會執行 Finally 區塊。  
  
 下列程式碼範例使用 Try\/Catch 區塊來攔截 <xref:System.ArgumentOutOfRangeException>。  `Main` 方法建立兩個陣列，並嘗試複製其中一個給另一個。  這動作產生 **ArgumentOutOfRangeException**，而錯誤則寫到主控台。  Finally 區塊都會執行，不論複製動作的結果為何。  
  
## 範例  
 [!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
 [!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
 [!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  
  
## 請參閱  
 [如何：使用 Try\/Catch 區塊攔截例外狀況](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [如何：明確擲回例外狀況](../../../docs/standard/exceptions/how-to-explicitly-throw-exceptions.md)   
 [如何：建立使用者定義的例外狀況](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)   
 [例外狀況處理基礎觀念](../../../docs/standard/exceptions/exception-handling-fundamentals.md)