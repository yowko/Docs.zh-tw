---
title: 如何：複製目錄
description: 瞭解如何使用 i/o 類別來複製目錄，以同步方式將目錄的內容複寫到另一個位置。
ms.date: 12/27/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET], copying directories
- subdirectory copying
- copying directories
- directories [.NET], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: dfe45d8529eb927a6b174a7bb411afa8072035f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679061"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="1bc8a-103">如何：複製目錄</span><span class="sxs-lookup"><span data-stu-id="1bc8a-103">How to: Copy directories</span></span>

<span data-ttu-id="1bc8a-104">本文示範如何使用 i/o 類別，以同步方式將目錄的內容複寫到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="1bc8a-104">This article demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="1bc8a-105">如需非同步檔案複製的範例，請參閱[非同步檔案 I/O](asynchronous-file-i-o.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc8a-105">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="1bc8a-106">此範例會將 `DirectoryCopy` 方法的 `copySubDirs` 設定為 `true` 來複製子目錄。</span><span class="sxs-lookup"><span data-stu-id="1bc8a-106">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="1bc8a-107">`DirectoryCopy` 方法會以遞迴方式複製子目錄，方法是在每個子目錄上呼叫其本身，直到沒有其他要複製的子目錄為止。</span><span class="sxs-lookup"><span data-stu-id="1bc8a-107">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bc8a-108">範例</span><span class="sxs-lookup"><span data-stu-id="1bc8a-108">Example</span></span>  

 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="1bc8a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bc8a-109">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="1bc8a-110">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="1bc8a-110">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="1bc8a-111">一般 I/O 工作</span><span class="sxs-lookup"><span data-stu-id="1bc8a-111">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="1bc8a-112">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="1bc8a-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
