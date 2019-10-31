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
ms.openlocfilehash: b79337e6ee8057506ff87c696cecd6b038eeebfc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141638"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>如何：使用平行工作周遊二進位樹狀
下列範例示範可以使用平行工作來周遊樹狀資料結構的兩種方式。 建立樹狀的部分則留待練習。  
  
## <a name="example"></a>範例  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 這兩個方法的功能相同。 透過使用 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> 方法來建立並執行工作，您會收到來自工作的控制代碼，用於等待工作及處理例外狀況。  
  
## <a name="see-also"></a>請參閱

- [工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
