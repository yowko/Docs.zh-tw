---
title: "How to: Iterate File Directories with PLINQ | Microsoft Docs"
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
  - "PLINQ queries, how to iterate directories"
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Iterate File Directories with PLINQ
這個範例示範在檔案目錄上平行處理作業的兩個簡單方式。  第一個查詢使用 <xref:System.IO.Directory.GetFiles%2A> 方法，在目錄和所有子目錄中填入檔案名稱的陣列。  這個方法等到填入整個陣列之後才會傳回，因此會在作業開頭時引入延遲。  不過，在填入陣列之後，PLINQ 就會平行、非常快速地處理它。  
  
 第二個查詢使用靜態 <xref:System.IO.Directory.EnumerateDirectories%2A> 和 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> 方法，立即開始傳回結果。  這個作法在逐一查看大型目錄樹狀結構時比較快，儘管處理時間相較於第一個範例可能會根據許多因素而不同。  
  
> [!WARNING]
>  這些範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。  如需加速的詳細資訊，請參閱[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## 範例  
 下列範例示範當您能存取樹狀結構中的所有目錄、檔案大小不是太大、存取時間也不是太多的簡單情況下，如何逐一查看檔案目錄。  這個作法在一開始建構檔案名稱的陣列時有一段延遲。  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## 範例  
 下列範例示範當您能存取樹狀結構中的所有目錄、檔案大小不是太大、存取時間也不是太多的簡單情況下，如何逐一查看檔案目錄。  這個作法比前一個作法更快開始產生結果。  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 使用 <xref:System.IO.Directory.GetFiles%2A> 時，確認您擁有樹狀結構中所有目錄足夠的使用權限。  否則會擲回例外狀況，也不會傳回結果。  在 PLINQ 查詢中使用 <xref:System.IO.Directory.EnumerateDirectories%2A> 時，以非失誤性、能繼續逐一查看的方式處理 I\/O 例外狀況時會有問題。  如果您的程式碼必須處理 I\/O 或未授權的存取例外狀況，應該考慮 [如何：使用平行類別逐一查看檔案目錄](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md)中說明的作法。  
  
 如果 I\/O 延遲是問題，例如在網路上處理檔案 I\/O 時，請考慮使用 [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)和此[部落格文章](http://go.microsoft.com/fwlink/?LinkID=186458) \(英文\) 中說明的其中一個非同步 I\/O 技巧。  
  
## 請參閱  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)