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
ms.openlocfilehash: 5587a60e97464324659b325e38a18ac25488d30d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="basic-query-operations-visual-basic"></a>基本查詢作業 (Visual Basic)
本主題提供簡介[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]運算式在 Visual Basic 中，並且一些您在查詢中執行的作業一般類型。 如需詳細資訊，請參閱下列主題：  
  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [逐步解說： 在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>指定資料來源 （來源）  
 在[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢中，第一個步驟是指定您想要查詢的資料來源。 因此，`From`子句的查詢中一律是第一次。 查詢運算子會選取和圖形的來源類型為基礎的結果。  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 `From`子句指定的資料來源， `customers`，和*範圍變數*， `cust`。 範圍變數是類似於迴圈的反覆項目變數中，不同之處在於查詢運算式中沒有實際的反覆項目，就會發生。 查詢執行時，通常使用`For Each`迴圈，做為在每個後續項目參考的範圍變數`customers`。 因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。 寫入逾時或無明確輸入查詢的範例，請參閱[查詢作業 (Visual Basic) 中的類型關聯性](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。  
  
 如需有關如何使用`From`子句在 Visual Basic，請參閱[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。  
  
## <a name="filtering-data-where"></a>篩選資料 （位置）  
 可能最常見的查詢作業套用篩選的布林運算式的形式。 然後查詢會傳回只在運算式為 true 的元素。 A`Where`子句用來執行的篩選。 篩選器會指定要包含在結果序列中的資料來源中的哪些項目。 在下列範例中，只有這些客戶在倫敦 （london） 的位址會包含。  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 您可以使用邏輯運算子，例如`And`和`Or`結合篩選條件運算式中的`Where`子句。 例如，若要傳回只有那些客戶從倫敦 （london） 以及其名稱是 Devon，使用下列程式碼：  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 若要從倫敦 （london） 或巴黎傳回客戶，請使用下列程式碼：  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 如需有關如何使用`Where`子句在 Visual Basic，請參閱[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。  
  
## <a name="ordering-data-order-by"></a>排序資料 (Order By)  
 通常很方便地排序傳回的資料排列成非特定順序。 `Order By`子句便會傳回指定的欄位或欄位排序序列中的項目。 例如，下列查詢會排序結果根據`Name`屬性。 因為`Name`是一個字串，將依照字母順序排序傳回的資料，從 A 到 Z。  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 若要以相反順序排序結果 (從 Z 到 A)，請使用 `Order By...Descending` 子句。 預設值是`Ascending`當兩者皆非`Ascending`也`Descending`指定。  
  
 如需有關如何使用`Order By`子句在 Visual Basic，請參閱[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
## <a name="selecting-data-select"></a>選取的資料 （選取）  
 `Select`子句會指定表單並傳回項目的內容。 例如，您可以指定是否將結果將會包含完整`Customer`物件，其中一個`Customer`屬性、 屬性的子集、 從各種資料來源或某些新的結果型別屬性的組合為基礎的計算。 `Select` 子句不只產生一份來源項目時，作業稱為「投影」。  
  
 若要擷取集合，其中包含完整`Customer`物件，選取本身的範圍變數：  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 如果`Customer`執行個體是大型物件，有許多欄位，以及所有您想要擷取是的名稱，您可以選取`cust.Name`，如下列範例所示。 這會變更結果型別集合中的區域類型推斷會辨識`Customer`的字串集合的物件。  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 若要選取多個欄位從資料來源，您有兩個選擇：  
  
-   在`Select`子句，指定您想要包含在結果中的欄位。 編譯器會在定義的那些欄位做為其屬性的匿名型別。 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
     在下列範例傳回的元素是匿名類型的執行個體，因為您無法為型別依名稱參考其他地方程式碼中。 編譯器指定類型名稱包含在標準的 Visual Basic 程式碼中無效的字元。 在下列範例中，在集合中的查詢所傳回的項目`londonCusts4`是匿名類型的執行個體  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     -或-  
  
-   定義包含您想要包含在結果中，以及建立和初始化中的型別之執行個體的特定欄位的具名的類型`Select`子句。 只有當您必須使用個別結果之外的記憶體回收會傳回這些，或如果您必須將其傳遞做為方法呼叫中的參數，請使用此選項。 型別`londonCusts5`在下列範例中是 IEnumerable (Of NamePhone)。  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 如需有關如何使用`Select`子句在 Visual Basic，請參閱[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。  
  
## <a name="joining-data-join-and-group-join"></a>聯結 （聯結和群組聯結） 的資料  
 您可以結合多個資料來源中的`From`子句數種方式。 例如，下列程式碼會使用兩個資料來源，並隱含地結合來自這兩種結果中的屬性。 查詢會選取的學生姓氏開頭為母音。  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  您可以執行此程式碼中建立的學員清單[How to： 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。  
  
 `Join`關鍵字相當於`INNER JOIN`SQL 中。 它結合了兩個集合中的項目之間的比對索引鍵值為基礎的兩個集合。 查詢會傳回全部或部分有相符的索引鍵的值的集合項目。 例如，下列程式碼複製先前的隱含聯結的動作。  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join` 將集合合併成單一階層式實體集合，就像是`LEFT JOIN`SQL 中。 如需詳細資訊，請參閱[Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md)和[Group Join 子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)。  
  
## <a name="grouping-data-group-by"></a>群組 (Group By) 的資料  
 您可以加入`Group By`子句分組查詢結果，根據一個或多個欄位的項目中的項目。 例如，下列程式碼會將學生分組類別年。  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 如果您執行此程式碼使用的學生在中建立清單[How to： 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)，從輸出`For Each`陳述式：  
  
 年份： Junior  
  
 Tucker Michael  
  
 Garcia Hugo  
  
 Garcia 蔡  
  
 Tucker 騎士  
  
 年份： 資深  
  
 Omelchenko Svetlana  
  
 Osada Michiko  
  
 Fakhouri Fadi  
  
 Hanying Feng  
  
 Adams Terry  
  
 年份： 包括新生諮詢人員  
  
 Mortensen Sven  
  
 Garcia Cesar  
  
 下列程式碼所示的變化年級，，然後每年排列學生的姓氏。  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 如需有關`Group By`，請參閱[群組 By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [使用 Visual Basic 撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)  
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
