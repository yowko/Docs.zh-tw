---
title: "如何：控制 PLINQ 查詢中的順序"
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
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3aef90c1a1160905662f93a83d6536f6d804b179
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>如何：控制 PLINQ 查詢中的順序
這些範例示範如何使用 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 擴充方法來控制 PLINQ 查詢中的順序。  
  
> [!WARNING]
>  這些範例主要是為了示範用法，執行速度可能比對應的循序 LINQ to Objects 查詢快或慢。  
  
## <a name="example"></a>範例  
 下列範例會保留來源序列中的順序。 這有時是必要的；比方說，有些查詢運算子需要已排序的來源序列才能產生正確結果。  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>範例  
 下列範例示範來源序列可能會排序的部分查詢運算子。 這些運算子將處理未排序的順序，但它們可能會產生非預期的結果。  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 若要執行此方法，請將它貼到 [PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案中的 PLINQDataSample 類別，然後按 F5 鍵。  
  
## <a name="example"></a>範例  
 下列範例示範如何保留查詢第一個部分的順序，然後移除順序以增加 join 子句的效能，再重新套用順序至最終結果順序。  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 若要執行此方法，請將它貼到 [PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)專案中的 PLINQDataSample 類別，然後按 F5 鍵。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Linq.ParallelEnumerable>  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
