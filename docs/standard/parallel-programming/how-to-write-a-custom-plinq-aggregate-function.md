---
title: "如何：撰寫自訂 PLINQ 彙總函式"
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
helpviewer_keywords: PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b098f21e29d0d59cd99ddbb64af6246d9953a3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>如何：撰寫自訂 PLINQ 彙總函式
這個範例示範如何使用<xref:System.Linq.ParallelEnumerable.Aggregate%2A>方法，以自訂彙總函式套用至來源序列。  
  
> [!WARNING]
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。 提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 下列範例會計算標準差順序的整數。  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 這個範例會使用特有 PLINQ 彙總的標準查詢運算子的多載。 這個多載會採用額外<xref:System.Func%603?displayProperty=nameWithType>做為第三個輸入參數。 在執行彙總結果的最終計算之前，這個委派會結合所有執行緒的結果。 在此範例中我們加入一起加總所有執行緒。  
  
 請注意，當包含的單一運算式的傳回值的 lambda 運算式主體<xref:System.Func%602?displayProperty=nameWithType>委派是運算式的值。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq.ParallelEnumerable>  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
