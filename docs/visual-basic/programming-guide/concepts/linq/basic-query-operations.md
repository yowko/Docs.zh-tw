---
title: 基本查詢作業 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: 12f10f30dd767f3435044f2bbebe0eb865c29d0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939370"
---
# <a name="basic-query-operations-visual-basic"></a>基本查詢作業 (Visual Basic)
本主題提供 Visual Basic 中的[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]運算式, 以及您在查詢中執行的一些一般作業類型的簡介。 如需詳細資訊，請參閱下列主題：  
  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [查詢](../../../../visual-basic/language-reference/queries/index.md)  
  
 [逐步解說：在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>指定資料來源 (從)  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]在查詢中, 第一個步驟是指定您想要查詢的資料來源。 因此, 查詢`From`中的子句一律會先出現。 查詢運算子會根據來源的類型來選取和塑造結果。  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 子句會指定資料`customers`源`cust`和*範圍變數。* `From` 範圍變數就像迴圈反覆運算變數, 不同的是, 在查詢運算式中, 不會發生實際的反復專案。 執行查詢時, 通常會使用`For Each`迴圈, 範圍變數會當做中`customers`每個後續元素的參考。 因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。 如需使用和而不明確輸入來撰寫之查詢的範例, 請參閱[查詢作業中的類型關聯性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。  
  
 如需如何在 Visual Basic 中使用`From`子句的詳細資訊, 請參閱[from 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。  
  
## <a name="filtering-data-where"></a>篩選資料 (Where)  
 最常見的查詢作業可能是以布林運算式的形式套用篩選。 然後, 此查詢只會傳回運算式為 true 的元素。 `Where`子句是用來執行篩選。 篩選器會指定要在結果序列中包含的資料來源中的哪些元素。 在下列範例中, 只會包含在倫敦具有位址的客戶。  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 您可以使用邏輯運算子 (例如`And`和`Or` ) 來結合子句中的`Where`篩選條件運算式。 例如, 若只要傳回來自倫敦且其名稱為 Devon 的客戶, 請使用下列程式碼:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 若要傳回來自倫敦或巴黎的客戶, 請使用下列程式碼:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 如需如何在 Visual Basic 中使用`Where`子句的詳細資訊, 請參閱[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。  
  
## <a name="ordering-data-order-by"></a>排序資料 (Order By)  
 將傳回的資料排序為特定的順序, 通常是很方便的方式。 `Order By`子句會使傳回序列中的專案在指定的欄位上進行排序。 例如, 下列查詢會根據`Name`屬性來排序結果。 因為`Name`是字串, 所以傳回的資料會依字母順序從 a 到 Z 排序。  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 若要以相反順序排序結果 (從 Z 到 A)，請使用 `Order By...Descending` 子句。 當沒有指定`Ascending` 或`Descending`時, 預設值為。 `Ascending`  
  
 如需如何在 Visual Basic 中使用`Order By`子句的詳細資訊, 請參閱[Order by 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
## <a name="selecting-data-select"></a>選取資料 (選取)  
 `Select`子句會指定傳回元素的表單和內容。 例如, 您可以指定您的結果是否包含完整`Customer`的物件、只有一個`Customer`屬性、屬性的子集、來自各種資料來源的屬性組合, 或是以計算為基礎的一些新結果型別。 `Select` 子句不只產生一份來源項目時，作業稱為「投影」。  
  
 若要取出由完整`Customer`物件所組成的集合, 請選取範圍變數本身:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 如果實例是具有許多欄位的大型物件, 而您想要取出的是名稱, 您可以選取`cust.Name`, 如下列範例所示。 `Customer` 區欄位型別推斷會辨識這項`Customer`工作會將結果類型從物件集合變更為字串的集合。  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 若要從資料來源選取多個欄位, 您有兩個選擇:  
  
- `Select`在子句中, 指定您想要包含在結果中的欄位。 編譯器會定義具有這些欄位做為其屬性的匿名型別。 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
     因為下列範例中傳回的元素是匿名型別的實例, 所以您無法在程式碼中的其他地方依名稱參考該型別。 類型的編譯器指定名稱包含在一般 Visual Basic 程式碼中不正確字元。 在下列範例中, 查詢`londonCusts4`所傳回之集合中的元素是匿名型別的實例。  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -或-  
  
- 定義名為的型別, 其中包含您想要包含在結果中的特定欄位, 並在`Select`子句中建立和初始化型別的實例。 只有當您必須在傳回的集合以外的個別結果, 或是您必須將它們當做方法呼叫中的參數傳遞時, 才使用此選項。 下列範例`londonCusts5`中的類型是 IEnumerable (of NamePhone)。  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 如需如何在 Visual Basic 中使用`Select`子句的詳細資訊, 請參閱[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。  
  
## <a name="joining-data-join-and-group-join"></a>聯結資料 (聯結和群組聯結)  
 您可以用數種方式在子句中結合`From`一個以上的資料來源。 例如, 下列程式碼會使用兩個數據源, 並在結果中隱含結合兩者的屬性。 查詢會選取姓氏以母音開頭的學生。  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> 您可以使用下列[方式來執行此程式碼: 建立的學生清單建立專案](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)清單。  
  
 關鍵字相當於 SQL 中的`INNER JOIN`。 `Join` 它會根據兩個集合中元素之間相符的索引鍵值, 結合兩個集合。 此查詢會傳回具有相符索引鍵值的全部或部分集合元素。 例如, 下列程式碼會重複先前的隱含聯結動作。  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`將集合結合成單一階層式集合, 就像`LEFT JOIN` SQL 中的一樣。 如需詳細資訊, 請參閱[聯結子句](../../../../visual-basic/language-reference/queries/join-clause.md)和[群組聯結子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)。  
  
## <a name="grouping-data-group-by"></a>群組資料 (分組依據)  
 您可以加入`Group By`子句, 根據元素的一或多個欄位, 將查詢結果中的專案分組。 例如, 下列程式碼會依類別年度來分組學生。  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 如果您使用下列[方式建立的程式碼:建立專案](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)清單, `For Each`語句的輸出為:  
  
 歷年初級  
  
 Tucker, Michael  
  
 Garcia、Hugo  
  
 Garcia、Debra  
  
 Tucker、Lance  
  
 歷年高  
  
 Omelchenko, Svetlana  
  
 Osada、包括 michiko  
  
 Fakhouri, Fadi  
  
 We feng、Hanying  
  
 Adams, Terry  
  
 歷年Freshman  
  
 Mortensen, Sven  
  
 Garcia、Cesar  
  
 下列程式碼中顯示的變化會排序類別年份, 然後依姓氏排序每年中的學生。  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 如需的詳細`Group By`資訊, 請參閱[group by 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic.IEnumerable%601>
- [使用 Visual Basic 撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [查詢](../../../../visual-basic/language-reference/queries/index.md)
- [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
