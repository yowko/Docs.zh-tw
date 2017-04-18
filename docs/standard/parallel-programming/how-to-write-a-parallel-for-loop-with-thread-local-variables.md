---
title: "How to: Write a Parallel.For Loop with Thread-Local Variables | Microsoft Docs"
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
  - "parallel for loops, how to use local state"
ms.assetid: 68384064-7ee7-41e2-90e3-71f00bde01bb
caps.latest.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 23
---
# How to: Write a Parallel.For Loop with Thread-Local Variables
此範例說明如何使用執行緒區域變數，儲存及擷取 <xref:System.Threading.Tasks.Parallel.For%2A> 迴圈所建立之每項工作的狀態。  使用執行緒區域資料，可讓您避免因同步處理大量的共用狀態存取而產生額外負荷。  您可以計算並儲存值，直到工作的所有反覆運算完成為止，而無須在每次反覆運算時寫入至共用資源。  接著，您可以將最終結果寫入至共用資源，或將其傳遞至其他方法。  
  
## 範例  
 下列範例呼叫 <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> 方法，以計算含有一百萬個項目之陣列中的值總和。  每個項目的值等於其索引。  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 每個 <xref:System.Threading.Tasks.Parallel.For%2A> 方法的前兩個參數指定反覆運算的開始和結束值。  在方法的這個多載中，第三個參數是您初始化區域狀態的位置。  在此內容中，區域狀態表示存留期始於目前執行緒上之迴圈的第一次反覆運算之前，終於最後一次反覆運算之後的變數。  
  
 第三個參數的類型是 <xref:System.Func%601>，其中 `TResult` 是將會儲存執行緒區域狀態的變數類型。  其類型是由呼叫泛型 <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> 方法時所提供的泛型類型引數所定義，在此範例中為 <xref:System.Int64>。  此類型引數會指示編譯器將用於儲存執行緒區域狀態的暫存變數類型。  在此範例中，運算式 `() => 0` \(在 Visual Basic 中為 `Function() 0`\) 會將執行緒區域變數初始化為零。  如果泛型類型引數是參考類型或使用者定義的實值類型，則此運算式如下所示：  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 第四個參數會定義迴圈邏輯。  它必須是委派或 Lambda 運算式，其簽章是 `Func<int, ParallelLoopState, long, long>` \(在 C\# 中\) 或 `Func(Of Integer, ParallelLoopState, Long, Long)` \(在 Visual Basic 中\)。  第一個參數是該迴圈反覆運算之迴圈計數器的值。  第二個參數是可用於脫離迴圈的 <xref:System.Threading.Tasks.ParallelLoopState> 物件，<xref:System.Threading.Tasks.Parallel> 類別會提供此物件給每個迴圈。  第三個參數是執行緒區域變數。  最後一個參數是傳回類型。  在此範例中，此類型為 <xref:System.Int64>，因為這是我們在 <xref:System.Threading.Tasks.Parallel.For%2A> 類型引數中指定的類型。  該變數的名稱為 `subtotal`，會由 Lambda 運算式傳回。  此傳回值會在迴圈的每次後續反覆運算時，用來初始化 `subtotal`。  您也可以將此最後一個參數視為會傳遞至每個反覆項目，然後在最後一個反覆項目完成時傳遞至 `localFinally` 委派的值。  
  
 第五個參數定義要在特定執行緒上所有的反覆項目完成後呼叫一次的方法。  輸入參數的類型會重新對應至 <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> 方法的類型引數，以及主體 Lambda 運算式所傳回的類型。  在此範例中，會透過呼叫 <xref:System.Threading.Interlocked.Add%2A?displayProperty=fullName> 方法，以安全執行緒的方式將值加入至類別範圍的變數中。  使用執行緒區域變數，可讓我們避免在每次反覆運算迴圈時寫入至此類別變數。  
  
 如需如何使用 Lambda 運算式的詳細資訊，請參閱 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。  
  
## 請參閱  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)