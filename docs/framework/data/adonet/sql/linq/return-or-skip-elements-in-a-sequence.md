---
title: 傳回或略過序列中的項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 885e6bc011041320a3dc7b17d84b2541bf030adf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168307"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>傳回或略過序列中的項目
使用 <xref:System.Linq.Queryable.Take%2A> 運算子傳回序列中指定數目的項目，然後略過其餘的項目。  
  
 使用 <xref:System.Linq.Queryable.Skip%2A> 運算子略過序列中指定數目的項目，然後傳回其餘的項目。  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 在用於對 SQL Server 2000 進行的查詢中時會有一些限制。 如需詳細資訊，請參閱中的"Skip 和 Take 例外狀況在 SQL Server 2000"項目[疑難排解](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 將轉譯<xref:System.Linq.Queryable.Skip%2A>藉由使用子查詢與 SQL`NOT EXISTS`子句。 這項轉譯具有下列限制：  
  
-   引數必須為集合。 即使多重集 (Multiset) 已排序，仍不支援多重集。  
  
-   產生的查詢可能會比已套用 <xref:System.Linq.Queryable.Skip%2A> 之基底查詢所產生的查詢更為複雜。 這種複雜性會導致效能降低甚或逾時。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Take` 來選取前五名雇用的 `Employees`。 請注意，此集合會先按照 `HireDate` 排序。  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>範例  
 下列範例會使用 <xref:System.Linq.Queryable.Skip%2A> 來選取除了 10 項最貴 `Products` 以外的所有產品。  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>範例  
 下列範例會結合 <xref:System.Linq.Queryable.Skip%2A> 和 <xref:System.Linq.Queryable.Take%2A> 方法略過前 50 筆記錄，然後傳回接下來的 10 筆記錄。  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A> 和 <xref:System.Linq.Queryable.Skip%2A> 作業僅針對已排序的集合加以妥善定義。 並未定義未排序集合或多重集 (Multiset) 的語意 (Semantics)。  
  
 由於在 SQL 中排序的限制，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會嘗試將 <xref:System.Linq.Queryable.Take%2A> 或 <xref:System.Linq.Queryable.Skip%2A> 運算子的引數排序移至運算子的結果。  
  
> [!NOTE]
>  [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] 和 [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)] 的轉譯有所不同。 如果您打算使用 <xref:System.Linq.Queryable.Skip%2A> 搭配任何複雜度的查詢，請使用 [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)]。  
  
 請考量下列 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] 查詢：  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將排序移至 SQL 程式碼的結尾，如下所示：  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 當 <xref:System.Linq.Queryable.Take%2A> 和 <xref:System.Linq.Queryable.Skip%2A> 鏈結在一起時，所有指定的排序都必須一致。 否則，會有未定義的結果。  
  
 至於以 SQL 規格為基礎的非負數、常數整數引數，<xref:System.Linq.Queryable.Take%2A> 和 <xref:System.Linq.Queryable.Skip%2A> 都已定義妥善。  
  
## <a name="see-also"></a>另請參閱

- [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
