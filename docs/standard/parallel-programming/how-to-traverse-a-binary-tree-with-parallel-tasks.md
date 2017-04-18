---
title: "How to: Traverse a Binary Tree with Parallel Tasks | Microsoft Docs"
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
  - "tasks, how to traverse a tree"
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Traverse a Binary Tree with Parallel Tasks
下列範例說明兩種可使用平行工作周遊樹狀資料結構的方法。  建立樹狀結構的動作則留著當做練習。  
  
## 範例  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 所顯示的兩種方法在功能上是相等的。  使用 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> 方法建立及執行工作，可讓您從工作取得可用以等候工作及處理例外狀況的控制代碼。  
  
## 請參閱  
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)