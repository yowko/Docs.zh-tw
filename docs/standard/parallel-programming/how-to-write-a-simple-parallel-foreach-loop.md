---
title: "How to: Write a Simple Parallel.ForEach Loop | Microsoft Docs"
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
  - "foreach, parallel version"
  - "parallel programming, foreach"
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# How to: Write a Simple Parallel.ForEach Loop
本範例顯示如何使用 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 迴圈，對任何 <xref:System.Collections.IEnumerable?displayProperty=fullName> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 資料來源啟用平行處理原則。  
  
> [!NOTE]
>  本文件使用 Lambda 運算式來定義 PLINQ 中的委派。  如果您不太熟悉 C\# 或 Visual Basic 中的 Lambda 運算式，請參閱 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。  
  
## 範例  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈的運作類似 <xref:System.Threading.Tasks.Parallel.For%2A> 迴圈。  來源集合會進行分割，然後根據系統環境將工作排定在多個執行緒上執行。  系統上的處理器愈多，平行方法執行就愈快。  對於某些來源集合，視來源大小和所執行的工作類型而定，循序迴圈可能會比較快。  如需效能的詳細資訊，請參閱[Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)。  
  
 如需平行迴圈的詳細資訊，請參閱 [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)。  
  
 若要搭配非泛型集合使用 <xref:System.Threading.Tasks.Parallel.ForEach%2A>，您可以使用 <xref:System.Linq.Enumerable.Cast%2A> 擴充方法將集合轉換為泛型集合，如下列範例所示：  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 您也可以使用平行 LINQ \(PLINQ\) 來平行處理 <xref:System.Collections.Generic.IEnumerable%601> 資料來源。  PLINQ 可讓您使用宣告式查詢語法來表達迴圈行為。  如需詳細資訊，請參閱[Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。  
  
## 編譯程式碼  
  
-   將這段程式碼複製並貼至 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010 主控台應用程式專案中。  
  
-   將參考加入至 System.Drawing.dll  
  
-   按 F5  
  
## 請參閱  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)