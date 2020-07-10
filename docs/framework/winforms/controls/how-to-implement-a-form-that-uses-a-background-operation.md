---
title: 如何：實作使用背景作業的表單
description: 瞭解如何執行使用背景作業的 Windows Form，讓一個作業可以繼續執行，而另一個作業繼續進行。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: 23bf4bc02fbf998d92dfce6d84e4e337cbefe7d9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174519"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>如何：實作使用背景作業的表單
下列範例程式會建立表單，計算 Fibonacci 數字。 該計算在執行緒上執行，與使用者介面執行緒中的不同，因此使用者介面會繼續執行，在繼續計算時不會造成延遲。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  
  
 另請參閱[逐步解說：實作使用背景作業的表單](walkthrough-implementing-a-form-that-uses-a-background-operation.md)。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
## <a name="robust-programming"></a>穩固程式設計  
  
> [!CAUTION]
> 無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。 請在實作使用多執行緒的任何解決方案之前參閱 [Managed 執行緒最佳做法](../../../standard/threading/managed-threading-best-practices.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [事件架構非同步模式概觀](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [受控執行緒最佳做法](../../../standard/threading/managed-threading-best-practices.md)
