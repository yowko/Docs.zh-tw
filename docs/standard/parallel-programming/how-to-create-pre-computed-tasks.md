---
title: "如何：建立經過預先計算的工作"
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
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 262aa626e9e426da94de0d2ad5f2ef04a5bbc5f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-pre-computed-tasks"></a>如何：建立經過預先計算的工作
此文件將說明如何使用 <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> 方法擷取保留在快取中的非同步下載作業的結果。 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法會傳回已完成的 <xref:System.Threading.Tasks.Task%601> 物件，該物件中會保存提供的值做為其 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性。 當您執行會傳回 <xref:System.Threading.Tasks.Task%601> 物件的非同步作業，而且該 <xref:System.Threading.Tasks.Task%601> 物件的結果已計算時，這個方法很有用。  
  
## <a name="example"></a>範例  
 下列範例將會從網路下載字串。 它會定義 `DownloadStringAsync` 方法。 這個方法會以非同步方式從網路下載字串。 這個範例也會使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 物件快取先前作業的結果。 如果這個快取中保存了輸入位址，`DownloadStringAsync` 就會使用 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法產生保存該位址內容的 <xref:System.Threading.Tasks.Task%601> 物件。 否則，`DownloadStringAsync` 會從網路下載檔案，並將結果加入至快取。  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 這個範例會計算下載多個字串兩次所需的時間。 由於結果已保存在快取中，因此第二組下載作業所需的時間應該會比第一組短。 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法會讓 `DownloadStringAsync` 方法建立保存這些預先計算結果的 <xref:System.Threading.Tasks.Task%601> 物件。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請複製範例程式碼，並將它貼入 Visual Studio 專案中，或是貼入名為 `CachedDownloads.cs` 的檔案中 (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中為 `CachedDownloads.vb`)，然後在 Visual Studio 的 [命令提示字元] 視窗中執行下列命令。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe CachedDownloads.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe CachedDownloads.vb**  
  
## <a name="robust-programming"></a>穩固程式設計  
  
## <a name="see-also"></a>請參閱  
 [以工作為基礎的非同步程式設計](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
