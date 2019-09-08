---
title: 傳回兩個序列之間的集合差異
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 92513ed33e2afb785edbdd462ba7bc14923aa6b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781152"
---
# <a name="return-the-set-difference-between-two-sequences"></a>傳回兩個序列之間的集合差異
使用 <xref:System.Linq.Queryable.Except%2A> 運算子傳回兩個序列之間的集合差異。  
  
## <a name="example"></a>範例  
 這個範例會<xref:System.Linq.Queryable.Except%2A>使用來傳回`Customers` live 但不存在`Employees`的所有國家/地區序列。  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Except%2A> 作業僅妥善定義於集合上。 尚未定義多重集 (Multiset) 的語意 (Semantics)。  
  
## <a name="see-also"></a>另請參閱

- [查詢範例](query-examples.md)
- [標準查詢運算子轉譯](standard-query-operator-translation.md)
