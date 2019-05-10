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
ms.openlocfilehash: af99a6c22239be1f9f03bafd8323c73f83df5c51
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642268"
---
# <a name="basic-query-operations-visual-basic"></a>基本查詢作業 (Visual Basic)
本主題提供簡介[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]運算式在 Visual Basic 中，以及一些典型的一種您在查詢中執行的作業。 如需詳細資訊，請參閱下列主題：  
  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [查詢](../../../../visual-basic/language-reference/queries/index.md)  
  
 [逐步解說：在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>指定資料來源 （來源）  
 在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢中，第一個步驟是指定您想要查詢的資料來源。 因此，`From`在查詢中的子句一律會先出現。 查詢運算子來選取和塑造結果取決於來源的類型。  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 `From`子句會指定資料來源`customers`，以及*範圍變數*， `cust`。 範圍變數是迴圈的反覆項目變數，例如，不同之處在於查詢運算式中，在沒有實際反覆項目，就會發生。 查詢執行時，通常使用`For Each`迴圈中，範圍變數做為在每個後續項目的參考`customers`。 因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。 如需撰寫使用，而不需要明確的輸入查詢的範例，請參閱[查詢作業 (Visual Basic) 中的型別關聯性](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。  
  
 如需有關如何使用`From`子句，在 Visual Basic 中，請參閱[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。  
  
## <a name="filtering-data-where"></a>篩選資料 （位置）  
 可能最常見的查詢作業套用篩選的布林運算式的形式。 然後查詢會傳回只在運算式為 true 的元素。 A`Where`子句用來執行篩選。 篩選會指定要包含在產生的序列中的資料來源中的哪些項目。 在下列範例中，僅有的地址在倫敦的客戶則會包含項目。  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 您可以使用邏輯運算子，例如`And`並`Or`結合篩選條件運算式中的`Where`子句。 比方說，如果要傳回的只有這些客戶來自 London 你是誰，且其名稱是 Devon，使用下列程式碼：  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 若要傳回來自 London 或 Paris 的客戶，使用下列程式碼：  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 如需有關如何使用`Where`子句，在 Visual Basic 中，請參閱[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。  
  
## <a name="ordering-data-order-by"></a>排序資料 (Order By)  
 通常很方便就可以放到特定的順序排序傳回的資料。 `Order By`子句會造成指定的欄位或欄位排序傳回的序列的項目。 例如，下列查詢會排序結果根據`Name`屬性。 因為`Name`是字串，會依字母順序，排序傳回的資料，從 A 到 Z。  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 若要以相反順序排序結果 (從 Z 到 A)，請使用 `Order By...Descending` 子句。 預設值是`Ascending`時都`Ascending`也`Descending`指定。  
  
 如需有關如何使用`Order By`子句，在 Visual Basic 中，請參閱[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
## <a name="selecting-data-select"></a>選取 (Select) 的資料  
 `Select`子句指定的格式和內容傳回的項目。 比方說，您可以指定是否將結果包含完整`Customer`物件，其中一個`Customer`屬性、 屬性的子集、 從各種資料來源或一些新的結果型別屬性的組合為基礎的計算。 `Select` 子句不只產生一份來源項目時，作業稱為「投影」。  
  
 若要擷取集合，其中包含完整`Customer`物件選取範圍變數本身：  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 如果`Customer`執行個體的大型物件，都有許多欄位，以及所有您想要擷取是名稱，您可以選取`cust.Name`，如下列範例所示。 區域類型推斷會辨識此集合中的變更的結果型別`Customer`字串集合的物件。  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 若要選取多個欄位從資料來源，您會有兩個選擇：  
  
- 在 `Select`子句，指定您想要包含在結果中的欄位。 編譯器會定義匿名型別具有為其屬性的這些欄位。 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
     因為傳回的項目，在下列範例中是匿名型別執行個體，您無法為型別依名稱參考其他位置中您的程式碼。 編譯器指定類型名稱包含在一般的 Visual Basic 程式碼中無效的字元。 在下列範例中，在集合中的查詢所傳回的項目`londonCusts4`匿名類型的執行個體  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -或-  
  
- 定義具名型別，其中包含您想要包含在結果中，以及建立和初始化中的型別之執行個體的特定欄位`Select`子句。 只有當您必須使用個別的結果，會傳回這些，集合之外，或如果您必須將它們傳遞為方法呼叫中的參數，請使用此選項。 型別`londonCusts5`在下列範例中是 IEnumerable (Of NamePhone)。  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 如需有關如何使用`Select`子句，在 Visual Basic 中，請參閱[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。  
  
## <a name="joining-data-join-and-group-join"></a>（聯結及群組聯結） 聯結的資料  
 您可以結合多個資料來源中的`From`子句以數種方式。 比方說，下列程式碼會使用兩個資料來源，並隱含地結合來自這兩個結果中的屬性。 查詢會選取最後一個名稱以母音開頭的學生。  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
>  您可以執行此程式碼中建立的學生清單[How to:建立項目清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。  
  
 `Join`關鍵字相當於`INNER JOIN`SQL 中。 它結合了兩個集合中的項目之間的比對索引鍵值為基礎的兩個集合。 查詢會傳回所有或部分具有相符索引鍵值的集合項目。 例如，下列程式碼重複先前的隱含聯結的動作。  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` 將集合合併成單一的階層式集合，就像`LEFT JOIN`SQL 中。 如需詳細資訊，請參閱 < [Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md)並[Group Join 子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)。  
  
## <a name="grouping-data-group-by"></a>分組資料 （依群組）  
 您可以新增`Group By`子句分組查詢結果，根據一個或多個欄位的項目中的項目。 例如，下列程式碼會將學生分組類別年。  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 如果您執行此程式碼使用的中建立的學生清單[How to:建立清單的項目](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)，從輸出`For Each`陳述式：  
  
 年份：Junior  
  
 Tucker Michael  
  
 牙哥加西亞島 Hugo  
  
 牙哥加西亞島 Debra  
  
 Tucker Lance  
  
 年份：資深  
  
 Omelchenko, Svetlana  
  
 Osada Michiko  
  
 Fakhouri Fadi  
  
 Feng Hanying  
  
 Adams Terry  
  
 年份：包括新生諮詢人員  
  
 Mortensen, Sven  
  
 牙哥加西亞島 Cesar  
  
 下列程式碼所示的變化年級，並依姓氏然後排列每年的學生。  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 如需詳細資訊`Group By`，請參閱 <<c2> [ 群組的子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic.IEnumerable%601>
- [使用 Visual Basic 撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [查詢](../../../../visual-basic/language-reference/queries/index.md)
- [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
