---
title: ':::no-loc(Join):::作業（c #）'
description: '兩個數據源的聯結會使物件與跨資料來源共用屬性的物件產生關聯。 瞭解 c # 中 LINQ framework 的聯結方法。'
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- ':::no-loc(Join):::'
- ':::no-loc(GroupJoin):::'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165691"
---
# <a name="no-locjoin-operations-c"></a>:::no-loc(Join):::作業（c #）

兩個資料來源的「聯結」**，就是某個資料來源中的物件，和另一個資料來源中共用通用屬性的物件的關聯。  
  
 :::no-loc(Join):::在以資料來源為目標的查詢中，對於彼此之間的關聯性無法直接遵循，ing 是一項重要的作業。 在物件導向的程式設計中，這可能表示物件之間的相互關聯沒有模組化，例如單向關聯性的返回方向。 一個單向關聯性的範例是「客戶」類別，其具有類型「城市」的屬性，但「城市」類別沒有「客戶」物件集合的屬性。 若您有「城市」物件清單，且您想要尋找每個城市中的所有客戶，您就可以使用聯結作業來尋找客戶。  
  
 LINQ 架構中所提供的 join 方法是 <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> 和 <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>。 這些方法會執行等聯結，或是執行根據其索引鍵相等與否配對兩個資料來源的聯結。 （為了進行比較，Transact-sql 支援 ' equals ' 以外的聯結運算子，例如 ' 小於 ' 運算子）。在關係資料庫詞彙中， <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> 會執行內部聯結，這是一種聯結類型，其中只會傳回在其他資料集中具有相符項的物件。 <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> 方法從關聯式資料庫觀點來看沒有直接的對應項目，但它會實作內部聯結和左方外部聯結的超集。 左方外部聯結是傳回第一個 (左) 資料來源中每個項目的聯結，即使它在其他資料來源中沒有相互關聯的項目也一樣。  
  
 以下概念圖示範兩個集合，以及兩個集合中包含在內部聯結或左外部聯結中的項目。  
  
 ![顯示內部&#47;外部的兩個重疊圓形。](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|C# 查詢運算式語法|相關資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|:::no-loc(Join):::|:::no-loc(Join):::s 以索引鍵選取器函式為基礎的兩個序列，並會解壓縮值的配對。|`join … in … on … equals …`|<xref:System.Linq.Enumerable.:::no-loc(Join):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(Join):::%2A?displayProperty=nameWithType>|  
|:::no-loc(GroupJoin):::|:::no-loc(Join):::以索引鍵選取器函式為基礎的兩個序列，並將每個元素的結果相符專案分組。|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例
  
### :::no-loc(Join):::  
  
下列範例會使用 `join … in … on … equals …` 子句，根據特定值聯結兩個序列：
  
[!code-csharp[:::no-loc(Join):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(Join):::)]  

### :::no-loc(GroupJoin):::  

下列範例會使用 `join … in … on … equals … into …` 子句，根據特定值聯結兩個序列，並將每個元素的結果相符專案分組：
  
[!code-csharp[:::no-loc(GroupJoin):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(GroupJoin):::)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)
- [匿名類型](../../classes-and-structs/anonymous-types.md)
- [制訂 :::no-loc(Join)::: 和交叉乘積查詢](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join 子句](../../../language-reference/keywords/join-clause.md)
- [:::no-loc(Join):::使用複合索引鍵](../../../linq/join-by-using-composite-keys.md)
- [如何從不同的檔案聯結內容（LINQ）（c #）](./how-to-join-content-from-dissimilar-files-linq.md)
- [排序 join 子句的結果](../../../linq/order-the-results-of-a-join-clause.md)
- [執行自訂的聯結作業](../../../linq/perform-custom-join-operations.md)
- [執行群組聯結](../../../linq/perform-grouped-joins.md)
- [執行內部聯結](../../../linq/perform-inner-joins.md)
- [執行左方外部聯結](../../../linq/perform-left-outer-joins.md)
- [如何從多個來源填入物件集合（LINQ）（c #）](./how-to-populate-object-collections-from-multiple-sources-linq.md)
