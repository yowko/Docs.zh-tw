---
title: 從識別快取擷取物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: d14b15f72bd196d8b3a61f22c614516e17d2e95b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781236"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>從識別快取擷取物件
本主題描述 LINQ to SQL 查詢的類型，這些查詢可從 <xref:System.Data.Linq.DataContext> 所管理的識別快取傳回物件。  
  
 在 LINQ to SQL 中，<xref:System.Data.Linq.DataContext> 用來管理物件的其中一種方式就是在執行查詢時，將物件識別記錄在識別快取中。 在某些情況下，LINQ to SQL 會先嘗試從識別快取擷取物件，然後再執行資料庫的查詢。  
  
 一般而言，為了讓 LINQ to SQL 查詢從識別快取傳回物件，此查詢必須以物件的主索引鍵為基礎，而且必須傳回單一物件。 特別是，此查詢必須採用下列其中一種一般格式。  
  
> [!NOTE]
> 預先編譯的查詢不會從識別快取傳回物件。 如需預先編譯查詢的詳細資訊，請<xref:System.Data.Linq.CompiledQuery>參閱[和如何：儲存和重複使用](how-to-store-and-reuse-queries.md)查詢。  
  
 若要從識別快取擷取物件，查詢必須採用下列其中一種一般格式：  
  
- <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
- <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 在這些一般格式中，`Function1`、`Function2` 和 `predicate` 的定義方式如下。  
  
 `Function1` 可以是下列任何項目：  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` 可以是下列任何項目：  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` 必須是物件之主索引鍵屬性設定為常數值的運算式。 如果物件具有多個屬性所定義的主索引鍵，每個主索引鍵屬性都必須設定為常數值。 下面是 `predicate` 必須採用的格式範例：  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>範例  
 下列程式碼將提供 LINQ to SQL 查詢類型的範例，這些查詢可從識別快取擷取物件。  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [查詢概念](query-concepts.md)
- [物件身分識別](object-identity.md)
- [背景資訊](background-information.md)
- [物件身分識別](object-identity.md)
