---
title: 撰寫第一個 LINQ 查詢
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: c7d0595b991bdad6ef05b567f95ead8c7fccdbc2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077276"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>撰寫第一個 LINQ 查詢 (Visual Basic)

「查詢」** 是指從資料來源中擷取資料的運算式。 查詢是以專用的查詢語言來表示。 經過一段時間之後，就會針對不同類型的資料來源開發不同的語言，例如，適用于關係資料庫的 SQL 和適用于 XML 的 XQuery。 這讓應用程式開發人員必須針對每一種支援的資料來源或資料格式，學習新的查詢語言。  
  
 語言整合式查詢 (LINQ) 藉由提供一致的模型來處理各種資料來源和格式的資料，藉此簡化這種情況。 在 LINQ 查詢中，您永遠都是使用物件。 您可以使用相同的基本程式碼撰寫模式來查詢及轉換 XML 檔、SQL 資料庫、ADO.NET 資料集和實體 .NET Framework 集合，以及可使用 LINQ 提供者的任何其他來源或格式的資料。 本檔說明建立和使用基本 LINQ 查詢的三個階段。  
  
## <a name="three-stages-of-a-query-operation"></a>查詢作業的三個階段  

 LINQ 查詢作業包含三個動作：  
  
1. 取得資料來源或來源。  
  
2. 建立查詢。  
  
3. 執行查詢。  
  
 在 LINQ 中，查詢的執行與查詢的建立方式不同。 您只需建立查詢就能取出任何資料。 本主題稍後會詳細討論這一點。  
  
 下列範例說明查詢作業的三個部分。 此範例使用整數陣列作為示範用途的方便資料來源。 但是，相同的概念也適用于其他資料來源。  
  
> [!NOTE]
> 在 [ [編譯] 頁面上， (Visual Basic) 的 [專案設計 ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)工具]，確定 [ **選項推斷** ] 設定為 [ **開啟**]。  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 輸出：  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>資料來源  

 因為上一個範例中的資料來源是陣列，所以它會隱含地支援泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面。 這是可讓您使用陣列作為 LINQ 查詢資料來源的事實。 支援 <xref:System.Collections.Generic.IEnumerable%601> 或衍生介面的類型，例如泛型 <xref:System.Linq.IQueryable%601> 稱為*可查詢的類型*。  
  
 陣列是一種隱含可查詢的類型，不需要修改或特殊處理以做為 LINQ 資料來源。 這也適用于任何支援的集合類型 <xref:System.Collections.Generic.IEnumerable%601> ，包括泛型 <xref:System.Collections.Generic.List%601> 、 <xref:System.Collections.Generic.Dictionary%602> 和 .NET Framework 類別庫中的其他類別。  
  
 如果來源資料尚未執行 <xref:System.Collections.Generic.IEnumerable%601> ，則需要 LINQ 提供者來為該資料來源執行 *標準查詢運算子* 的功能。 例如，會 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 處理將 XML 檔載入可查詢型別的工作 <xref:System.Xml.Linq.XElement> ，如下列範例所示。 如需標準查詢運算子的詳細資訊，請參閱 [標準查詢運算子總覽 (Visual Basic) ](standard-query-operators-overview.md)。  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 在中 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ，您會先在設計階段建立物件關聯式對應，不論是手動或使用 Visual Studio 中 [Visual Studio 的 LINQ to SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) 。 您可以針對物件撰寫查詢，而 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 則會在執行階段處理與資料庫之間的通訊。 在下列範例中， `customers` 代表資料庫中的特定資料表，並 <xref:System.Data.Linq.Table%601> 支援 generic <xref:System.Linq.IQueryable%601> 。  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 如需有關如何建立特定資料來源類型的詳細資訊，請參閱各種 LINQ 提供者的檔。  (如需這些提供者的清單，請參閱 [LINQ (語言整合式查詢) ](index.md)。 ) 基本規則很簡單： LINQ 資料來源是支援泛型介面的任何物件 <xref:System.Collections.Generic.IEnumerable%601> ，或繼承自它的介面。  
  
> [!NOTE]
> <xref:System.Collections.ArrayList>支援非泛型介面的類型 <xref:System.Collections.IEnumerable> 也可以當做 LINQ 資料來源使用。 如需使用的範例 <xref:System.Collections.ArrayList> ，請參閱 how [to：使用 LINQ 查詢 ArrayList (Visual Basic) ](how-to-query-an-arraylist-with-linq.md)。  
  
## <a name="the-query"></a>查詢  

 在查詢中，您會指定要從資料來源或來源取得哪些資訊。 您也可以選擇指定應該如何排序、分組或結構化資訊，再傳回該資訊。 為了啟用查詢建立，Visual Basic 已將新的查詢語法併入語言中。  
  
 執行時，下列範例中的查詢會傳回整數陣列中的所有偶數（偶數） `numbers` 。  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 查詢運算式包含三個子句： `From` 、 `Where` 和 `Select` 。 [ (Visual Basic) 的基本查詢作業](basic-query-operations.md)中，會討論每個查詢運算式子句的特定函數和用途。 如需詳細資訊，請參閱 [查詢](../../../language-reference/queries/index.md)。 請注意，在 LINQ 中，查詢定義通常會儲存在變數中並在稍後執行。 查詢變數（如 `evensQuery` 上述範例所示）必須是可查詢的型別。 的類型 `evensQuery` 是 `IEnumerable(Of Integer)` 由編譯器使用區欄位型別推斷所指派。  
  
 請務必記住，查詢變數本身不會採取任何動作，也不會傳回任何資料。 它只會儲存查詢定義。 在上述範例中，這是 `For Each` 執行查詢的迴圈。  
  
## <a name="query-execution"></a>查詢執行  

 查詢執行與查詢建立不同。 建立查詢會定義查詢，但會以不同的機制觸發執行。 只要查詢定義 (*立即執行*) ，就可以執行查詢，或者可以儲存定義，然後在稍後 (*延後執行*) 執行查詢。  
  
### <a name="deferred-execution"></a>延後執行  

 一般 LINQ 查詢類似于上一個範例中定義的查詢 `evensQuery` 。 它會建立查詢，但不會立即執行。 相反地，查詢定義會儲存在查詢變數中 `evensQuery` 。 您稍後會執行查詢，通常是使用 `For Each` 迴圈傳回值的序列，或套用標準的查詢運算子（例如 `Count` 或） `Max` 。 此進程稱為 *延後執行*。  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 針對一系列的值，您可以使用 `For Each` `number` 上一個範例)  (迴圈中的反覆運算變數來存取取出的資料。 因為查詢變數（ `evensQuery` ）會保留查詢定義，而不是查詢結果，所以您可以使用查詢變數多次執行查詢。 例如，您的應用程式中可能會有另一個應用程式持續更新的資料庫。 在您建立從該資料庫抓取資料的查詢之後，您可以使用 `For Each` 迴圈來重複執行查詢，每次都會抓取最新的資料。  
  
 下列範例將示範延後執行的運作方式。 `evensQuery2`使用迴圈來定義和執行之後（ `For Each` 如先前的範例所示），資料來源中的某些元素 `numbers` 會變更。 然後再次執行第二個 `For Each` 迴圈 `evensQuery2` 。 第二次的結果會不同，因為 `For Each` 迴圈會使用中的新值，再次執行查詢 `numbers` 。  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 輸出：  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>立即執行  

 在順延強制查詢時，查詢定義會儲存在查詢變數中，以便稍後執行。 在立即執行時，會在其定義時執行查詢。 當您套用需要存取查詢結果之個別元素的方法時，就會觸發執行。 通常會使用其中一個會傳回單一值的標準查詢運算子來強制執行立即執行。 範例包括 `Count` 、 `Max` 、 `Average` 和 `First` 。 這些標準查詢運算子會在套用查詢時立即執行查詢，以便計算並傳回單一結果。 如需傳回單一值之標準查詢運算子的詳細資訊，請參閱 [匯總作業](aggregation-operations.md)、 [元素作業](element-operations.md)和 [數量詞作業](quantifier-operations.md)。  
  
 下列查詢會傳回整數陣列中偶數數目的計數。 查詢定義不會儲存，而且 `numEvens` 很簡單 `Integer` 。  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 您可以使用方法來達到相同的結果 `Aggregate` 。  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 您也可以 `ToList` 在查詢上呼叫或方法來強制執行查詢 `ToArray` (立即) 或查詢變數 (延後) ，如下列程式碼所示。  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 在上述範例中， `evensQuery3` 是查詢變數，但是 `evensList` 清單，而且 `evensArray` 是陣列。  
  
 `ToList` `ToArray` 在您想要立即執行查詢，並將結果快取在單一集合物件中時，使用或強制立即執行會特別有用。 如需這些方法的詳細資訊，請參閱 [轉換資料類型](converting-data-types.md)。  
  
 您也可以使用方法（例如方法）來執行查詢 `IEnumerable` <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> 。  
  
## <a name="see-also"></a>另請參閱

- [使用 Visual Basic 撰寫 LINQ 入門](getting-started-with-linq.md)
- [區域型別推斷](../../language-features/variables/local-type-inference.md)
- [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)
- [Visual Basic 中的 LINQ 簡介](../../language-features/linq/introduction-to-linq.md)
- [LINQ](../../language-features/linq/index.md)
- [查詢](../../../language-reference/queries/index.md)
