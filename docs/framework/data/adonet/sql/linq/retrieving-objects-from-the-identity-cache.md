---
title: 從識別快取擷取物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: dceda9dce794e0a08cc9cd7905cf3cd0685898d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569150"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>從識別快取擷取物件
本主題描述 LINQ to SQL 查詢的類型，這些查詢可從 <xref:System.Data.Linq.DataContext> 所管理的識別快取傳回物件。  
  
 在 LINQ to SQL 中，<xref:System.Data.Linq.DataContext> 用來管理物件的其中一種方式就是在執行查詢時，將物件識別記錄在識別快取中。 在某些情況下，LINQ to SQL 會先嘗試從識別快取擷取物件，然後再執行資料庫的查詢。  
  
 一般而言，為了讓 LINQ to SQL 查詢從識別快取傳回物件，此查詢必須以物件的主索引鍵為基礎，而且必須傳回單一物件。 特別是，此查詢必須採用下列其中一種一般格式。  
  
> [!NOTE]
>  預先編譯的查詢不會從識別快取傳回物件。 如需有關預先編譯的查詢的詳細資訊，請參閱<xref:System.Data.Linq.CompiledQuery>和[How to:儲存並重複使用查詢](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)。  
  
 若要從識別快取擷取物件，查詢必須採用下列其中一種一般格式：  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 在這些一般格式中，`Function1`、`Function2` 和 `predicate` 的定義方式如下。  
  
 `Function1` 可以是下列任何項目：  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` 可以是下列任何項目：  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` 必須是物件之主索引鍵屬性設定為常數值的運算式。 如果物件具有多個屬性所定義的主索引鍵，每個主索引鍵屬性都必須設定為常數值。 下面是 `predicate` 必須採用的格式範例：  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>範例  
 下列程式碼將提供 LINQ to SQL 查詢類型的範例，這些查詢可從識別快取擷取物件。  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [物件身分識別](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [物件身分識別](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
