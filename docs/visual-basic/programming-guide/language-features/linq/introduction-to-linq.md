---
title: "Introduction to LINQ in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [LINQ in Visual Basic], about LINQ in Visual Basic queries"
  - "query execution [LINQ in Visual Basic]"
  - "range variables"
  - "LINQ [Visual Basic]"
  - "LINQ [Visual Basic], about LINQ in Visual Basic"
  - "query expressions [LINQ in Visual Basic]"
  - "LINQ"
  - "deferred execution"
  - "iteration variables"
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# Introduction to LINQ in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Language\-Integrated Query \(LINQ\) 將查詢功能加入 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]，在您使用所有類型的資料時，為您提供簡單而強大的功能。  LINQ 將查詢當成 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 語言的一部分導入，而不是將查詢傳送至資料庫加以處理，或針對您搜尋的各種類型資料，使用不同的查詢語法。  它使用統一的語法，不論資料類型為何。  
  
 LINQ 可讓您從 SQL Server 資料庫、XML、記憶體內部的陣列和集合、[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] 資料集，或任何支援 LINQ 的其他遠端或本機資料來源查詢資料。  使用一般的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 語言項目即可執行上述所有作業。  因為查詢是以 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 語言撰寫而成，所以傳回的查詢結果會是強類型物件。  這些物件支援 IntelliSense，讓您加快撰寫程式碼的速度，並在編譯階段即捕捉查詢中的錯誤，而不是在執行階段。  LINQ 查詢可用做其他查詢來源，以精簡結果。  它們也可以繫結至控制項，讓使用者輕鬆地檢視和修改查詢結果。  
  
 例如，下列程式碼範例顯示的 LINQ 查詢，會從集合中傳回一份客戶清單，並根據位置分組。  
  
 [!code-vb[VbVbalrIntroToLINQ#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_1.vb)]  
  
 在本主題中，您會找到有關下列領域的資訊：  
  
-   [執行範例](#RunningtheExamples)  
  
-   [LINQ 提供者](#LINQProviders)  
  
-   [LINQ 查詢結構](#StructureOfALINQQuery)  
  
-   [Visual Basic LINQ 查詢運算子](#VisualBasicLINQQueryOperators)  
  
-   [使用 LINQ to SQL 連接到資料庫](#ConnectingToADatabase)  
  
-   [支援 LINQ 的 Visual Basic 功能](#VisualBasicFeaturesThatSupportLINQ)  
  
-   [延期與立即執行查詢](#QueryExecution)  
  
-   [Visual Basic 中的 XML](#XMLInVisualBasic)  
  
-   [相關資源](#RelatedResources)  
  
-   [如何和逐步解說主題](#HowToAndWalkthroughTopics)  
  
##  <a name="RunningtheExamples"></a> 執行範例  
 執行簡介和＜LINQ 查詢結構＞一節中的範例，包括下列程式碼，會傳回客戶和訂單清單。  
  
 [!code-vb[VbVbalrIntroToLINQ#31](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_2.vb)]  
  
##  <a name="LINQProviders"></a> LINQ 提供者  
 *「LINQ 提供者」*\(LINQ provider\) 會對應 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] LINQ 查詢和查詢中的資料來源。  當您撰寫 LINQ 查詢時，提供者會接受該查詢，並將它轉譯成資料來源能夠執行的命令。  提供者也會將資料從來源轉換成組成查詢結果的物件。  最後，當您將更新傳送至資料來源時，它會將物件轉換成資料。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 包含下列 LINQ 提供者。  
  
|||  
|-|-|  
|提供者|描述|  
|LINQ to Objects|LINQ to Objects 提供者讓您查詢記憶體內部的集合和陣列。  如果物件支援 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> 介面，LINQ to Objects 提供者就會讓您查詢。<br /><br /> 匯入 <xref:System.Linq> 命名空間就可以啟用 LINQ to Objects 提供者，所有 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 專案都預設匯入。<br /><br /> 如需 LINQ to Objects 提供者的詳細資訊，請參閱 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)。|  
|LINQ to SQL|LINQ to SQL 提供者可讓您查詢及修改 SQL Server 資料庫中的資料。  這可讓您輕鬆對應應用程式的物件模型與資料庫的資料表和物件。<br /><br /> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 納入物件關聯式設計工具 \(O\/R 設計工具\)，讓 LINQ to SQL 更好用。  這個設計工具是用於在對應至資料庫物件的應用程式中建立物件模型。 O\/R 設計工具也提供將預存程序和函式對應至 <xref:System.Data.Linq.DataContext> 物件的功能，它會管理與資料庫的通訊，並且儲存開放式並行存取檢查的狀態。<br /><br /> 如需 LINQ to SQL 提供者的詳細資訊，請參閱 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)。  如需物件關聯式設計工具的詳細資訊，請參閱[物件關聯式設計工具 \(O\/R 設計工具\)](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2)。|  
|LINQ to XML|LINQ to XML 提供者可讓您查詢及修改 XML。  您可以修改記憶體內部的 XML，也可以從檔案載入 XML 並將 XML 儲存到檔案。<br /><br /> 此外，LINQ to XML 提供者也會啟用 XML 常值和 XML 軸屬性，讓您直接在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式碼中撰寫 XML。  如需詳細資訊，請參閱 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)。|  
|LINQ to DataSet|LINQ to DataSet 提供者可讓您查詢及更新 [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] 資料集中的資料。  您可以將 LINQ 的強大功能加入使用資料集的應用程式，以簡化並擴充查詢、彙總及更新資料集資料的能力。<br /><br /> 如需詳細資訊，請參閱 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)。|  
  
##  <a name="StructureOfALINQQuery"></a> LINQ 查詢結構  
 LINQ 查詢，通常稱為*「查詢運算式」*\(query expression\)，由識別查詢之資料來源和反覆運算變數的查詢子句組合而成。  查詢運算式也可以包含排序、篩選、群組和聯結的指示，或套用至來源資料的計算。  查詢運算式語法類似於 SQL 語法，所以您會覺得大部分的語法很熟悉。  
  
 查詢運算式以 `From` 子句開頭。  這個子句會識別查詢和變數的來源資料，這些變數用於分別參考來源資料的每個項目。  這些變數稱為*「範圍變數」*\(range variables\) 或*「反覆運算變數」*\(iteration variables\)。  查詢一定要有 `From` 子句，`Aggregate` 查詢除外，因為 `From` 子句對這類查詢為選擇性項目。  識別出 `From` 或 `Aggregate` 子句中的查詢範圍和來源之後，您可以包含任何查詢子句組合以精簡查詢。  如需查詢子句的詳細資訊，請參閱本主題後文中的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] LINQ 查詢運算子。  例如，下列查詢會將客戶資料的來源集合識別為 `customers` 變數，而反覆運算變數則稱之為 `cust`。  
  
 [!code-vb[VbVbalrIntroToLINQ#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_3.vb)]  
  
 這個範例本身就是個有效的查詢；但是當您加入更多的查詢子句來精簡結果時，查詢就會變得更強大。  例如，您可以加入 `Where` 子句，根據一或多個值來篩選結果。  查詢運算式是單行程式碼，您只可以將其他查詢子句附加至查詢結尾。  您可以使用底線 \(\_\) 行接續字元，將查詢分割成多行文字，以提高可讀性。  下列程式碼範例顯示的查詢範例，包含 `Where` 子句。  
  
 [!code-vb[VbVbalrIntroToLINQ#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_4.vb)]  
  
 另一個功能強大的查詢子句是 `Select` 子句，可讓您只傳回從資料來源選取的欄位。  LINQ 查詢會傳回可列舉的強類型物件集合。  查詢可以傳回匿名類型或具名類型的集合。  您可以使用 `Select` 子句，只傳回資料來源的單一欄位。  當您這麼做時，傳回的集合類型就是該單一欄位的類型。  您也可以使用 `Select` 子句，傳回資料來源的多個欄位。  當您這麼做時，傳回的集合類型就是新的匿名類型。  您也可以比對查詢傳回的欄位和指定的具名類型欄位。  下列程式碼範例顯示傳回匿名類型集合的查詢運算式，該類型具有填入來自資料來源之選取欄位資料的成員。  
  
 [!code-vb[VbVbalrIntroToLINQ#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_5.vb)]  
  
 LINQ 查詢也可以用來結合多個資料來源，並傳回單一結果。  使用一或多個 `From` 子句，或使用 `Join` 或 `Group Join` 查詢子句，即可完成。  下列程式碼範例顯示的查詢運算式，結合了客戶和訂單資料，並傳回包含客戶和訂單資料的匿名類型集合。  
  
 [!code-vb[VbVbalrIntroToLINQ#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_6.vb)]  
  
 您可以使用 `Group Join` 子句建立階層式的查詢結果，其包含客戶物件的集合。  每個客戶物件都有一個屬性，包含該客戶所有訂單的集合。  下列程式碼範例顯示的查詢運算式，結合了階層式結果的客戶和訂單資料，並傳回匿名類型的集合。  查詢傳回的類型包含 `CustomerOrders` 屬性，內含客戶訂單資料的集合。  它也包含 `OrderTotal` 屬性，內含該客戶所有訂單小計的總和。  \(這個查詢相當於 LEFT OUTER JOIN\)。  
  
 [!code-vb[VbVbalrIntroToLINQ#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_7.vb)]  
  
 另有幾個 LINQ 查詢運算子，可讓您建立功能強大的查詢運算式。  本主題的下一節，將討論查詢運算式中可包含的各種查詢子句。  如需 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 查詢子句的詳細資訊，請參閱[Queries](../../../../visual-basic/language-reference/queries/queries.md)。  
  
##  <a name="VisualBasicLINQQueryOperators"></a> Visual Basic LINQ 查詢運算子  
 <xref:System.Linq> 命名空間和其他支援 LINQ 查詢的命名空間中的類別，包含了依應用程式需求建立並精簡查詢的呼叫方法。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 包含最常見的查詢子句關鍵字，如下表所示。  
  
|||  
|-|-|  
|詞彙|定義|  
|[From Clause](../../../../visual-basic/language-reference/queries/from-clause.md)|查詢必須有 `From` 子句或 `Aggregate` 子句才能開始。  `From` 子句會指定查詢的來源集合和反覆運算變數。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#7](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_8.vb)]|  
|[Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md)|選擇項。  宣告一組查詢的反覆運算變數。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#8](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_9.vb)]<br /><br /> 如果不指定 `Select` 子句，則查詢的反覆運算變數即由 `From` 或 `Aggregate` 子句指定的反覆運算變數組成。|  
|[Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md)|選擇項。  指定查詢的篩選條件。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#9](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_10.vb)]|  
|[Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md)|選擇項。  指定查詢的資料行排序。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_11.vb)]|  
|[Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md)|選擇項。  將兩個集合合併成單一集合。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_12.vb)]|  
|[Group By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)|選擇項。  群組查詢結果的項目。  可用來將彙總函式套用至每個群組。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_13.vb)]|  
|[Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md)|選擇項。  將兩個集合合併成單一階層式集合。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_14.vb)]|  
|[Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md)|查詢必須有 `From` 子句或 `Aggregate` 子句才能開始。  `Aggregate` 子句會將一或多個彙總函式套用至集合。  例如，您可以使用 `Aggregate` 子句計算查詢傳回的所有項目小計。<br /><br /> [!code-vb[VbVbalrIntroToLINQ#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_15.vb)]<br /><br /> 也可以使用 `Aggregate` 子句修改查詢。  例如，您可以使用 `Aggregate` 子句執行相關查詢集合的計算。<br /><br /> [!code-vb[VbVbalrIntroToLINQ#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_16.vb)]|  
|[Let Clause](../../../../visual-basic/language-reference/queries/let-clause.md)|選擇項。  計算值，並將它指派給查詢中的新變數。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_17.vb)]|  
|[Distinct Clause](../../../../visual-basic/language-reference/queries/distinct-clause.md)|選擇項。  限制目前反覆運算變數的值，以消除查詢結果中重複的值。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#17](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_18.vb)]|  
|[Skip Clause](../../../../visual-basic/language-reference/queries/skip-clause.md)|選擇項。  略過集合中指定數目的項目，然後傳回其餘項目。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#18](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_19.vb)]|  
|[Skip While Clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md)|選擇項。  只要指定的條件為 `true`，即略過集合中的項目，然後傳回其餘項目。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#19](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_20.vb)]|  
|[Take Clause](../../../../visual-basic/language-reference/queries/take-clause.md)|選擇項。  從集合開頭傳回指定數目的連續項目。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#20](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_21.vb)]|  
|[Take While Clause](../../../../visual-basic/language-reference/queries/take-while-clause.md)|選擇項。  只要指定的條件為 `true`，即包含集合中的項目，並略過其餘項目。  例如:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#21](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_22.vb)]|  
  
 如需 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 查詢子句的詳細資訊，請參閱[Queries](../../../../visual-basic/language-reference/queries/queries.md)。  
  
 透過呼叫 LINQ 提供的可列舉和可查詢類型的成員，您可以使用其他的 LINQ 查詢功能。  透過呼叫查詢運算式結果上的特定查詢運算子，您可以使用這些額外的功能。  例如，下列程式碼範例使用 <xref:System.Linq.Enumerable.Union%2A> 方法，將兩個查詢結果合併成一個查詢結果。  它使用 <xref:System.Linq.Enumerable.ToList%2A> 方法傳回泛型清單的查詢結果。  
  
 [!code-vb[VbVbalrIntroToLINQ#22](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_23.vb)]  
  
 如需其他 LINQ 功能的詳細資訊，請參閱[Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
##  <a name="ConnectingToADatabase"></a> 使用 LINQ to SQL 連接到資料庫  
 在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中，您使用 LINQ to SQL 檔案識別要存取的 SQL Server 資料庫物件，例如資料表、檢視和預存程序。  LINQ to SQL 檔案的副檔名為 .dbml。  
  
 當您有 SQL Server 資料庫的有效連接時，可以將 \[LINQ to SQL 類別\] 項目範本加入專案。  這會顯示物件關聯式設計工具 \(O\/R 設計工具\)。  O\/R 設計工具可讓您將想要存取的程式碼項目，從 \[伺服器總管\]\/\[資料庫總管\] 拖曳至設計工具介面上。  LINQ to SQL 檔案將 <xref:System.Data.Linq.DataContext> 物件加入專案。  此物件包含您想要存取的資料表和檢視的屬性和集合，以及您想要呼叫的預存程序方法。  將變更儲存至 LINQ to SQL \(.dbml\) 檔案之後，參考 O\/R 設計工具所定義的 <xref:System.Data.Linq.DataContext> 物件，您就可以存取程式碼中的這些物件。  專案的 <xref:System.Data.Linq.DataContext> 物件依據您的 LINQ to SQL 檔案名稱來命名。  例如，名為 Northwind.dbml 的 LINQ to SQL 檔案，會建立名為 `NorthwindDataContext` 的 <xref:System.Data.Linq.DataContext> 物件。  
  
 如需逐步指示的範例，請參閱 [How to: Query a Database](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md)和[How to: Call a Stored Procedure](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md)。  
  
##  <a name="VisualBasicFeaturesThatSupportLINQ"></a> 支援 LINQ 的 Visual Basic 功能  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 包含其他值得注意的功能，讓 LINQ 簡單易用，並減少為執行 LINQ 查詢所必須撰寫的程式碼數量。  這些需求包括下列各項：  
  
-   **匿名類型**：可讓您根據查詢結果建立新的類型。  
  
-   **隱含類型變數**：可讓您延後指定類型，並讓編譯器根據查詢結果推斷類型。  
  
-   **擴充方法**：可讓您以自己的方法擴充現有的類型，卻不修改類型本身。  
  
 如需詳細資訊，請參閱[Visual Basic Features That Support LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md)。  
  
##  <a name="QueryExecution"></a> 延期與立即執行查詢  
 查詢執行會與建立查詢分開。  查詢建立之後，會另有機制觸發執行。  查詢一經定義便可執行 \(*「立即執行」*\(immediate execution\)\)，或者儲存定義以待稍後執行查詢 \(*延後執行*\(deferred execution\)\)。  
  
 當您建立查詢時，查詢本身預設不會立即執行。  反而會將查詢定義儲存在變數中，用以參考查詢結果。  稍後存取程式碼中的查詢結果變數時，例如在 `For…Next` 迴圈中，就會執行查詢。  這個程序稱之為*「延後執行」*\(deferred execution\)。  
  
 查詢也可以在定義當時執行，這稱之為*「立即執行」*\(immediate execution\)。  套用要求存取查詢結果個別項目的方法，可觸發立即執行。  這個結果可能會包括彙總函式，例如 `Count`、`Sum`、`Average`、`Min` 或 `Max`。  如需彙總函式的詳細資訊，請參閱 [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 使用 `ToList` 或 `ToArray` 方法也會強制立即執行。  當您想要立即執行查詢並快取結果時，這方法非常好用。  如需這些方法的詳細資訊，請參閱[Converting Data Types](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)。  
  
 如需查詢執行的詳細資訊，請參閱 [撰寫第一個 LINQ 查詢](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
##  <a name="XMLInVisualBasic"></a> Visual Basic 中的 XML  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的 XML 功能包括 XML 常值和 XML 軸屬性，讓您輕鬆建立、存取、查詢及修改程式碼中的 XML。  XML 常值可讓您直接在程式碼中撰寫 XML。  Visual Basic 編譯器將 XML 視為第一級的資料物件。  
  
 下列程式碼範例示範如何建立 XML 項目、存取其子項目和屬性，以及使用 LINQ 查詢項目內容。  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/introduction-to-linq_24.vb)]  
  
 如需詳細資訊，請參閱 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)。  
  
##  <a name="RelatedResources"></a> 相關資源  
  
|||  
|-|-|  
|主題|描述|  
|[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)|說明 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中可查詢的 XML 功能，它們還可讓您在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式碼中將 XML 當做第一級資料物件納入。|  
|[Queries](../../../../visual-basic/language-reference/queries/queries.md)|提供 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的查詢子句參考資訊。|  
|[LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)|包含 LINQ 的一般資訊、程式設計指南和範例。|  
|[LINQ to SQL](../Topic/LINQ%20to%20SQL.md)|包含 LINQ to SQL 的一般資訊、程式設計指南和範例。|  
|[LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)|包含 LINQ to Objects 的一般資訊、程式設計指南和範例。|  
|[LINQ to ADO.NET](../Topic/LINQ%20to%20ADO.NET%20\(Portal%20Page\)1.md)|包含 LINQ to [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] 的一般資訊、程式設計指南和範例連結。|  
|[LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)|包含 LINQ to XML 的一般資訊、程式設計指南和範例。|  
  
##  <a name="HowToAndWalkthroughTopics"></a> 如何和逐步解說主題  
 [How to: Query a Database](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md)  
  
 [How to: Call a Stored Procedure](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [How to: Modify Data in a Database](../../../../visual-basic/programming-guide/language-features/linq/how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [How to: Combine Data with Joins](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)  
  
 [How to: Sort Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
  
 [How to: Filter Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
  
 [How to: Count, Sum, or Average Data](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [How to: Find the Minimum or Maximum Value in a Query Result](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)  
  
 [HOW TO：指派預存程序來執行更新、插入和刪除 \(O\/R 設計工具\)](../Topic/How%20to:%20Assign%20stored%20procedures%20to%20perform%20updates,%20inserts,%20and%20deletes%20\(O-R%20Designer\).md)  
  
## 精選書籍章節  
 [Visual Basic 2008 程式設計](http://go.microsoft.com/fwlink/?LinkId=195383) [第 17 章：LINQ](http://go.microsoft.com/fwlink/?LinkId=195277)  
  
## 請參閱  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)   
 [LINQ to DataSet 概觀](../Topic/LINQ%20to%20DataSet%20Overview.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [LINQ 範例](../Topic/LINQ%20Samples.md)   
 [物件關聯式設計工具 \(O\/R 設計工具\)](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2)   
 [DataContext 方法 \(O\/R 設計工具\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)