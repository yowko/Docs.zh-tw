---
title: "How to: Prevent a Child Task from Attaching to its Parent | Microsoft Docs"
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
  - "tasks, preventing attachments"
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# How to: Prevent a Child Task from Attaching to its Parent
本文件示範如何防止將子工作附加至父工作。  會導致子工作無法附加到它的父代是有用的，當您呼叫由協力廠商撰寫，而且使用的元件。  例如，使用 <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName> 選項建立 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件的協力廠商元件可能造成問題的程式碼，如果它是長時間執行的或擲回未處理的例外狀況。  
  
## 範例  
 下列範例使用會導致子工作效果比較使用預設選項效果附加與父代。  這個範例會將協力廠商程式庫也會使用 <xref:System.Threading.Tasks.Task> 物件的 <xref:System.Threading.Tasks.Task> 物件。  協力廠商程式庫使用 <xref:System.Threading.Tasks.TaskCreationOptions> 選項建立 <xref:System.Threading.Tasks.Task> 物件。  應用程式使用 <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName> 選項建立父工作。  這個選項會指示執行階段移除子工作的 <xref:System.Threading.Tasks.TaskCreationOptions> 規格。  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 因為父工作會在所有子工作完成後才完成，因此長時間執行的子工作可能造成整個應用程式效能不佳。  在此範例中，當應用程式使用預設選項來建立父工作時，子工作必須先完成，父工作完成。  當應用程式使用 <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName> 選項時，子系未附加至父代。  因此，應用程式可以在父工作完成後執行其他工作，它必須等候子工作完成。  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為  `DenyChildAttach.cs`的檔案中 \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 的 `DenyChildAttach.vb` \) ，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe DenyChildAttach.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe DenyChildAttach.vb**  
  
## 穩固程式設計  
  
## 請參閱  
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)