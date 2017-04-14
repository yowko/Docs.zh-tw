---
title: "如何：使用平行類別逐一查看檔案目錄 | Microsoft Docs"
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
  - "平行迴圈，如何逐一查看目錄"
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用平行類別逐一查看檔案目錄
在許多情況下，檔案反覆運算是可輕易平行處理的作業。  [How to: Iterate File Directories with PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)主題說明在許多案例下執行此工作最簡單的方式。  不過，當您的程式碼必須處理存取檔案系統時可能發生的許多例外狀況類型時，可能會增加複雜度。  下列範例示範處理問題的一個作法。  它使用以堆疊為基礎的反覆項目，周遊指定之目錄下的所有檔案和資料夾，可讓您的程式碼攔截及處理各種例外狀況。  當然，處理例外狀況的方式是由您決定。  
  
## 範例  
 下列範例會以循序方式逐一查看目錄，但會以平行方式處理檔案。  當檔案與目錄的比例很高時，這可能是最佳作法。  另外，也可以平行處理目錄反覆運算，而循序存取每個檔案。  除非是特別以具有大量處理器的電腦為目標，否則平行處理兩個迴圈可能沒有效率。  但無論如何，您都應該徹底測試應用程式，判斷最佳作法。  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 在此範例中，檔案 I\/O 是以同步方式執行。  處理大型檔案或慢速網路連線時，最好是以非同步方式存取檔案。  您可以將非同步 I\/O 技巧與平行反覆運算結合。  如需詳細資訊，請參閱[TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)。  
  
 這個範例會使用本機 `fileCount` 變數維護處理的檔案總管計數。  由於變數可能會由多個工作同時存取，對它的存取是透過呼叫 <xref:System.Threading.Interlocked.Add%2A?displayProperty=fullName> 的方法同步。  
  
 請注意，如果在主執行緒上擲回例外狀況，由 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 方法所啟動的執行緒可能會繼續執行。  若要停止這些執行緒，您可以在例外狀況處理常式中設定布林值變數，在每次平行迴圈反覆運算時檢查其值。  如果值表示已擲回例外狀況，請使用 <xref:System.Threading.Tasks.ParallelLoopState> 變數停止或中斷迴圈。  如需詳細資訊，請參閱[How to: Stop or Break from a Parallel.For Loop](http://msdn.microsoft.com/zh-tw/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)。  
  
## 請參閱  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)