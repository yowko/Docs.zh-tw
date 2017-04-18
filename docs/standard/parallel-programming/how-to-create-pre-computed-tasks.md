---
title: "How to: Create Pre-Computed Tasks | Microsoft Docs"
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
  - "tasks, creating pre-computed"
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# How to: Create Pre-Computed Tasks
此文件描述如何使用 <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=fullName> 方法擷取保留在快取中之非同步下載作業的結果。  <xref:System.Threading.Tasks.Task.FromResult%2A> 方法會傳回已完成的 <xref:System.Threading.Tasks.Task%601> 物件提供的值做為其 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性。  當您執行會傳回 <xref:System.Threading.Tasks.Task%601> 物件的非同步作業，而且該 <xref:System.Threading.Tasks.Task%601> 物件的結果已計算時，這個方法很有用。  
  
## 範例  
 下列範例下載從網路的字串。  它會定義 `DownloadStringAsync` 方法。  這個方法下載從網路資料流的非同步。  這個範例也會使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 物件快取先前的作業的結果。  如果輸入位址。這個快取存放 `DownloadStringAsync` ，使用 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法產生 <xref:System.Threading.Tasks.Task%601> 物件內容在該位址。  否則， `DownloadStringAsync` 下載從網路的檔案並將結果加入至快取。  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 這個範例會計算下載多個字串兩次的時間。  因為結果保留在快取中，保留第二組下載作業的第一個集合應該相當長的時間。  <xref:System.Threading.Tasks.Task.FromResult%2A> 方法會使 `DownloadStringAsync` 方法建立保留這些預先計算結果的 <xref:System.Threading.Tasks.Task%601> 物件。  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為  `CachedDownloads.cs`的檔案中 \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 的 `CachedDownloads.vb` \) ，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe CachedDownloads.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe CachedDownloads.vb**  
  
## 穩固程式設計  
  
## 請參閱  
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)