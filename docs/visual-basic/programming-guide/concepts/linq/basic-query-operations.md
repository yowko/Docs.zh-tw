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
ms.openlocfilehash: 92ac5beb70526795eb140bd794e47981cebfea93
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410912"
---
# <a name="basic-query-operations-visual-basic"></a>基本查詢作業 (Visual Basic)
本主題提供 Visual Basic 中的語言整合式查詢（LINQ）運算式的簡介，以及您在查詢中執行的一些一般作業類型。 如需詳細資訊，請參閱下列主題：  
  
 [Visual Basic 中的 LINQ 簡介](../../language-features/linq/introduction-to-linq.md)  
  
 [查詢](../../../language-reference/queries/index.md)  
  
 [逐步解說：在 Visual Basic 中撰寫查詢](walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>指定資料來源（從）  
 在 LINQ 查詢中，第一個步驟是指定您想要查詢的資料來源。 因此， `From` 查詢中的子句一律會先出現。 查詢運算子會根據來源的類型來選取和塑造結果。  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 `From`子句會指定資料來源 `customers` 和*範圍變數* `cust` 。 範圍變數就像迴圈反覆運算變數，不同的是，在查詢運算式中，不會發生實際的反復專案。 執行查詢時，通常會使用 `For Each` 迴圈，範圍變數會當做中每個後續元素的參考 `customers` 。 因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。 如需使用和而不明確輸入來撰寫之查詢的範例，請參閱[查詢作業中的類型關聯性（Visual Basic）](type-relationships-in-query-operations.md)。  
  
 如需如何 `From` 在 Visual Basic 中使用子句的詳細資訊，請參閱[from 子句](../../../language-reference/queries/from-clause.md)。  
  
## <a name="filtering-data-where"></a>篩選資料（Where）  
 最常見的查詢作業可能是以布林運算式的形式套用篩選。 然後，此查詢只會傳回運算式為 true 的元素。 `Where`子句是用來執行篩選。 篩選器會指定要在結果序列中包含的資料來源中的哪些元素。 在下列範例中，只會包含在倫敦具有位址的客戶。  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 您可以使用邏輯運算子（例如 `And` 和） `Or` 來結合子句中的篩選條件運算式 `Where` 。 例如，若只要傳回來自倫敦且其名稱為 Devon 的客戶，請使用下列程式碼：  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 若要傳回來自倫敦或巴黎的客戶，請使用下列程式碼：  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 如需如何 `Where` 在 Visual Basic 中使用子句的詳細資訊，請參閱[Where 子句](../../../language-reference/queries/where-clause.md)。  
  
## <a name="ordering-data-order-by"></a>排序資料（Order By）  
 將傳回的資料排序為特定的順序，通常是很方便的方式。 `Order By`子句會使傳回序列中的專案在指定的欄位上進行排序。 例如，下列查詢會根據屬性來排序結果 `Name` 。 因為 `Name` 是字串，所以傳回的資料會依字母順序從 a 到 Z 排序。  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 若要以相反順序排序結果 (從 Z 到 A)，請使用 `Order By...Descending` 子句。 `Ascending`當沒有指定或時，預設值為 `Ascending` `Descending` 。  
  
 如需如何 `Order By` 在 Visual Basic 中使用子句的詳細資訊，請參閱[Order by 子句](../../../language-reference/queries/order-by-clause.md)。  
  
## <a name="selecting-data-select"></a>選取資料（選取）  
 `Select`子句會指定傳回元素的表單和內容。 例如，您可以指定您的結果是否包含完整的 `Customer` 物件、只有一個 `Customer` 屬性、屬性的子集、來自各種資料來源的屬性組合，或是以計算為基礎的一些新結果型別。 `Select` 子句不只產生一份來源項目時，作業稱為「投影」**。  
  
 若要取出由完整物件所組成的集合 `Customer` ，請選取範圍變數本身：  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 如果 `Customer` 實例是具有許多欄位的大型物件，而您想要取出的是名稱，您可以選取 `cust.Name` ，如下列範例所示。 區欄位型別推斷會辨識這項工作會將結果類型從物件集合變更 `Customer` 為字串的集合。  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 若要從資料來源選取多個欄位，您有兩個選擇：  
  
- 在 `Select` 子句中，指定您想要包含在結果中的欄位。 編譯器會定義具有這些欄位做為其屬性的匿名型別。 如需詳細資訊，請參閱[匿名](../../language-features/objects-and-classes/anonymous-types.md)型別。  
  
     因為下列範例中傳回的元素是匿名型別的實例，所以您無法在程式碼中的其他地方依名稱參考該型別。 類型的編譯器指定名稱包含在一般 Visual Basic 程式碼中不正確字元。 在下列範例中，查詢所傳回之集合中的元素 `londonCusts4` 是匿名型別的實例。  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -或-  
  
- 定義名為的型別，其中包含您想要包含在結果中的特定欄位，並在子句中建立和初始化型別的實例 `Select` 。 只有當您必須在傳回的集合以外的個別結果，或是您必須將它們當做方法呼叫中的參數傳遞時，才使用此選項。 `londonCusts5`下列範例中的類型是 IEnumerable （Of NamePhone）。  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 如需如何 `Select` 在 Visual Basic 中使用子句的詳細資訊，請參閱[Select 子句](../../../language-reference/queries/select-clause.md)。  
  
## <a name="joining-data-join-and-group-join"></a>聯結資料（聯結和群組聯結）  
 您可以 `From` 用數種方式在子句中結合一個以上的資料來源。 例如，下列程式碼會使用兩個數據源，並在結果中隱含結合兩者的屬性。 查詢會選取姓氏以母音開頭的學生。  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> 您可以使用在[如何：建立專案清單](how-to-create-a-list-of-items.md)中建立的學生清單來執行此程式碼。  
  
 `Join`關鍵字相當於 `INNER JOIN` SQL 中的。 它會根據兩個集合中元素之間相符的索引鍵值，結合兩個集合。 此查詢會傳回具有相符索引鍵值的全部或部分集合元素。 例如，下列程式碼會重複先前的隱含聯結動作。  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`將集合結合成單一階層式集合，就像 `LEFT JOIN` SQL 中的一樣。 如需詳細資訊，請參閱[聯結子句](../../../language-reference/queries/join-clause.md)和[群組聯結子句](../../../language-reference/queries/group-join-clause.md)。  
  
## <a name="grouping-data-group-by"></a>群組資料（分組依據）  
 您可以加入 `Group By` 子句，根據元素的一或多個欄位，將查詢結果中的專案分組。 例如，下列程式碼會依類別年度來分組學生。  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 如果您使用[如何：建立專案清單](how-to-create-a-list-of-items.md)中所建立的學生清單來執行此程式碼，則語句的輸出 `For Each` 會是：  
  
 Year：初級  
  
 Tucker，Michael  
  
 Garcia、Hugo  
  
 Garcia、Debra  
  
 Tucker、Lance  
  
 Year：資深  
  
 Omelchenko, Svetlana  
  
 Osada、包括 michiko  
  
 Fakhouri, Fadi  
  
 We feng、Hanying  
  
 Adams，Terry  
  
 Year： Freshman  
  
 Mortensen, Sven  
  
 Garcia、Cesar  
  
 下列程式碼中顯示的變化會排序類別年份，然後依姓氏排序每年中的學生。  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 如需的詳細資訊 `Group By` ，請參閱[Group by 子句](../../../language-reference/queries/group-by-clause.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic.IEnumerable%601>
- [使用 Visual Basic 撰寫 LINQ 入門](getting-started-with-linq.md)
- [查詢](../../../language-reference/queries/index.md)
- [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)
- [LINQ](../../language-features/linq/index.md)
