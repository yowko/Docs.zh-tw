---
title: "How to: Call Windows APIs (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "API calls"
  - "Windows API, calling"
  - "API calls, platform invoke"
  - "calls, stored procedures"
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Call Windows APIs (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

這個範例在 user32.dll 中定義並且呼叫 `MessageBox` 函式，接著將字串傳遞給該函式。  
  
## 範例  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   對 <xref:System> 命名空間的參考。  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   這個方法不是靜態的 \(Static\)，而是抽象方法，或先前已定義的方法。  父型別是介面，或者 *name* 或 *dllName* 的長度為零   \(<xref:System.ArgumentException>\)  
  
-   *name* 或 *dllName* 為 `Nothing` \(<xref:System.ArgumentNullException>\)  
  
-   先前已使用 `CreateType` 建立包含型別 \(Containing Type\)   \(<xref:System.InvalidOperationException>\)  
  
## 請參閱  
 [A Closer Look at Platform Invoke](http://msdn.microsoft.com/zh-tw/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)   
 [平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)   
 [使用 Unmanaged DLL 函式](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md)   
 [Defining a Method with Reflection Emit](http://msdn.microsoft.com/zh-tw/84fd3bf6-628f-41aa-83d9-b990cf926e81)   
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)