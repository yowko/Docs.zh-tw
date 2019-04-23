---
title: 制定聯結和交叉乘積查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: b0037f56947a86627ee9ea84369527aec859a0f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180501"
---
# <a name="formulate-joins-and-cross-product-queries"></a>制定聯結和交叉乘積查詢
下列範例顯示如何合併多張資料表中的結果。  
  
## <a name="example"></a>範例  
 下列範例會使用中的外部索引鍵巡覽`From`在 Visual Basic 中的子句 (`from`子句C#) 來選取在倫敦的客戶的所有訂單。  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>範例  
 下列範例會使用中的外部索引鍵巡覽`Where`在 Visual Basic 中的子句 (`where`子句中的C#) 來篩選出缺貨`Products`其`Supplier`是在美國境內。  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>範例  
 下列範例會使用中的外部索引鍵巡覽`From`在 Visual Basic 中的子句 (`from`子句C#) 來篩選位於西雅圖的員工，並列出他們的領域。  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>範例  
 下列範例會使用中的外部索引鍵巡覽`Select`在 Visual Basic 中的子句 (`select`子句C#) 來篩選員工配對，到另一位員工報告的位置，以及兩位員工的來自相同的位置`City`。  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>範例  
 下列 Visual Basic 範例會尋找所有客戶和訂單、 可確保訂單會比對，為客戶和保證，該清單中每位客戶，提供連絡人的名稱。  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>範例  
 下列範例明確聯結 (Join) 兩張資料表，並規劃來自這兩張資料表的結果。  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>範例  
 下列範例明確聯結三張資料表，並規劃來自每張資料表的結果。  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用 `LEFT OUTER JOIN` 來達成 `DefaultIfEmpty()`。 如果 `DefaultIfEmpty()` 沒有 `Order`，則 `Employee` 方法會傳回 null。  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>範例  
 下列範例會規劃透過聯結產生的 `let` 運算式。  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>範例  
 下列範例顯示具有複合索引鍵的 `join`。  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>範例  
 下列範例顯示如何建構 `join`，其中另一端可以為 null，而另一端則不可以。  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>另請參閱

- [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
