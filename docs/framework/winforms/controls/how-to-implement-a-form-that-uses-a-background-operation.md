---
title: "如何：實作使用背景作業的表單 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "背景作業"
  - "背景工作"
  - "背景執行緒"
  - "BackgroundWorker 元件"
  - "元件 [Windows Form], 非同步"
  - "表單, 背景作業"
  - "表單, 多執行緒"
  - "執行緒處理 [Windows Form], 背景作業"
  - "執行緒處理 [Windows Form], 表單"
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：實作使用背景作業的表單
下列範例程式會建立表單，計算 Fibonacci 數字。  該計算在執行緒上執行，與使用者介面執行緒中的不同，因此使用者介面會繼續執行，在繼續計算時不會造成延遲。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  
  
 另請參閱[逐步解說：實作使用背景作業的表單](http://msdn.microsoft.com/library/b2zk6580%20\(v=vs.110\))。  
  
## 範例  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## 穩固程式設計  
  
> [!CAUTION]
>  無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。  請在實作使用多執行緒處理的任何方案之前參閱 [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)。  
  
## 請參閱  
 <xref:System.ComponentModel.BackgroundWorker>   
 <xref:System.ComponentModel.DoWorkEventArgs>   
 [Event\-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)