---
title: "撰寫第一個 LINQ 查詢 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "查詢 [Visual Basic 中的 LINQ]，撰寫"
  - "LINQ 查詢 [Visual Basic]"
  - "LINQ [Visual Basic]，撰寫查詢"
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: 56
caps.handback.revision: 54
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 撰寫第一個 LINQ 查詢 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

「*查詢*」\(Query\) 是一種從資料來源擷取資料的運算式，  而且使用專用的查詢語言來表示。  隨著時間演進，業界已針對不同類型的資料來源開發出不同語言，例如，關聯式資料庫的 SQL 以及 XML 的 XQuery。  因此，應用程式開發人員需要針對每種支援的資料來源類型或資料格式學習新的查詢語言。  
  
 [!INCLUDE[vbteclinqext](../../../../csharp/programming-guide/concepts/linq/includes/vbteclinqext_md.md)] 提供一致的模型來使用各種資料來源和格式的資料，從而簡化了上述情況。  在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢中，您所處理的一定是物件。  不論您要查詢及轉換的資料是存在 XML 文件、SQL 資料庫、ADO.NET 資料集和實體 \(Entity\)，還是 .NET Framework 集合，以及其他任何有可用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 提供者 \(Provider\) 的來源或格式中，都是使用相同的基本程式碼撰寫模式。  本文件說明建立及使用基本 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢的三個階段。  
  
 ![視訊的連結](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") 如需相關示範影片，請參閱[如何：開始使用 LINQ？](http://go.microsoft.com/fwlink/?LinkId=133021) \(英文\)。  
  
## 查詢作業的三個階段  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢作業包含三個動作：  
  
1.  取得一個或多個資料來源。  
  
2.  建立查詢。  
  
3.  執行查詢。  
  
 在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 中，查詢的執行與建立是分開的。  單純建立查詢時，並不會擷取任何資料。  本主題稍後會詳細討論這一點。  
  
 下列範例說明查詢作業的三個部分。  為了便於示範，這個範例會使用整數陣列做為快速方便的資料來源。  不過，相同的概念也適用於其他資料來源。  
  
> [!NOTE]
>  在 [專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)中，確定 \[**Option Infer**\] 設定為 \[**在**\]。  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 輸出：  
  
 `0 2 4 6`  
  
## 資料來源  
 因為上一個範例的資料來源是陣列，所以這個範例隱含地支援泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面。  這便是可以使用陣列做為 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢資料來源的原因。  支援 <xref:System.Collections.Generic.IEnumerable%601> 或衍生的介面 \(例如泛型 <xref:System.Linq.IQueryable%601> 的型別都 *稱為可查詢型別*。  
  
 陣列是一種隱含的可查詢型別，不需要進行修改或特殊處理，就可以當成 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 資料來源使用。  這也適用於支援 <xref:System.Collections.Generic.IEnumerable%601>，包括泛型 <xref:System.Collections.Generic.List%601>， <xref:System.Collections.Generic.Dictionary%602>的任何集合型別和其他類別在 .NET Framework 類別庫中。  
  
 如果資料來源沒有實作 <xref:System.Collections.Generic.IEnumerable%601>， [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 提供者需要實作 *標準查詢運算子的* 功能該資料來源的。  例如，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 會處理將 XML 文件載入至可查詢 <xref:System.Xml.Linq.XElement> 型別的工作，如下列範例所示。  如需標準查詢運算子的詳細資訊，請參閱[Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 使用 [!INCLUDE[vbtecdlinq](../../../../csharp/language-reference/keywords/includes/vbtecdlinq_md.md)] 時，請先在設計階段利用手動方式或[物件關聯式設計工具 \(O\/R 設計工具\)](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2)，建立物件關聯對應。  您可以針對物件撰寫查詢，而 [!INCLUDE[vbtecdlinq](../../../../csharp/language-reference/keywords/includes/vbtecdlinq_md.md)] 則會在執行階段處理與資料庫之間的通訊。  在下列範例中，`customers` 表示資料庫中的特定資料表，而 <xref:System.Data.Linq.Table%601> 則支援泛型 <xref:System.Linq.IQueryable%601>。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 如需如何建立特定資料來源類型的詳細資訊，請參閱各種 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 提供者的文件。  \(如需這些提供者的清單，請參閱 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)\)。基本規則十分簡單：[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 資料來源可以是任何支援泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面或繼承它之介面的物件。  
  
> [!NOTE]
>  諸如 <xref:System.Collections.ArrayList> 等支援非泛型 <xref:System.Collections.IEnumerable> 介面的型別，也可以當成 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 資料來源使用。  如需使用 <xref:System.Collections.ArrayList> 的範例，請參閱 [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)。  
  
## 查詢  
 在查詢中，可以指定想要從資料來源擷取的資訊。  也可以選擇指定該資訊在傳回之前的排序、分組或結構方式。  為了能夠建立查詢，Visual Basic 在語言中併入了新的查詢語法。  
  
 下列範例中的查詢在執行時會傳回整數陣列 `numbers` 中的所有偶數。  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 查詢運算式包含三個子句：`From`、`Where` 和 `Select`。  [基本查詢作業 \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) 中會討論這些查詢運算式子句的特定功能和用途。  如需詳細資訊，請參閱[Queries](../../../../visual-basic/language-reference/queries/queries.md)。  請注意，在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 中，查詢定義通常會儲存在變數中，等稍後再執行。  查詢變數 \(例如，在上述範例中， `evensQuery` 必須是可查詢的型別。`evensQuery` 的型別是 `IEnumerable(Of Integer)`，會使用區域型別推斷的編譯器中指定。  
  
 重要的是要記住，查詢變數本身並不會採取任何動作，也不會傳回任何資料，  它只會儲存查詢定義。  在上一個範例中，負責執行查詢的是 `For Each` 迴圈 \(Loop\)。  
  
## 查詢執行  
 查詢執行與查詢建立是分開的。  查詢建立會定義查詢，但是執行則是由不同的機制所觸發 \(Trigger\)。  查詢可以在定義之後馬上執行 \(「*立即執行*」\(Immediate Execution\)\)，或者先儲存好定義再於稍後執行 \(「*延後執行*」\(Deferred Execution\)\)。  
  
### 延後執行  
 典型的 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢與上一個範例中的查詢類似，而上一個範例中定義了 `evensQuery`。  它會建立查詢，但是不會立即執行。  相反地，它會將查詢定義儲存在查詢變數 `evensQuery` 中。  稍後您會再執行查詢，方法通常是使用會傳回一系列值的 `For Each` 迴圈，或是套用 `Count` 或 `Max` 等標準查詢運算子。  這個程序稱為「*延後執行*」\(Deferred Execution\)。  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 如果有一系列值，則可以在 `For Each` 迴圈中使用反覆運算變數 \(在上一個範例中是 `number`\) 來存取擷取到的資料。  因為查詢變數 `evensQuery` 保存的是查詢定義，而不是查詢結果，所以您可以隨心所欲地多次使用查詢變數來執行查詢。  例如，有另一個應用程式會持續更新您應用程式中的資料庫。  建立從該資料庫擷取資料的查詢之後，您就可以使用 `For Each` 迴圈重複執行查詢，每次都擷取最新的資料。  
  
 下列範例示範延後執行的運作方式。  在定義 `evensQuery2` 並使用 `For Each` 迴圈加以執行之後 \(如上面範例所示\)，資料來源 `numbers` 中的部分項目有所變更。  於是又再次使用一個 `For Each` 迴圈執行 `evensQuery2`。  第二次的結果會不同，原因是再次執行查詢的 `For Each` 迴圈使用的是 `numbers` 中的新值。  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 輸出：  
  
 `Evens in original array:`  
  
 `0 2 4 6`  
  
 `Evens in changed array:`  
  
 `0 10 2 22 8`  
  
### 立即執行  
 在查詢的延後執行中，查詢定義會儲存在查詢變數中供稍後執行。  在立即執行中，查詢會在定義時馬上執行。  當您所套用的方法需要存取查詢結果中的個別項目時，就會觸發執行。  立即執行通常是透過一個會傳回單一值的標準查詢運算子強制執行，  例如 `Count`、`Max`、`Average` 和 `First`。  這些標準查詢運算子會在套用時馬上執行查詢，以計算並傳回單一結果。  如需會傳回單一值之標準查詢運算子的詳細資訊，請參閱[Aggregation Operations](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)、[Element Operations](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)和[Quantifier Operations](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)。  
  
 下列查詢會傳回整數陣列中的偶數計數。  但不會儲存查詢定義，而 `numEvens` 是簡單 `Integer`。  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 使用 `Aggregate` 方法可以達成相同的結果。  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 您也可以在查詢 \(立即\) 或查詢變數 \(延後\) 上呼叫 `ToList` 或 `ToArray` 方法來強制執行查詢 \(如下列程式碼所示\)。  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 在前述範例中，`evensQuery3` 是查詢變數，而 `evensList` 是清單，`evensArray` 是陣列。  
  
 如果想要立即執行查詢，並將結果快取至單一集合物件中，則使用 `ToList` 或 `ToArray` 強制立即執行特別有用。  如需這些方法的詳細資訊，請參閱[Converting Data Types](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)。  
  
 您也可以使用諸如 <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> 方法等 `IEnumerable` 方法來執行查詢。  
  
## 相關示範影片  
 [如何開始使用 LINQ？](http://go.microsoft.com/fwlink/?LinkId=133021)  
  
 [影片 HOW TO：在 Visual Basic 中撰寫查詢](http://go.microsoft.com/fwlink/?LinkID=100356)  
  
## 請參閱  
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ 範例](../Topic/LINQ%20Samples.md)   
 [O\/R 設計工具概觀](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)