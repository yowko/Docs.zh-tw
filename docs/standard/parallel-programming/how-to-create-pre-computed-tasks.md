---
title: 作法：建立經過預先計算的工作
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e68465b6fae39089600457414e7f2a2328f725b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593132"
---
# <a name="how-to-create-pre-computed-tasks"></a>作法：建立經過預先計算的工作
此文件將說明如何使用 <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> 方法擷取保留在快取中的非同步下載作業的結果。 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法會傳回已完成的 <xref:System.Threading.Tasks.Task%601> 物件，該物件中會保存提供的值做為其 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性。 當您執行會傳回 <xref:System.Threading.Tasks.Task%601> 物件的非同步作業，而且該 <xref:System.Threading.Tasks.Task%601> 物件的結果已計算時，這個方法很有用。  
  
## <a name="example"></a>範例  
 下列範例將會從網路下載字串。 它會定義 `DownloadStringAsync` 方法。 這個方法會以非同步方式從網路下載字串。 這個範例也會使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 物件快取先前作業的結果。 如果這個快取中保存了輸入位址，`DownloadStringAsync` 就會使用 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法產生保存該位址內容的 <xref:System.Threading.Tasks.Task%601> 物件。 否則，`DownloadStringAsync` 會從網路下載檔案，並將結果加入至快取。  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 這個範例會計算下載多個字串兩次所需的時間。 由於結果已保存在快取中，因此第二組下載作業所需的時間應該會比第一組短。 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法會讓 `DownloadStringAsync` 方法建立保存這些預先計算結果的 <xref:System.Threading.Tasks.Task%601> 物件。  
  
## <a name="see-also"></a>另請參閱

- [以工作為基礎的非同步程式設計](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
