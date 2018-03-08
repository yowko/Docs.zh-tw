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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f8069072f5d917d4ef169a1aed8854ae3139016d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>如何：實作事件架構非同步模式的用戶端
下列程式碼範例示範如何使用遵守[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)的元件。 此範例的表單使用 `PrimeNumberCalculator` 元件，請參閱[如何：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)所述。  
  
 當您執行使用此範例的專案時，就會看到含有資料格的「質數計算機」表單和兩個按鈕：[開始新工作] 和 [取消]。 您可以連續按一下 [開始新工作] 按鈕數次，然後每按一下，非同步作業都會開始計算以決定隨機產生的測試數字是否為質數。 表單會定期顯示進度和累加結果。 每個作業都會指派一個工作識別碼。 計算結果會顯示在 [結果] 欄，如果測試號碼不是質數，就會標示為 [複合]，並顯示其第一個除數。  
  
 任何暫止的作業可以使用 [取消] 按鈕來取消。 您可以選取多個項目。  
  
> [!NOTE]
>  大部分數字都不會是質數。 如果數次完成作業後都找不到質數，只要啟動更多工作，最終一定會找到一些質數。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
