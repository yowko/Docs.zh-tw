---
title: "How to: Implement a Client of the Event-based Asynchronous Pattern | Microsoft Docs"
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
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "Asynchronous Pattern"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "components [.NET Framework], asynchronous"
  - "AsyncOperation class"
  - "threading [Windows Forms], asynchronous features"
  - "AsyncCompletedEventArgs class"
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Implement a Client of the Event-based Asynchronous Pattern
下列程式碼範例會示範如何使用遵守[Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)的元件。  此範例的表單使用 [How to: Implement a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)中所描述的  `PrimeNumberCalculator`  元件。  
  
 當您執行使用此範例的專案時，將會看到「質數計算機」\(Prime Number Calculator\) 表單，此表單具有一個方格和兩個按鈕：\[**啟動新工作**\] 和 \[**取消**\]。  您可以連續按 \[**啟動新工作**\] 按鈕許多次，每按一下時，都會有非同步作業 \(Asynchronous Operation\) 開始計算，以判斷隨機產生的測試數值是否為質數。  表單將會定期顯示進度和累加結果。  每項作業都會被指派唯一的工作 ID，  而且計算的結果會顯示在 \[**結果**\] 欄中；如果測試數值不是質數，就會具有 \[**合數**\] 的標籤，而且會顯示其所擁有的第一個除數。  
  
 使用 \[**取消**\] 按鈕即可取消任何擱置中的作業。  另外也能進行多重選取。  
  
> [!NOTE]
>  多數的數目都不會是質數。  如果在幾次作業完成之後沒有找到質數，請再啟動更多工作，最後一定會找到一些質數。  
  
## 範例  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## 請參閱  
 <xref:System.ComponentModel.AsyncOperation>   
 <xref:System.ComponentModel.AsyncOperationManager>   
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>