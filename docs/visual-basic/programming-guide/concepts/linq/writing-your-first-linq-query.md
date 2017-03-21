---
title: "撰寫第一個 LINQ 查詢 (Visual Basic) |Microsoft 文件"
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
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: 56
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 48f1c5e15654580b6e4d060860a0d7001af5e2ef
ms.lasthandoff: 03/13/2017

---
# <a name="writing-your-first-linq-query-visual-basic"></a>撰寫第一個 LINQ 查詢 (Visual Basic)
A*查詢*是從資料來源擷取資料的運算式。 查詢是以專用的查詢語言來表示。 經過一段時間，不同語言所開發的不同類型的資料來源，例如 SQL 用於關聯式資料庫，而 XQuery 用於 XML。 這可讓您所需的應用程式開發人員若要了解每種類型的資料來源或資料格式，支援新的查詢語言。  
  
 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]藉由提供一致的模型，可處理各種資料來源和格式的簡化這種情況。 在[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢中，您一律處理的物件。 您可以使用相同的基本程式碼撰寫模式查詢及轉換 XML 文件中的資料、 SQL 資料庫、 ADO.NET 資料集和實體、.NET Framework 集合和任何其他來源或格式的[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]提供者的。 本文件說明的三個階段的建立和使用 basic[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢。  
  
## <a name="three-stages-of-a-query-operation"></a>查詢作業的三個階段  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢作業包含三個動作︰  
  
1.  取得資料來源。  
  
2.  建立查詢。  
  
3.  執行查詢。  
  
 在[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]，查詢的執行是不同的查詢建立。 您不只是藉由建立查詢擷取任何資料。 本主題稍後詳細討論這點。  
  
 下列範例說明查詢作業的三個部分。 基於示範目的，範例會使用整數的陣列做為方便存取的資料來源。 不過，相同的概念也適用於其他資料來源。  
  
> [!NOTE]
>  在[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，請確認**Option infer**設為**上**。  
  
 [!code-vb[VbLINQFirstQuery #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 輸出：  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>資料來源  
 在上述範例中的資料來源是一個陣列，因為隱含支援泛型<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601> 這項事實，可讓您使用陣列做為資料來源是[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢。 型別支援<xref:System.Collections.Generic.IEnumerable%601>或衍生的介面，例如泛型<xref:System.Linq.IQueryable%601>稱為*可查詢型別*。</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
 做為隱含的可查詢類型的陣列，不需要修改或特殊處理，做為[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]資料來源。 這也適用於任何支援的集合型別<xref:System.Collections.Generic.IEnumerable%601>，包括泛型<xref:System.Collections.Generic.List%601>， <xref:System.Collections.Generic.Dictionary%602>，與其他.NET Framework 類別庫中的類別。</xref:System.Collections.Generic.Dictionary%602> </xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
 如果來源資料已經實作<xref:System.Collections.Generic.IEnumerable%601>、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]實作的功能所需的提供者*標準查詢運算子*針對該資料來源。</xref:System.Collections.Generic.IEnumerable%601> 例如，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]會處理 XML 文件載入可查詢的工作<xref:System.Xml.Linq.XElement>類型，如下列範例所示。</xref:System.Xml.Linq.XElement> 如需標準查詢運算子的詳細資訊，請參閱[標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)。  
  
 [!code-vb[VbLINQFirstQuery #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 使用[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]，您必須先建立物件關聯式對應在設計階段，以手動方式或使用[LINQ to SQL 工具，在 Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) Visual Studio 中。 撰寫您的查詢物件，並在執行階段[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]處理與資料庫通訊。 在下列範例中，`customers`代表資料庫和<xref:System.Data.Linq.Table%601>支援泛型<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></xref:System.Data.Linq.Table%601>中的特定資料表  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 如需如何建立特定類型的資料來源的詳細資訊，請參閱文件的各種[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]提供者。 (如需這些提供者的清單，請參閱[LINQ （語言整合式查詢）](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)。)基本規則很簡單︰[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]資料來源是支援的泛型<xref:System.Collections.Generic.IEnumerable%601>介面或介面繼承自它</xref:System.Collections.Generic.IEnumerable%601>的任何物件  
  
> [!NOTE]
>  型別，例如<xref:System.Collections.ArrayList>支援非泛型<xref:System.Collections.IEnumerable>介面也可用來當做[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]資料來源。</xref:System.Collections.IEnumerable> </xref:System.Collections.ArrayList> 如需範例，會使用<xref:System.Collections.ArrayList>，請參閱[How to︰ 使用 LINQ (Visual Basic) 查詢 ArrayList](how-to-query-an-arraylist-with-linq.md)。</xref:System.Collections.ArrayList>  
  
## <a name="the-query"></a>查詢  
 在查詢中，您可以指定您想要從來源或資料來源中擷取的資訊。 您也可以指定如何這項資訊應該排序、 分組，或結構會在傳回之前的選擇。 若要啟用查詢建立，Visual Basic 已併入新的查詢語法的語言。  
  
 下列範例中的查詢執行時，會傳回偶數整數陣列中，從`numbers`。  
  
 [!code-vb[VbLINQFirstQuery #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 查詢運算式中包含三個子句︰ `From`， `Where`，和`Select`。 討論的特定函式和每個查詢運算式子句的目的[基本查詢作業 (Visual Basic)](basic-query-operations.md)。 如需詳細資訊，請參閱[查詢](../../../../visual-basic/language-reference/queries/queries.md)。 請注意，在[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]，查詢定義通常儲存在變數，並稍後執行。 查詢變數，例如`evensQuery`在上述範例中，必須是可查詢型別。 型別`evensQuery`是`IEnumerable(Of Integer)`、 指派的編譯器使用區域型別推斷。  
  
 請務必記得，查詢變數本身會採取任何動作，並不傳回任何資料。 它只會儲存查詢定義。 在上述範例中，它是`For Each`迴圈執行查詢。  
  
## <a name="query-execution"></a>查詢執行  
 查詢執行會從查詢建立分開的。 查詢建立定義查詢，但執行由不同的機制所觸發。 可以執行查詢，因為它定義 (*立即執行*)，或定義可以儲存和更新版本才能執行查詢 (*延後執行*)。  
  
### <a name="deferred-execution"></a>延後執行  
 一般[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢類似在前一個範例中，在其中一個`evensQuery`定義。 它會建立查詢，但不會立即執行它。 相反地，在查詢變數中儲存查詢定義`evensQuery`。 在執行查詢之後，通常藉由使用`For Each`迴圈，而傳回序列的值，或藉由套用標準查詢運算子，例如`Count`或`Max`。 此程序稱為*延後執行*。  
  
 [!code-vb[VbLINQFirstQuery #&7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 序列的值，您必須存取擷取的資料使用中的反覆運算變數`For Each`迴圈 (`number`前一個範例中)。 因為查詢變數`evensQuery`，保留查詢定義，而不是查詢結果中，您可以依照您想使用一次以上的查詢變數的頻率來執行查詢。 例如，您可能必須將資料庫由個別的應用程式持續更新的應用程式中。 建立從資料庫中擷取資料的查詢之後，您可以使用`For Each`擷取最新的資料每次迴圈重複執行查詢。  
  
 下列範例示範延後的執行如何運作。 之後`evensQuery2`定義，並以執行`For Each`如同上述範例中，迴圈中的資料來源的某些元素`numbers`會變更。 然後第二個`For Each`迴圈執行`evensQuery2`一次。 結果就不同第二次，因為`For Each`迴圈會執行查詢，使用中的新值`numbers`。  
  
 [!code-vb[VbLINQFirstQuery #&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 輸出：  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>立即執行  
 在延後執行查詢時，查詢定義會儲存在查詢變數中供稍後執行。 在立即執行，其定義時執行查詢。 當您將需要存取個別的項目查詢結果的方法套用，便會觸發執行。 立即執行通常會強制使用其中一個標準查詢運算子會傳回單一值。 Examples are `Count`, `Max`, `Average`, and `First`. 這些標準查詢運算子會執行查詢，因為它們會套用以計算並傳回單一結果。 如需傳回單一值的標準查詢運算子的詳細資訊，請參閱[彙總作業](aggregation-operations.md)，[項目作業](element-operations.md)，和[數量詞作業](quantifier-operations.md)。  
  
 下列查詢會傳回偶數計數的整數陣列中。 不會儲存查詢定義，以及`numEvens`是簡單`Integer`。  
  
 [!code-vb[VbLINQFirstQuery #&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 您可以使用，以達到相同的結果`Aggregate`方法。  
  
 [!code-vb[VbLINQFirstQuery #&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 您也可以強制執行查詢，藉由呼叫`ToList`或`ToArray`（即時） 的查詢或查詢變數 （延遲），如下列程式碼所示的方法。  
  
 [!code-vb[VbLINQFirstQuery #&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 在上一個範例中，`evensQuery3`是查詢變數，但`evensList`是清單和`evensArray`是陣列。  
  
 使用`ToList`或`ToArray`來強制立即執行是您要立即執行查詢，並快取單一集合物件中的結果的情況下特別有用。 如需有關這些方法的詳細資訊，請參閱[轉換資料型別](converting-data-types.md)。  
  
 您也可能會導致執行查詢，以使用`IEnumerable`方法，例如<xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>方法。</xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中撰寫 LINQ 入門](getting-started-with-linq.md)   
 [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)   
 [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)
