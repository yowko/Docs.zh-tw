---
title: 如何：實作使用背景作業的表單
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd9951929fb030e12c32e8470e5ea433645c4d77
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>如何：實作使用背景作業的表單
下列範例程式會建立表單，計算 Fibonacci 數字。 該計算在執行緒上執行，與使用者介面執行緒中的不同，因此使用者介面會繼續執行，在繼續計算時不會造成延遲。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  
  
 另請參閱[逐步解說：實作使用背景作業的表單](http://msdn.microsoft.com/library/b2zk6580\(v=vs.110\))。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="robust-programming"></a>穩固程式設計  
  
> [!CAUTION]
>  無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。 請在實作使用多執行緒的任何解決方案之前參閱 [Managed 執行緒最佳做法](../../../../docs/standard/threading/managed-threading-best-practices.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [事件架構非同步模式概觀](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Managed 執行緒處理的最佳實施方針](../../../../docs/standard/threading/managed-threading-best-practices.md)
