---
title: 撰寫第一個 LINQ 查詢 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 5c83d888f65ce5c216327e94c5d4d1267fb93c29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952003"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>撰寫第一個 LINQ 查詢 (Visual Basic)
「查詢」是指從資料來源中擷取資料的運算式。 查詢是以專用的查詢語言表示。 經過一段時間後, 針對不同類型的資料來源 (例如, 適用于關係資料庫的 SQL 和 XQuery for XML) 開發了不同的語言。 如此一來, 應用程式開發人員就必須針對支援的每種資料來源或資料格式, 學習新的查詢語言。  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]藉由提供一致的模型來處理各種資料來源和格式的資料, 來簡化這種情況。 在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢中，您所處理的一定是物件。 您可以使用相同的基本編碼模式來查詢和轉換 XML 檔、SQL 資料庫、ADO.NET 資料集和實體、.NET Framework 集合, 以及[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]提供者可用的任何其他來源或格式的資料。 本檔說明建立和使用基本[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢的三個階段。  
  
## <a name="three-stages-of-a-query-operation"></a>查詢作業的三個階段  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢作業包含三個動作:  
  
1. 取得資料來源或來源。  
  
2. 建立查詢。  
  
3. 執行查詢。  
  
 在[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]中, 查詢的執行與查詢的建立方式不同。 您只要建立查詢, 就不會抓取任何資料。 本主題稍後會詳細討論這一點。  
  
 下列範例說明查詢作業的三個部分。 此範例會使用整數陣列做為示範用途的方便資料來源。 不過, 相同的概念也適用于其他資料來源。  
  
> [!NOTE]
> 在 [[編譯] 頁面上, [專案設計工具] (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), 確定 [**選項推斷**] 已設定為 [**開啟**]。  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 輸出：  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>資料來源  
 因為上一個範例中的資料來源是陣列, 所以它會隱含支援泛型<xref:System.Collections.Generic.IEnumerable%601>介面。 這是可讓您使用陣列做為[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢資料來源的事實。 支援 <xref:System.Collections.Generic.IEnumerable%601> 或衍生介面的類型，例如泛型 <xref:System.Linq.IQueryable%601> 稱為*可查詢的類型*。  
  
 以隱含方式查詢的類型而言, 陣列不需要進行修改或特殊處理, 就[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]能做為資料來源。 任何支援<xref:System.Collections.Generic.IEnumerable%601>的集合類型也是如此, 包括泛型<xref:System.Collections.Generic.List%601>、 <xref:System.Collections.Generic.Dictionary%602>和 .NET Framework Class Library 中的其他類別。  
  
 如果來源資料尚未執行<xref:System.Collections.Generic.IEnumerable%601> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , 則需要提供者, 才能為該資料來源執行*標準查詢運算子*的功能。 例如, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]會處理將 XML 檔載入到可查詢<xref:System.Xml.Linq.XElement>類型的工作, 如下列範例所示。 如需標準查詢運算子的詳細資訊, 請參閱[標準查詢運算子總覽 (Visual Basic)](standard-query-operators-overview.md)。  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 在中, 您會先以手動方式或使用 Visual Studio[中 Visual Studio 中的 LINQ to SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2), 在設計階段建立物件關聯式對應。 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 您可以針對物件撰寫查詢，而 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 則會在執行階段處理與資料庫之間的通訊。 在下列範例中, `customers`代表資料庫中的特定資料表, 並<xref:System.Data.Linq.Table%601>支援泛型<xref:System.Linq.IQueryable%601>。  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 如需如何建立特定資料來源類型的詳細資訊，請參閱各種 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 提供者的文件。 (如需這些提供者的清單, 請參閱[LINQ (語言整合式查詢)](../../../../visual-basic/programming-guide/concepts/linq/index.md))。基本規則很簡單: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]資料來源是支援泛型<xref:System.Collections.Generic.IEnumerable%601>介面的任何物件, 或繼承自它的介面。  
  
> [!NOTE]
> 支援非泛型<xref:System.Collections.ArrayList> <xref:System.Collections.IEnumerable>介面的類型 (例如) 也[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]可以當做資料來源使用。 如需使用<xref:System.Collections.ArrayList>的範例, 請參閱[如何:使用 LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md)查詢 ArrayList。  
  
## <a name="the-query"></a>查詢  
 在查詢中, 您可以指定您想要從資料來源或來源中取出的資訊。 您也可以選擇指定該資訊在傳回之前應如何排序、分組或結構化。 若要啟用查詢建立, Visual Basic 已將新的查詢語法併入語言中。  
  
 執行時, 下列範例中的查詢會傳回整數陣列`numbers`中的所有偶數數位。  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 查詢運算式包含三個子句: `From`、 `Where`和`Select`。 [基本查詢作業 (Visual Basic)](basic-query-operations.md)中會討論每個查詢運算式子句的特定函數和用途。 如需詳細資訊, 請參閱[查詢](../../../../visual-basic/language-reference/queries/index.md)。 請注意, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]在中, 查詢定義通常會儲存在變數中, 並于稍後執行。 查詢變數 (如`evensQuery`前一個範例中的) 必須是可查詢的型別。 的類型`evensQuery`是`IEnumerable(Of Integer)`, 由編譯器使用區欄位型別推斷來指派。  
  
 請務必記住, 查詢變數本身不會採取任何動作, 也不會傳回任何資料。 它只會儲存查詢定義。 在上述範例中, 它是執行`For Each`查詢的迴圈。  
  
## <a name="query-execution"></a>查詢執行  
 查詢執行與查詢建立分開。 查詢建立會定義查詢, 但執行是由不同的機制所觸發。 查詢可以在定義 (*立即執行*) 時立即執行, 或可以儲存定義, 而且稍後可以執行查詢 (*延後執行*)。  
  
### <a name="deferred-execution"></a>延後執行  
 一般[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢類似上一個範例`evensQuery`中所定義的查詢。 它會建立查詢, 但不會立即執行。 相反地, 查詢定義會儲存在查詢變數`evensQuery`中。 您稍後會執行查詢, 通常是透過使用`For Each`迴圈來傳回值的序列, 或套用標準查詢運算子 ( `Count`例如或`Max`)。 此程式稱為*延後執行*。  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 針對一連串的值, 您可以使用`For Each`迴圈中的反復專案變數 (`number`在上一個範例中) 來存取抓取的資料。 因為查詢變數`evensQuery`會保存查詢定義, 而不是查詢結果, 所以您可以使用查詢變數多次來執行查詢, 而不需要一次。 例如, 您的應用程式中可能會有另一個應用程式持續更新的資料庫。 建立可從該資料庫抓取資料的查詢之後, 您可以使用`For Each`迴圈來重複執行查詢, 每次都會抓取最新的資料。  
  
 下列範例示範順延強制的運作方式。 在`evensQuery2`定義並`For Each`以迴圈執行之後 (如先前的範例所示), 資料來源`numbers`中的某些元素會變更。 然後再次執行`For Each` `evensQuery2`第二個迴圈。 第二次的結果會不同, 因為`For Each`迴圈會使用中`numbers`的新值, 再次執行查詢。  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 輸出：  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>立即執行  
 在延後執行查詢時, 查詢定義會儲存在查詢變數中, 以供稍後執行。 在立即執行中, 查詢會在其定義時執行。 當您套用需要存取查詢結果之個別元素的方法時, 就會觸發執行。 通常會使用傳回單一值的其中一個標準查詢運算子來強制立即執行。 範例包括`Count`、 `Max`、 `Average`和。`First` 這些標準查詢運算子會在套用查詢時立即執行, 以便計算並傳回單一結果。 如需傳回單一值之標準查詢運算子的詳細資訊, 請參閱[匯總作業](aggregation-operations.md)、[元素作業](element-operations.md)和[數量詞作業](quantifier-operations.md)。  
  
 下列查詢會傳回整數陣列中偶數數目的計數。 不會儲存查詢定義, 而`numEvens`是簡單`Integer`的。  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 您可以使用`Aggregate`方法來達到相同的結果。  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 您也可以在查詢 (立即) 或查詢變數`ToList` ( `ToArray`延後) 上呼叫或方法, 以強制執行查詢, 如下列程式碼所示。  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 在先前的範例中`evensQuery3` , 是查詢變數, 但`evensList`是清單, 而且`evensArray`是陣列。  
  
 當`ToList`您`ToArray`想要立即執行查詢, 並快取單一集合物件中的結果時, 使用或來強制立即執行會特別有用。 如需這些方法的詳細資訊, 請參閱[轉換資料類型](converting-data-types.md)。  
  
 您也可以使用`IEnumerable`方法 (例如<xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>方法) 來執行查詢。  
  
## <a name="see-also"></a>另請參閱

- [使用 Visual Basic 撰寫 LINQ 入門](getting-started-with-linq.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查詢](../../../../visual-basic/language-reference/queries/index.md)
