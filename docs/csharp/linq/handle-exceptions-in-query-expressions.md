---
title: "處理查詢運算式中的例外狀況"
description: "如何處理查詢運算式中的例外狀況。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 376bd461bfeb51653471fd374a2215aa15872976
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="handle-exceptions-in-query-expressions"></a>處理查詢運算式中的例外狀況

您可在查詢運算式的內容中呼叫任何方法。 不過，我們建議您避免在查詢運算式中呼叫任何方法，因為它會產生副作用，例如修改資料來源的內容或擲回例外狀況。 本例顯示如何避免在查詢運算式中呼叫方法時引發例外狀況，卻不違反處理例外狀況的一般 .NET Framework 方針。 這些方針指出，當您了解為何在指定內容中擲回時，可以接受攔截特定的例外狀況。 如需詳細資訊，請參閱[例外狀況的最佳做法](../../standard/exceptions/best-practices-for-exceptions.md)。  
  
 最後一個範例顯示如何處理這種當您在查詢執行期間必須擲回例外狀況的情況。  
  
## <a name="example"></a>範例  

 下例示範如何將例外狀況處理程式碼移到查詢運算式之外。 只有當方法不依賴任何查詢區域變數時才可以。  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a>範例 

 在某些情況下，對從查詢中擲回的例外狀況的最佳回應，可能是立即停止執行查詢。 下例示範如何處理可能從查詢主體內擲回的例外狀況。 假設 `SomeMethodThatMightThrow` 可能造成需要停止執行查詢的例外狀況。  
  
 請注意，`try` 區塊會括住 `foreach` 迴圈，不是括住查詢本身。 這是因為 `foreach` 迴圈是查詢實際執行的點。 如需詳細資訊，請參閱 [LINQ 查詢簡介](../programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a>另請參閱  
 [LINQ 查詢運算式](index.md)
