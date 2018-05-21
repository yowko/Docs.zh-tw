---
title: 如何：使用平行工作周遊二進位樹狀
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6446145d34d22503697bbca59bc2cb2cd2619cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="adabc-102">如何：使用平行工作周遊二進位樹狀</span><span class="sxs-lookup"><span data-stu-id="adabc-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="adabc-103">下列範例示範可以使用平行工作來周遊樹狀資料結構的兩種方式。</span><span class="sxs-lookup"><span data-stu-id="adabc-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="adabc-104">建立樹狀的部分則留待練習。</span><span class="sxs-lookup"><span data-stu-id="adabc-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adabc-105">範例</span><span class="sxs-lookup"><span data-stu-id="adabc-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="adabc-106">這兩個方法的功能相同。</span><span class="sxs-lookup"><span data-stu-id="adabc-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="adabc-107">透過使用 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> 方法來建立並執行工作，您會收到來自工作的控制代碼，用於等待工作及處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="adabc-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adabc-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="adabc-108">See Also</span></span>  
 [<span data-ttu-id="adabc-109">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="adabc-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
