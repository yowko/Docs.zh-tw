---
title: 聯結作業
ms.date: 07/20/2015
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
ms.openlocfilehash: 2e299b407712148db92c1c19a32fa318737ccf76
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397541"
---
# <a name="join-operations-visual-basic"></a>聯結作業（Visual Basic）
兩個資料來源的「聯結」**，就是某個資料來源中的物件，和另一個資料來源中共用通用屬性的物件的關聯。  
  
 對於不能直接追蹤目標資料來源彼此之間的關聯性的查詢而言，聯結是很重要的作業。 在物件導向的程式設計中，這可能表示物件之間的相互關聯沒有模組化，例如單向關聯性的返回方向。 一個單向關聯性的範例是「客戶」類別，其具有類型「城市」的屬性，但「城市」類別沒有「客戶」物件集合的屬性。 若您有「城市」物件清單，且您想要尋找每個城市中的所有客戶，您就可以使用聯結作業來尋找客戶。  
  
 LINQ 架構中所提供的 join 方法是 <xref:System.Linq.Enumerable.Join%2A> 和 <xref:System.Linq.Enumerable.GroupJoin%2A>。 這些方法會執行等聯結，或是執行根據其索引鍵相等與否配對兩個資料來源的聯結。 （為了進行比較，Transact-sql 支援 ' equals ' 以外的聯結運算子，例如 ' 小於 ' 運算子）。在關係資料庫詞彙中， <xref:System.Linq.Enumerable.Join%2A> 會執行內部聯結，這是一種聯結類型，其中只會傳回在其他資料集中具有相符項的物件。 <xref:System.Linq.Enumerable.GroupJoin%2A> 方法從關聯式資料庫觀點來看沒有直接的對應項目，但它會實作內部聯結和左方外部聯結的超集。 左方外部聯結是傳回第一個 (左) 資料來源中每個項目的聯結，即使它在其他資料來源中沒有相互關聯的項目也一樣。  
  
 以下概念圖示範兩個集合，以及兩個集合中包含在內部聯結或左外部聯結中的項目。  
  
 ![顯示內部&#47;外部的兩個重疊圓形。](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>方法  
  
|方法名稱|Description|Visual Basic 查詢運算式語法|相關資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Join|根據索引鍵選取器函式聯結兩個序列並擷取值組。|`From x In …, y In … Where x.a = y.a`<br /><br /> -或-<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|根據索引鍵選取器函式聯結兩個序列，並為每個項目的相符結果進行分組。|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)
- [匿名類型](../../language-features/objects-and-classes/anonymous-types.md)
- [制定聯結和交叉乘積查詢](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [Join 子句](../../../language-reference/queries/join-clause.md)
- [如何：從不同的檔案聯結內容（LINQ）（Visual Basic）](how-to-join-content-from-dissimilar-files-linq.md)
- [如何：從多個來源填入物件集合（LINQ）（Visual Basic）](how-to-populate-object-collections-from-multiple-sources-linq.md)
