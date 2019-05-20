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
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="441d5-102">作法：建立經過預先計算的工作</span><span class="sxs-lookup"><span data-stu-id="441d5-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="441d5-103">此文件將說明如何使用 <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> 方法擷取保留在快取中的非同步下載作業的結果。</span><span class="sxs-lookup"><span data-stu-id="441d5-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="441d5-104"><xref:System.Threading.Tasks.Task.FromResult%2A> 方法會傳回已完成的 <xref:System.Threading.Tasks.Task%601> 物件，該物件中會保存提供的值做為其 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="441d5-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="441d5-105">當您執行會傳回 <xref:System.Threading.Tasks.Task%601> 物件的非同步作業，而且該 <xref:System.Threading.Tasks.Task%601> 物件的結果已計算時，這個方法很有用。</span><span class="sxs-lookup"><span data-stu-id="441d5-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="441d5-106">範例</span><span class="sxs-lookup"><span data-stu-id="441d5-106">Example</span></span>  
 <span data-ttu-id="441d5-107">下列範例將會從網路下載字串。</span><span class="sxs-lookup"><span data-stu-id="441d5-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="441d5-108">它會定義 `DownloadStringAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="441d5-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="441d5-109">這個方法會以非同步方式從網路下載字串。</span><span class="sxs-lookup"><span data-stu-id="441d5-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="441d5-110">這個範例也會使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 物件快取先前作業的結果。</span><span class="sxs-lookup"><span data-stu-id="441d5-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="441d5-111">如果這個快取中保存了輸入位址，`DownloadStringAsync` 就會使用 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法產生保存該位址內容的 <xref:System.Threading.Tasks.Task%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="441d5-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="441d5-112">否則，`DownloadStringAsync` 會從網路下載檔案，並將結果加入至快取。</span><span class="sxs-lookup"><span data-stu-id="441d5-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="441d5-113">這個範例會計算下載多個字串兩次所需的時間。</span><span class="sxs-lookup"><span data-stu-id="441d5-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="441d5-114">由於結果已保存在快取中，因此第二組下載作業所需的時間應該會比第一組短。</span><span class="sxs-lookup"><span data-stu-id="441d5-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="441d5-115"><xref:System.Threading.Tasks.Task.FromResult%2A> 方法會讓 `DownloadStringAsync` 方法建立保存這些預先計算結果的 <xref:System.Threading.Tasks.Task%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="441d5-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441d5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="441d5-116">See also</span></span>

- [<span data-ttu-id="441d5-117">以工作為基礎的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="441d5-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
