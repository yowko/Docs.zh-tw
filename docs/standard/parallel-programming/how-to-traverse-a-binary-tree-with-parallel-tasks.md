---
title: "如何：使用平行工作周遊二進位樹狀"
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
helpviewer_keywords: tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c029a763faaa0b4d6ea5612efe079e47415b6fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>如何：使用平行工作周遊二進位樹狀
下列範例會示範兩種方式中可以使用平行工作周遊樹狀資料結構。 建立樹狀結構本身則留待練習。  
  
## <a name="example"></a>範例  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 所顯示的兩個方法的功能相同。 使用<xref:System.Threading.Tasks.TaskFactory.StartNew%2A>方法來建立並執行工作，您會回到控制代碼可用來等候工作，以及處理例外狀況的工作。  
  
## <a name="see-also"></a>另請參閱  
 [工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
