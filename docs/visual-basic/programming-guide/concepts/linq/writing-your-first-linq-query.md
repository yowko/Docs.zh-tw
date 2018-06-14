---
title: 撰寫第一個 LINQ 查詢 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: f426aac5358837563081d2bf9783f6d4fe04d853
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654882"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>撰寫第一個 LINQ 查詢 (Visual Basic)
「查詢」是指從資料來源中擷取資料的運算式。 查詢會在專用的查詢語言來表示。 經過一段時間，不同語言所開發的不同類型的資料來源，例如 SQL 用於關聯式資料庫，而 XQuery 用於 XML。 這可讓您所需的應用程式開發人員若要了解新的查詢語言，每種類型的資料來源或資料格式的支援。  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 藉由提供一致的模型，以處理各種資料來源和格式的資料，可簡化這種情況。 在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢中，您所處理的一定是物件。 您可以使用相同的基本程式碼撰寫模式查詢及轉換 XML 文件中的資料、 SQL 資料庫、 ADO.NET 資料集和實體、.NET Framework 集合和任何其他來源或格式為其[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]才有提供者。 本文件說明的三個階段的建立和使用 basic[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。  
  
## <a name="three-stages-of-a-query-operation"></a>查詢作業的三個階段  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢作業包含三個動作：  
  
1.  取得資料來源。  
  
2.  建立查詢。  
  
3.  執行查詢。  
  
 在[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，執行查詢會從查詢建立的不同。 您只要建立查詢不擷取任何資料。 本主題稍後會詳細討論這一點。  
  
 下列範例說明查詢作業的三個部分。 為了示範之用，範例會使用整數的陣列做為方便的資料來源。 不過，相同的概念也適用於其他資料來源。  
  
> [!NOTE]
>  在[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，請確認**Option infer**設**上**。  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 輸出：  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>資料來源  
 因為前一個範例中的資料來源是一個陣列，它會隱含地支援泛型<xref:System.Collections.Generic.IEnumerable%601>介面。 它是可讓您使用做為資料來源的陣列，此事實[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。 支援 <xref:System.Collections.Generic.IEnumerable%601> 或衍生介面的類型，例如泛型 <xref:System.Linq.IQueryable%601> 稱為*可查詢的類型*。  
  
 做為隱含的可查詢類型，陣列不需要修改或特殊處理，做為[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]資料來源。 也適用於任何支援的集合型別<xref:System.Collections.Generic.IEnumerable%601>，包括泛型<xref:System.Collections.Generic.List%601>， <xref:System.Collections.Generic.Dictionary%602>，與其他.NET Framework 類別庫中的類別。  
  
 如果來源資料已經實作<xref:System.Collections.Generic.IEnumerable%601>、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]實作的功能所需的提供者*標準查詢運算子*針對該資料來源。 例如，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]會處理 XML 文件載入可供查詢的工作<xref:System.Xml.Linq.XElement>類型，如下列範例所示。 如需標準查詢運算子的詳細資訊，請參閱[標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)。  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 與[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]，第一次建立物件關聯式對應在設計階段，以手動方式或使用[LINQ to SQL 工具，Visual Studio 中](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)Visual Studio 中。 您可以針對物件撰寫查詢，而 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 則會在執行階段處理與資料庫之間的通訊。 在下列範例中，`customers`代表在資料庫中，特定資料表及<xref:System.Data.Linq.Table%601>支援泛型<xref:System.Linq.IQueryable%601>。  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 如需如何建立特定資料來源類型的詳細資訊，請參閱各種 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 提供者的文件。 (如需這些提供者的清單，請參閱[LINQ (Language-Integrated Query ()](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)。)基本規則很簡單：[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]資料來源是支援一般的任何物件<xref:System.Collections.Generic.IEnumerable%601>介面或從它繼承的介面。  
  
> [!NOTE]
>  這類類型<xref:System.Collections.ArrayList>支援非泛型<xref:System.Collections.IEnumerable>介面也可用來當作[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]資料來源。 如需範例，會使用<xref:System.Collections.ArrayList>，請參閱[如何： 查詢使用 LINQ (Visual Basic) ArrayList](how-to-query-an-arraylist-with-linq.md)。  
  
## <a name="the-query"></a>查詢  
 在查詢中，您可以指定您想要從來源或資料來源中擷取的資訊。 您也可以指定如何該資訊應該排序、 分組，或結構化傳回之前的選擇。 若要啟用查詢建立，Visual Basic 已併入新的查詢語法的語言。  
  
 當它執行時，在下列範例查詢會傳回所有偶數整數陣列中，從`numbers`。  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 查詢運算式包含三個子句： `From`， `Where`，和`Select`。 中會討論特定函式和每個查詢運算式子句的目的[基本查詢作業 (Visual Basic)](basic-query-operations.md)。 如需詳細資訊，請參閱[查詢](../../../../visual-basic/language-reference/queries/queries.md)。 請注意，在[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，查詢定義通常是儲存在變數中，而且稍後執行。 查詢變數，例如`evensQuery`在上述範例中，必須是可查詢的型別。 型別`evensQuery`是`IEnumerable(Of Integer)`、 指派的編譯器使用區域類型推斷。  
  
 請務必記得，查詢變數本身會採取任何動作，並不傳回任何資料。 它只會儲存查詢定義。 在上述範例中，它是`For Each`迴圈執行查詢。  
  
## <a name="query-execution"></a>查詢執行  
 查詢執行會與 查詢建立分開的。 查詢建立定義查詢，但執行會觸發不同的機制。 可以執行的查詢，因為它定義 (*立即執行*)，或定義可以儲存和更新版本才能執行查詢 (*延後執行*)。  
  
### <a name="deferred-execution"></a>延後執行  
 一般[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢類似於在上一個範例中，在其中一個`evensQuery`定義。 它會建立查詢，但不會立即執行它。 相反地，查詢定義會儲存在查詢變數`evensQuery`。 在執行查詢之後，通常藉由使用`For Each`迴圈，而傳回序列的值，或藉由套用標準查詢運算子，例如`Count`或`Max`。 此程序指*延後執行*。  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 值的序列，您必須存取所擷取的資料使用中的反覆項目變數`For Each`迴圈 (`number`前一個範例中)。 因為查詢變數`evensQuery`，保留查詢定義，而不是查詢結果中，您可以執行查詢，視您想要使用查詢變數一次以上。 例如，您可能必須將資料庫由個別的應用程式持續更新的應用程式中。 建立查詢，從該資料庫擷取資料之後，您可以使用`For Each`擷取最新的資料每次迴圈重複執行查詢。  
  
 下列範例會示範延後的執行如何運作。 之後`evensQuery2`定義及執行`For Each`迴圈中，如同先前的範例中，資料來源中的某些項目`numbers`會變更。 第二個然後`For Each`迴圈執行時`evensQuery2`一次。 結果就不同，第二次因為`For Each`迴圈執行的查詢，使用中的新值`numbers`。  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 輸出：  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>立即執行  
 在延後執行的查詢中，查詢定義會儲存在稍後執行的查詢變數。 立即執行，在查詢執行在其定義的時間。 當您套用要求的查詢結果個別項目的存取的方法時，會觸發執行。 立即執行通常會強制使用其中一種傳回單一值的標準查詢運算子。 範例包括`Count`， `Max`， `Average`，和`First`。 這些標準查詢運算子會執行查詢，因為它們會套用，以計算並傳回單一結果。 如需有關傳回單一值的標準查詢運算子的詳細資訊，請參閱[彙總作業](aggregation-operations.md)，[項目作業](element-operations.md)，和[數量詞作業](quantifier-operations.md)。  
  
 下列查詢會傳回計數的偶數整數的陣列。 未儲存查詢定義，以及`numEvens`是簡單`Integer`。  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 您可以使用來達到相同結果`Aggregate`方法。  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 您也可以強制執行查詢，藉由呼叫`ToList`或`ToArray`（即時） 的查詢或查詢變數 （延遲），如下列程式碼所示的方法。  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 在上一個範例中，`evensQuery3`是查詢變數，但`evensList`是清單和`evensArray`是陣列。  
  
 使用`ToList`或`ToArray`強制立即執行是在您要立即執行查詢並快取單一集合物件中的結果的情況下特別有用。 如需有關這些方法的詳細資訊，請參閱[轉換資料類型](converting-data-types.md)。  
  
 您也可以讓查詢執行使用`IEnumerable`方法，例如<xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>方法。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Visual Basic 撰寫 LINQ 入門](getting-started-with-linq.md)  
 [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)
