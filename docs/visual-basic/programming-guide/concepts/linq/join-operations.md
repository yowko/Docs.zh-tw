---
title: "聯結作業 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dce1adb5b918674bc8ee8fc48c8ff5b3c3814a88
ms.lasthandoff: 03/13/2017

---
# <a name="join-operations-visual-basic"></a>聯結作業 (Visual Basic)
A*聯結*的兩個資料來源是指某個資料來源中的物件與另一個資料來源中的共同屬性的物件關聯。  
  
 對於不能直接追蹤目標資料來源彼此之間的關聯性的查詢而言，聯結是很重要的作業。 在物件導向的程式設計中，這可能表示物件之間的相互關聯沒有模組化，例如單向關聯性的返回方向。 一個單向關聯性的範例是「客戶」類別，其具有類型「城市」的屬性，但「城市」類別沒有「客戶」物件集合的屬性。 若您有「城市」物件清單，且您想要尋找每個城市中的所有客戶，您就可以使用聯結作業來尋找客戶。  
  
 LINQ 架構中提供的聯結方法為<xref:System.Linq.Enumerable.Join%2A>和<xref:System.Linq.Enumerable.GroupJoin%2A>.</xref:System.Linq.Enumerable.GroupJoin%2A> </xref:System.Linq.Enumerable.Join%2A> 這些方法會執行聯結或根據索引鍵相等與否的兩個資料來源的聯結。 (相較下，Transact-SQL 支援「等於」運算子以外的聯結運算子，例如「小於」運算字)。在關聯式資料庫術語<xref:System.Linq.Enumerable.Join%2A>實作內部聯結，一種聯結中，只有在其他資料集中有相符的物件會傳回。</xref:System.Linq.Enumerable.Join%2A> <xref:System.Linq.Enumerable.GroupJoin%2A>方法在關聯式資料庫詞彙中，有沒有直接的對等用法，但它會實作內部聯結及左外部聯結的超集。</xref:System.Linq.Enumerable.GroupJoin%2A> 左外部聯結是傳回每個元素的第一個 （左） 資料來源的聯結，即使它具有其他資料來源中的任何相關項目。  
  
 以下概念圖示範兩個集合，以及兩個集合中包含在內部聯結或左外部聯結中的項目。  
  
 ![兩個重疊圓形顯示內部/外部。] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Join|根據索引鍵選取器函式聯結兩個序列並擷取值組。|`From x In …, y In … Where x.a = y.a`<br /><br /> -或-<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></xref:System.Linq.Queryable.Join%2A?displayProperty=fullName>|  
|GroupJoin|根據索引鍵選取器函式聯結兩個序列，並為每個項目的相符結果進行分組。|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq></xref:System.Linq>   
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [制定聯結和交叉乘積查詢](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)   
 [Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md)   
 [如何︰ 將內容從不同的檔案 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)   
 [如何︰ 填入物件集合，從多個來源 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
