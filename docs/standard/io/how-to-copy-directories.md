---
title: 如何：複製目錄
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1cfe07af216da1c35b093a1ca23e4d48c60a7bfe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571231"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="1b024-102">如何：複製目錄</span><span class="sxs-lookup"><span data-stu-id="1b024-102">How to: Copy Directories</span></span>
<span data-ttu-id="1b024-103">本範例將示範如何使用 I/O 類別將某一個目錄的內容同步複製到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="1b024-103">This example demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> <span data-ttu-id="1b024-104">在此範例中，使用者可以指定是否要同時複製子目錄。</span><span class="sxs-lookup"><span data-stu-id="1b024-104">In this example, the user can specify whether to also copy the subdirectories.</span></span> <span data-ttu-id="1b024-105">如果子目錄已複製，這個範例中的方法就會以遞迴方式複製子目錄，方法是在每個後續的子目錄上呼叫其本身，直到沒有其他要複製的子目錄為止。</span><span class="sxs-lookup"><span data-stu-id="1b024-105">If the subdirectories are copied, the method in this example recursively copies them by calling itself on each subsequent subdirectory until there are no more to copy.</span></span>  
  
 <span data-ttu-id="1b024-106">如需以非同步方式複製檔案的範例，請參閱 [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md)。</span><span class="sxs-lookup"><span data-stu-id="1b024-106">For an example of copying files asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b024-107">範例</span><span class="sxs-lookup"><span data-stu-id="1b024-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1b024-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b024-108">See Also</span></span>  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [<span data-ttu-id="1b024-109">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="1b024-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="1b024-110">一般 I/O 工作</span><span class="sxs-lookup"><span data-stu-id="1b024-110">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
 [<span data-ttu-id="1b024-111">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="1b024-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
