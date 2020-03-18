---
title: Join操作 （C#）
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76868001"
---
# <a name="join-operations-c"></a>聯結作業 (C#)

兩個資料來源的「聯結」**，就是某個資料來源中的物件，和另一個資料來源中共用通用屬性的物件的關聯。  
  
 對於不能直接追蹤目標資料來源彼此之間的關聯性的查詢而言，聯結是很重要的作業。 在物件導向的程式設計中，這可能表示物件之間的相互關聯沒有模組化，例如單向關聯性的返回方向。 一個單向關聯性的範例是「客戶」類別，其具有類型「城市」的屬性，但「城市」類別沒有「客戶」物件集合的屬性。 若您有「城市」物件清單，且您想要尋找每個城市中的所有客戶，您就可以使用聯結作業來尋找客戶。  
  
 LINQ 架構中所提供的 join 方法是 <xref:System.Linq.Enumerable.Join%2A> 和 <xref:System.Linq.Enumerable.GroupJoin%2A>。 這些方法會執行等聯結，或是執行根據其索引鍵相等與否配對兩個資料來源的聯結。 （為了進行比較，Transact-SQL 支援"等於"以外的聯結運算子，例如"小於"運算子。在關係資料庫術語中，<xref:System.Linq.Enumerable.Join%2A>實現內部聯接，即僅返回在其他資料集中具有匹配的物件的聯接類型。 <xref:System.Linq.Enumerable.GroupJoin%2A> 方法從關聯式資料庫觀點來看沒有直接的對應項目，但它會實作內部聯結和左方外部聯結的超集。 左方外部聯結是傳回第一個 (左) 資料來源中每個項目的聯結，即使它在其他資料來源中沒有相互關聯的項目也一樣。  
  
 以下概念圖示範兩個集合，以及兩個集合中包含在內部聯結或左外部聯結中的項目。  
  
 ![顯示內部&#47;外部的兩個重疊圓形。](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|C# 查詢運算式語法|相關資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|根據索引鍵選取器函式聯結兩個序列並擷取值組。|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|根據索引鍵選取器函式聯結兩個序列，並為每個項目的相符結果進行分組。|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法示例
  
### Join  
  
下面的示例使用 子`join … in … on … equals …`句根據特定值聯接兩個序列：
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

下面的示例使用 子`join … in … on … equals … into …`句根據特定值聯接兩個序列，並為每個元素的結果匹配進行分組：
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)
- [匿名型別](../../classes-and-structs/anonymous-types.md)
- [制定聯結和交叉乘積查詢](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [聯接子句](../../../language-reference/keywords/join-clause.md)
- [Join通過使用複合鍵](../../../linq/join-by-using-composite-keys.md)
- [如何從不同檔 （LINQ） （C#） 加入內容](./how-to-join-content-from-dissimilar-files-linq.md)
- [排序 join 子句的結果](../../../linq/order-the-results-of-a-join-clause.md)
- [執行自訂聯接操作](../../../linq/perform-custom-join-operations.md)
- [執行群組聯結](../../../linq/perform-grouped-joins.md)
- [執行內部聯結](../../../linq/perform-inner-joins.md)
- [執行左方外部聯結](../../../linq/perform-left-outer-joins.md)
- [如何從多個源 （LINQ） （C#） 填充物件集合](./how-to-populate-object-collections-from-multiple-sources-linq.md)
