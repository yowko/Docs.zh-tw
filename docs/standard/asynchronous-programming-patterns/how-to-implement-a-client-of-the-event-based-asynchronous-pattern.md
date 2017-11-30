---
title: "如何：實作事件架構非同步模式的用戶端"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b70d4ba205d39ad8fcbc7c7f6fa1f5b34a36c98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>如何：實作事件架構非同步模式的用戶端
下列程式碼範例示範如何使用的元件，就會遵守[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)。 這個範例表單使用`PrimeNumberCalculator`中所述的元件[How to： 實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)。  
  
 當您執行使用此範例中的專案時，您會看到 「 質數計算機 」 表單方格與兩個按鈕：**啟動新工作**和**取消**。 您可以按一下**啟動新工作**按鈕多次連續，且每按一下，非同步作業會開始計算，來決定隨機產生的測試數目是否為質數。 進度和累加結果，會定期顯示表單。 每個操作已指派一個唯一的工作 id。 計算的結果會顯示在**結果**資料行; 如果測試數不是主要的它會標示為**複合**並顯示其第一個除數。  
  
 任何暫止的作業可以取消與**取消** 按鈕。 您可以進行多重選取。  
  
> [!NOTE]
>  大部分的數字不會是質數。 如果您已經找不到質數數個作業完成之後，只需啟動更多的工作，最後您會發現某些質數。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
