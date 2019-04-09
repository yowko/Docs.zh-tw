---
title: HOW TO：在 DataContext 層級篩選
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: 343cffa9b1c034068e5abcc652e936f89ee6a992
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084579"
---
# <a name="how-to-filter-at-the-datacontext-level"></a>HOW TO：在 DataContext 層級篩選
您可以在 `EntitySets` 層級篩選 `DataContext`。 這類篩選會套用至所有使用該 <xref:System.Data.Linq.DataContext> 執行個體的查詢。  
  
## <a name="example"></a>範例  
 在下列範例中，會使用 <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> 以根據 `ShippedDate` 來篩選客戶的預先載入訂單。  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a>另請參閱

- [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
