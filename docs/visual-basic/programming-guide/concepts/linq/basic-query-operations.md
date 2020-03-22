---
title: 基本查詢作業
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
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266374"
---
# <a name="basic-query-operations-visual-basic"></a>基本查詢作業 (Visual Basic)
本主題簡要介紹了視覺化基礎知識中的語言集成查詢 （LINQ） 運算式，以及您在查詢中執行的一些典型操作類型。 如需詳細資訊，請參閱下列主題：  
  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [查詢](../../../../visual-basic/language-reference/queries/index.md)  
  
 [逐步解說：在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>指定資料來源（來自）  
 在 LINQ 查詢中，第一步是指定要查詢的資料來源。 因此，`From`查詢中的子句始終排在第一位。 查詢運算子根據源的類型選擇和塑造結果。  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 子`From`句指定資料來源`customers`和*範圍變數*。 `cust` 範圍變數類似于迴圈反覆運算變數，只不過在查詢運算式中，不會發生實際反覆運算。 執行查詢時（通常通過使用`For Each`迴圈）時，範圍變數充當 對 中每個連續元素的`customers`引用。 因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。 有關使用顯式鍵入和未進行顯式鍵入的查詢的示例，請參閱[查詢操作中的類型關係（可視基本）。](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)  
  
 有關如何在 Visual Basic 中使用`From`子句的詳細資訊，請參閱[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。  
  
## <a name="filtering-data-where"></a>篩選資料（在哪裡）  
 最常見的查詢操作可能是以布林運算式的形式應用篩選器。 然後，查詢僅返回運算式為 true 的元素。 子`Where`句用於執行篩選。 篩選器指定資料來源中要包含在結果序列中的元素。 在下面的示例中，僅包括在倫敦有位址的客戶。  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 可以使用邏輯運算子（如 和`And``Or`）在`Where`子句中組合篩選器運算式。 例如，要僅返回來自倫敦且名稱為 Devon 的客戶，請使用以下代碼：  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 要從倫敦或巴黎返回客戶，請使用以下代碼：  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 有關如何在 Visual Basic 中使用`Where`子句的詳細資訊，請參閱[子句](../../../../visual-basic/language-reference/queries/where-clause.md)的位置 。  
  
## <a name="ordering-data-order-by"></a>訂購資料（按訂單）  
 將返回的資料按特定順序排序通常很方便。 子`Order By`句將導致返回序列中的元素在指定的欄位或欄位上進行排序。 例如，以下查詢根據`Name`屬性對結果進行排序。 因為`Name`是一個字串，返回的資料將按字母順序排序，從 A 到 Z。  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 若要以相反順序排序結果 (從 Z 到 A)，請使用 `Order By...Descending` 子句。 預設值為`Ascending`既不`Ascending`指定也不`Descending`指定時。  
  
 有關如何在視覺化基本版中使用`Order By`子句的詳細資訊，請參閱[按子句排序](../../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
## <a name="selecting-data-select"></a>選擇資料（選擇）  
 子`Select`句指定返回元素的形式和內容。 例如，可以指定結果是包含完整的`Customer`物件、一個`Customer`屬性、屬性子集、來自各種資料來源的屬性的組合，還是基於計算的一些新的結果類型。 `Select` 子句不只產生一份來源項目時，作業稱為「投影」**。  
  
 要檢索由完整`Customer`物件組成的集合，請選擇範圍變數本身：  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 如果`Customer`實例是具有許多欄位的大型物件，並且要檢索的只是名稱，則可以選擇`cust.Name`，如下例所示。 本地型別推斷認識到，這將結果類型從`Customer`物件集合更改為字串集合。  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 要從資料來源中選擇多個欄位，有兩種選擇：  
  
- 在子`Select`句中，指定要包含在結果中的欄位。 編譯器將定義一個匿名型別，該類型以這些欄位作為其屬性。 有關詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
     由於以下示例中返回的元素是匿名型別的實例，因此無法按代碼的其他位置參考型別。 類型的編譯器指定名稱包含在正常 Visual Basic 代碼中不正確字元。 在下面的示例中，查詢返回的集合中的元素`londonCusts4`是匿名型別的實例  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -或-  
  
- 定義包含要包含在結果中的特定欄位的命名類型，並在`Select`子句中創建和初始化該類型的實例。 僅當必須使用返回結果的集合之外的單個結果，或者您必須在方法調用中將它們作為參數傳遞時，才使用此選項。 以下示例中的類型`londonCusts5`為 IE無枚（NamePhone）。  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 有關如何在 Visual Basic 中使用`Select`子句的詳細資訊，請參閱[選擇子句](../../../../visual-basic/language-reference/queries/select-clause.md)。  
  
## <a name="joining-data-join-and-group-join"></a>加入資料（加入和組加入）  
 您可以通過多種方式將`From`子句中的多個資料來源合併。 例如，以下代碼使用兩個數據源，並在結果中隱式合併兩個數據源的屬性。 查詢選擇姓氏以母音開頭的學生。  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> 您可以使用在["如何：創建專案清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)"中創建的學生清單運行此代碼。  
  
 關鍵字`Join`等效于 SQL`INNER JOIN`中。 它基於兩個集合中元素之間的匹配鍵值組合兩個集合。 查詢返回具有匹配鍵值的全部或部分集合元素。 例如，以下代碼複製前一個隱式聯接的操作。  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`將集合合併到單個分層集合中，就像`LEFT JOIN`SQL 中的集合一樣。 有關詳細資訊，請參閱[加入子句](../../../../visual-basic/language-reference/queries/join-clause.md)和[組加入子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)。  
  
## <a name="grouping-data-group-by"></a>分組資料（分組）  
 您可以根據元素的`Group By`一個或多個欄位添加子句來對查詢結果中的元素進行分組。 例如，以下代碼按班級年份對學生進行分組。  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 如果使用"[如何創建：創建專案清單"](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)中創建的學生清單運行此代碼，則語句中的`For Each`輸出為：  
  
 年： 初級  
  
 塔克， 邁克爾  
  
 加西亞， 雨果  
  
 加西亞， 黛布拉  
  
 塔克， 蘭斯  
  
 年份： 高級  
  
 奧梅利琴科， 斯韋特蘭娜  
  
 奧薩達， 米奇科  
  
 法庫裡， 法迪  
  
 馮漢英  
  
 亞當斯， 特裡  
  
 年份： 新生  
  
 莫滕森， 斯文  
  
 加西亞， 塞薩爾  
  
 以下代碼中顯示的變體對班級年數進行排序，然後按姓氏每年對學生進行訂單。  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 有關 的詳細資訊`Group By`，請參閱[按子項分組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic.IEnumerable%601>
- [使用 Visual Basic 撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [查詢](../../../../visual-basic/language-reference/queries/index.md)
- [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
