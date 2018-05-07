---
title: 從序列排除重複項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 3dbb5be65823b456e5b573f7cbbad8d172022425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>從序列排除重複項目
使用 <xref:System.Linq.Queryable.Distinct%2A> 運算子去除序列中重複的項目。  
  
## <a name="example"></a>範例  
 下列範例使用 <xref:System.Linq.Queryable.Distinct%2A> 來選取一連串具有客戶的唯一城市。  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>另請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
