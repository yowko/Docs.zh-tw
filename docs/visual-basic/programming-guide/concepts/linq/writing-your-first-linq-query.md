---
title: 撰寫第一個 LINQ 查詢 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 83a1b7629672c6a74fd29ce698a6b8e6e152b1da
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068946"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>撰寫第一個 LINQ 查詢 (Visual Basic)
「查詢」是指從資料來源中擷取資料的運算式。 查詢會以專用的查詢語言來表示。 經過一段時間，不同的語言所開發的不同類型的資料來源，例如 SQL 用於關聯式資料庫，而 XQuery 用於 XML。 這可讓您所需的應用程式開發人員若要了解新的查詢語言，每種類型的資料來源或支援的資料格式。  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 藉由提供一致的模型，可處理各種資料來源和格式的資料，可簡化這種情況。 在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢中，您所處理的一定是物件。 您可以使用相同的基本程式碼撰寫模式查詢及轉換 XML 文件中的資料、 SQL 資料庫、 ADO.NET 資料集和實體、.NET Framework 集合和任何其他來源或格式為其[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]才有提供者。 本文件說明建立三個階段，以及善用基本[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。  
  
## <a name="three-stages-of-a-query-operation"></a>查詢作業的三個階段  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢作業是由三個動作所組成：  
  
1.  取得資料來源。  
  
2.  建立查詢。  
  
3.  執行查詢。  
  
 在  [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，查詢的執行是不同的查詢建立。 您不只是藉由建立查詢擷取任何資料。 本主題稍後會詳細討論這一點。  
  
 下列範例說明查詢作業的三個部分。 此範例會使用整數的陣列做為方便存取的資料來源供示範之用。 不過，相同的概念也適用於其他資料來源。  
  
> [!NOTE]
>  在上[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，請確認**Option infer**設定為**上**。  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 輸出：  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>資料來源  
 因為在上述範例中的資料來源是陣列，意味著其也支援泛型<xref:System.Collections.Generic.IEnumerable%601>介面。 這項事實，可讓您使用陣列做為資料來源很[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。 支援 <xref:System.Collections.Generic.IEnumerable%601> 或衍生介面的類型，例如泛型 <xref:System.Linq.IQueryable%601> 稱為*可查詢的類型*。  
  
 作為隱含的可查詢類型的陣列，不需要修改或特殊處理，就可以做為[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]資料來源。 這也適用於任何支援的集合型別<xref:System.Collections.Generic.IEnumerable%601>，包括泛型<xref:System.Collections.Generic.List%601>， <xref:System.Collections.Generic.Dictionary%602>，和.NET Framework 類別庫中的其他類別。  
  
 如果來源資料已實作<xref:System.Collections.Generic.IEnumerable%601>，則[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]實作的功能所需的提供者*標準查詢運算子*該資料來源。 例如，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]會處理 XML 文件載入可查詢的工作<xref:System.Xml.Linq.XElement>類型，如下列範例所示。 如需有關標準查詢運算子的詳細資訊，請參閱[標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)。  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 具有[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]，您必須先建立物件關聯式對應在設計階段，以手動方式或使用[LINQ to SQL 工具，在 Visual Studio 中](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)Visual Studio 中。 您可以針對物件撰寫查詢，而 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 則會在執行階段處理與資料庫之間的通訊。 在下列範例中，`customers`代表在資料庫中，特定資料表和<xref:System.Data.Linq.Table%601>支援泛型<xref:System.Linq.IQueryable%601>。  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 如需如何建立特定資料來源類型的詳細資訊，請參閱各種 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 提供者的文件。 (如需這些提供者的清單，請參閱 < [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)。)基本規則很簡單：[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]資料來源是支援泛型的任何物件<xref:System.Collections.Generic.IEnumerable%601>介面或繼承自它的介面。  
  
> [!NOTE]
>  類型，例如<xref:System.Collections.ArrayList>支援非泛型<xref:System.Collections.IEnumerable>介面也可用來當做[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]資料來源。 如需使用的範例<xref:System.Collections.ArrayList>，請參閱 <<c2> [ 如何： 使用 LINQ (Visual Basic) 查詢 ArrayList](how-to-query-an-arraylist-with-linq.md)。  
  
## <a name="the-query"></a>查詢  
 在查詢中，您可以指定您想要從資料來源或來源擷取的資訊。 您也可以選擇指定如何這項資訊應該排序、 分組，或結構化，再將它傳回。 若要啟用查詢建立，Visual Basic 已併入新的查詢語法的語言。  
  
 當它執行時，在下列範例查詢會傳回所有偶數整數陣列，從`numbers`。  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 查詢運算式包含三個子句︰ `From`， `Where`，和`Select`。 討論的特定函式和每個查詢運算式子句的目的[基本查詢作業 (Visual Basic)](basic-query-operations.md)。 如需詳細資訊，請參閱 <<c0> [ 查詢](../../../../visual-basic/language-reference/queries/index.md)。 請注意，在[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，查詢定義通常是儲存在變數中，且稍後執行。 查詢變數，例如`evensQuery`在前一個範例中，必須是可查詢類型。 型別`evensQuery`是`IEnumerable(Of Integer)`、 指派使用區域型別推斷的編譯器。  
  
 請務必記住，查詢變數本身會採取任何動作，並不傳回任何資料。 它只會儲存查詢定義。 在上述範例中，它是`For Each`迴圈會執行查詢。  
  
## <a name="query-execution"></a>查詢執行  
 查詢執行會從查詢建立個別項目。 查詢建立定義查詢，但執行由不同的機制來觸發。 可以執行查詢，因為它定義 (*立即執行*)，或定義可以儲存和更新版本執行查詢 (*延後執行*)。  
  
### <a name="deferred-execution"></a>延後執行  
 典型[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢類似於在前一個範例中，在其中`evensQuery`定義。 它會建立查詢，但不會立即執行它。 相反地，查詢定義會儲存在查詢變數`evensQuery`。 在執行查詢之後，通常藉由使用`For Each`迴圈，並傳回序列的值，或藉由套用標準查詢運算子，例如`Count`或`Max`。 此程序指*延後執行*。  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 序列的值，您必須存取擷取的資料使用中的反覆運算變數`For Each`迴圈 (`number`在上述範例中)。 因為查詢變數`evensQuery`，保留查詢定義，而不是查詢結果中，您可以執行查詢，視您想要使用的查詢變數一次以上。 比方說，您可能會有資料庫由個別的應用程式持續更新的應用程式中。 您已建立該資料庫中擷取資料的查詢之後，您可以使用`For Each`擷取最新的資料每次迴圈重複執行查詢。  
  
 下列範例示範延後的執行如何運作。 之後`evensQuery2`定義和執行`For Each`迴圈，如同先前的範例中，資料來源中的某些項目`numbers`會變更。 然後第二個`For Each`迴圈執行`evensQuery2`一次。 結果就不同的第二個的時間，因為`For Each`迴圈會執行查詢一次，使用中的新值`numbers`。  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 輸出：  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>立即執行  
 延後執行查詢時，在查詢定義會儲存在查詢變數中供稍後執行。 在 立即執行，其定義時執行查詢。 當您套用的方法，需要存取的查詢結果個別項目時，就會觸發執行。 立即執行通常會強制使用其中一種標準查詢運算子會傳回單一值。 範例包括`Count`， `Max`， `Average`，和`First`。 這些標準查詢運算子會執行查詢，因為它們會套用，以計算並傳回單一結果。 如需傳回單一值的標準查詢運算子的詳細資訊，請參閱[彙總作業](aggregation-operations.md)，[項目作業](element-operations.md)，並[數量詞作業](quantifier-operations.md)。  
  
 下列查詢會傳回偶數數目的整數陣列中。 未儲存的查詢定義，並`numEvens`是一項簡單`Integer`。  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 您可以使用來達到相同的結果`Aggregate`方法。  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 您也可以強制執行查詢，藉由呼叫`ToList`或`ToArray`（立即） 的查詢或查詢變數 （延遲），如下列程式碼所示的方法。  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 在上一個範例中，`evensQuery3`是查詢變數，但`evensList`是清單和`evensArray`是陣列。  
  
 使用`ToList`或`ToArray`來強制立即執行是在您要立即執行查詢並快取單一集合物件中的結果的案例中特別有用。 如需這些方法的詳細資訊，請參閱[轉換資料類型](converting-data-types.md)。  
  
 您也可以讓查詢以使用執行`IEnumerable`方法，例如<xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>方法。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Visual Basic 撰寫 LINQ 入門](getting-started-with-linq.md)  
 [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [查詢](../../../../visual-basic/language-reference/queries/index.md)
