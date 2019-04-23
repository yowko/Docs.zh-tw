---
title: 計算序列中的項目數目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: b39b0a1487c9f250e32b13330f2f70b7e3c7c877
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209524"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>計算序列中的項目數目
使用 <xref:System.Linq.Enumerable.Count%2A> 運算子計算序列中的項目數。  
  
 如果對 Northwind 範例資料庫執行這個查詢，會產生輸出 `91`。  
  
## <a name="example"></a>範例  
 下列範例會計算資料庫中的 `Customers` 數目。  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>範例  
 下列範例計算資料庫中未停產的產品項目。  
  
 如果對 Northwind 範例資料庫執行這個範例，會產生輸出 `69`。  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [彙總查詢](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
