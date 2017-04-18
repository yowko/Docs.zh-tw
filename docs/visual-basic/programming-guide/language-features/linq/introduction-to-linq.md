---
title: "在 Visual Basic 中的 LINQ 簡介 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], about LINQ in Visual Basic queries
- query execution [LINQ in Visual Basic]
- range variables
- LINQ [Visual Basic]
- LINQ [Visual Basic], about LINQ in Visual Basic
- query expressions [LINQ in Visual Basic]
- LINQ
- deferred execution
- iteration variables
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e1343b06089df63beb73cbb27a38de396f5cb6c8
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-linq-in-visual-basic"></a>Visual Basic 中的 LINQ 簡介
Language-Integrated Query (LINQ) 將查詢功能加入 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，在您使用所有類型的資料時，為您提供簡單而強大的功能。 LINQ 將查詢當成 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 語言的一部分導入，而不是將查詢傳送至資料庫加以處理，或針對您搜尋的各種類型資料，使用不同的查詢語法。 它使用統一的語法，不論資料類型為何。  
  
 LINQ 可讓您查詢的資料從 SQL Server 資料庫、 XML、 記憶體中陣列和集合，[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]資料集或任何其他遠端或本機資料來源支援 LINQ。 使用一般的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 語言項目即可執行上述所有作業。 因為查詢是以 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 語言撰寫而成，所以傳回的查詢結果會是強類型物件。 這些物件支援 IntelliSense，讓您加快撰寫程式碼的速度，並在編譯階段即捕捉查詢中的錯誤，而不是在執行階段。 LINQ 查詢可用做其他查詢來源，以精簡結果。 它們也可以繫結至控制項，讓使用者輕鬆地檢視和修改查詢結果。  
  
 例如，下列程式碼範例顯示的 LINQ 查詢，會從集合中傳回一份客戶清單，並根據位置分組。  
  
 [!code-vb[VbVbalrIntroToLINQ #&1;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
 在本主題中，您會找到有關下列領域的資訊：  
  
-   [執行範例](#RunningtheExamples)  
  
-   [LINQ 提供者](#LINQProviders)  
  
-   [LINQ 查詢的結構](#StructureOfALINQQuery)  
  
-   [Visual Basic LINQ 查詢運算子](#VisualBasicLINQQueryOperators)  
  
-   [使用 LINQ to SQL 連接至資料庫](#ConnectingToADatabase)  
  
-   [支援 LINQ 的 Visual Basic 功能](#VisualBasicFeaturesThatSupportLINQ)  
  
-   [延後和立即查詢執行](#QueryExecution)  
  
-   [在 Visual Basic 中的 XML](#XMLInVisualBasic)  
  
-   [相關的資源](#RelatedResources)  
  
-   [How To 和逐步解說主題](#HowToAndWalkthroughTopics)  
  
##  <a name="RunningtheExamples"></a>執行範例  
 執行簡介和＜LINQ 查詢結構＞一節中的範例，包括下列程式碼，會傳回客戶和訂單清單。  
  
 [!code-vb[VbVbalrIntroToLINQ #&31;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
##  <a name="LINQProviders"></a>LINQ 提供者  
 A *LINQ 提供者*對應您[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]正在查詢的資料來源的 LINQ 查詢。 當您撰寫 LINQ 查詢時，提供者會接受該查詢，並將它轉譯成資料來源能夠執行的命令。 提供者也會將資料從來源轉換成組成查詢結果的物件。 最後，當您將更新傳送至資料來源時，它會將物件轉換成資料。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 包含下列 LINQ 提供者。  
  
|提供者|描述|  
|---|---|  
|LINQ to Objects|LINQ to Objects 提供者讓您查詢記憶體內部的集合和陣列。 如果物件支援<xref:System.Collections.IEnumerable>或<xref:System.Collections.Generic.IEnumerable%601>介面，LINQ to 物件提供者可讓您查詢它。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable><br /><br /> 您可以藉由匯入啟用 LINQ to 物件提供者<xref:System.Linq>命名空間，預設會匯入所有[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案。</xref:System.Linq><br /><br /> 如需 LINQ to 物件提供者的詳細資訊，請參閱[LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)。|  
|LINQ to SQL|LINQ to SQL 提供者可讓您查詢及修改 SQL Server 資料庫中的資料。 這可讓您輕鬆對應應用程式的物件模型與資料庫的資料表和物件。<br /><br /> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 納入物件關聯式設計工具 (O/R 設計工具)，讓 LINQ to SQL 更好用。 這個設計工具是用於在對應至資料庫物件的應用程式中建立物件模型。 O/R 設計工具也提供功能來對應預存程序和函式<xref:System.Data.Linq.DataContext>物件，它會管理與資料庫通訊，並且儲存開放式並行存取檢查的狀態。</xref:System.Data.Linq.DataContext><br /><br /> 如需 LINQ to SQL 提供者的詳細資訊，請參閱[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)。 如需物件關聯式設計工具的詳細資訊，請參閱[LINQ to SQL 工具，在 Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。|  
|LINQ to XML|LINQ to XML 提供者可讓您查詢及修改 XML。 您可以修改記憶體內部的 XML，也可以從檔案載入 XML 並將 XML 儲存到檔案。<br /><br /> 此外，LINQ to XML 提供者也會啟用 XML 常值和 XML 軸屬性，讓您直接在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式碼中撰寫 XML。 如需詳細資訊，請參閱[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)。|  
|LINQ to DataSet|LINQ to DataSet 的提供者可讓您在查詢和更新資料[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]資料集。 您可以將 LINQ 的強大功能加入使用資料集的應用程式，以簡化並擴充查詢、彙總及更新資料集資料的能力。<br /><br /> 如需詳細資訊，請參閱[LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)。|  
  
##  <a name="StructureOfALINQQuery"></a>LINQ 查詢的結構  
 LINQ 查詢，通常稱為*查詢運算式*，識別資料來源和查詢的反覆項目變數的查詢子句的組合所組成。 查詢運算式也可以包含排序、篩選、群組和聯結的指示，或套用至來源資料的計算。 查詢運算式語法類似於 SQL 語法，所以您會覺得大部分的語法很熟悉。  
  
 查詢運算式以 `From` 子句開頭。 這個子句會識別查詢和變數的來源資料，這些變數用於分別參考來源資料的每個項目。 這些變數的名稱是*範圍變數*或*反覆運算變數*。 查詢一定要有 `From` 子句，`Aggregate` 查詢除外，因為 `From` 子句對這類查詢為選擇性項目。 識別出 `From` 或 `Aggregate` 子句中的查詢範圍和來源之後，您可以包含任何查詢子句組合以精簡查詢。 如需查詢子句的詳細資訊，請參閱本主題後文中的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] LINQ 查詢運算子。 例如，下列查詢會將客戶資料的來源集合識別為 `customers` 變數，而反覆運算變數則稱之為 `cust`。  
  
 [!code-vb[VbVbalrIntroToLINQ #&2;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 這個範例本身就是個有效的查詢；但是當您加入更多的查詢子句來精簡結果時，查詢就會變得更強大。 例如，您可以加入 `Where` 子句，根據一或多個值來篩選結果。 查詢運算式是單行程式碼，您只可以將其他查詢子句附加至查詢結尾。 您可以使用底線 (_) 行接續字元，將查詢分割成多行文字，以提高可讀性。 下列程式碼範例顯示的查詢範例，包含 `Where` 子句。  
  
 [!code-vb[VbVbalrIntroToLINQ #&3;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 另一個功能強大的查詢子句是 `Select` 子句，可讓您只傳回從資料來源選取的欄位。 LINQ 查詢會傳回可列舉的強類型物件集合。 查詢可以傳回匿名類型或具名類型的集合。 您可以使用 `Select` 子句，只傳回資料來源的單一欄位。 當您這麼做時，傳回的集合類型就是該單一欄位的類型。 您也可以使用 `Select` 子句，傳回資料來源的多個欄位。 當您這麼做時，傳回的集合類型就是新的匿名類型。 您也可以比對查詢傳回的欄位和指定的具名類型欄位。 下列程式碼範例顯示傳回匿名類型集合的查詢運算式，該類型具有填入來自資料來源之選取欄位資料的成員。  
  
 [!code-vb[VbVbalrIntroToLINQ #&4;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 LINQ 查詢也可以用來結合多個資料來源，並傳回單一結果。 使用一或多個 `From` 子句，或使用 `Join` 或 `Group Join` 查詢子句，即可完成。 下列程式碼範例顯示的查詢運算式，結合了客戶和訂單資料，並傳回包含客戶和訂單資料的匿名類型集合。  
  
 [!code-vb[VbVbalrIntroToLINQ #&5;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 您可以使用 `Group Join` 子句建立階層式的查詢結果，其包含客戶物件的集合。 每個客戶物件都有一個屬性，包含該客戶所有訂單的集合。 下列程式碼範例顯示的查詢運算式，結合了階層式結果的客戶和訂單資料，並傳回匿名類型的集合。 查詢傳回的類型包含 `CustomerOrders` 屬性，內含客戶訂單資料的集合。 它也包含 `OrderTotal` 屬性，內含該客戶所有訂單小計的總和。 (這個查詢相當於 LEFT OUTER JOIN)。  
  
 [!code-vb[VbVbalrIntroToLINQ #&6;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 另有幾個 LINQ 查詢運算子，可讓您建立功能強大的查詢運算式。 本主題的下一節，將討論查詢運算式中可包含的各種查詢子句。 如需詳細資訊[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]查詢子句，請參閱[查詢](../../../../visual-basic/language-reference/queries/queries.md)。  
  
##  <a name="VisualBasicLINQQueryOperators"></a>Visual Basic LINQ 查詢運算子  
 中的類別<xref:System.Linq>命名空間和其他支援 LINQ 查詢的命名空間包含建立和修改您的應用程式的需求為基礎的查詢，您可以呼叫的方法。</xref:System.Linq> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 包含最常見的查詢子句關鍵字，如下表所示。  
  
|詞彙|定義|  
|---|---|  
|[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)|查詢必須有 `From` 子句或 `Aggregate` 子句才能開始。 `From` 子句會指定查詢的來源集合和反覆運算變數。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&7;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_8.vb)]|  
|[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)|選擇項。 宣告一組查詢的反覆運算變數。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&8;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_9.vb)]<br /><br /> 如果不指定 `Select` 子句，則查詢的反覆運算變數即由 `From` 或 `Aggregate` 子句指定的反覆運算變數組成。|  
|[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)|選擇項。 指定查詢的篩選條件。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&9;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_10.vb)]|  
|[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)|選擇項。 指定查詢的資料行排序。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&10;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_11.vb)]|  
|[Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md)|選擇項。 將兩個集合合併成單一集合。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&11;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_12.vb)]|  
|[Group By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)|選擇項。 群組查詢結果的項目。 可用來將彙總函式套用至每個群組。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&12;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_13.vb)]|  
|[Group Join 子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)|選擇項。 將兩個集合合併成單一階層式集合。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&13;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_14.vb)]|  
|[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)|查詢必須有 `From` 子句或 `Aggregate` 子句才能開始。 `Aggregate` 子句會將一或多個彙總函式套用至集合。 例如，您可以使用 `Aggregate` 子句計算查詢傳回的所有項目小計。<br /><br /> [!code-vb[VbVbalrIntroToLINQ #&14;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_15.vb)]<br /><br /> 也可以使用 `Aggregate` 子句修改查詢。 例如，您可以使用 `Aggregate` 子句執行相關查詢集合的計算。<br /><br /> [!code-vb[VbVbalrIntroToLINQ #&15;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_16.vb)]|  
|[Let 子句](../../../../visual-basic/language-reference/queries/let-clause.md)|選擇項。 計算值，並將它指派給查詢中的新變數。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&16;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_17.vb)]|  
|[Distinct 子句](../../../../visual-basic/language-reference/queries/distinct-clause.md)|選擇項。 限制目前反覆運算變數的值，以消除查詢結果中重複的值。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&17;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_18.vb)]|  
|[Skip 子句](../../../../visual-basic/language-reference/queries/skip-clause.md)|選擇項。 略過集合中指定數目的項目，然後傳回其餘項目。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&18;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_19.vb)]|  
|[Skip While 子句](../../../../visual-basic/language-reference/queries/skip-while-clause.md)|選擇項。 只要指定的條件為 `true`，即略過集合中的項目，然後傳回其餘項目。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&19;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_20.vb)]|  
|[Take 子句](../../../../visual-basic/language-reference/queries/take-clause.md)|選擇項。 從集合開頭傳回指定數目的連續項目。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&20;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_21.vb)]|  
|[Take While 子句](../../../../visual-basic/language-reference/queries/take-while-clause.md)|選擇項。 只要指定的條件為 `true`，即包含集合中的項目，並略過其餘項目。 例如: <br /><br /> [!code-vb[VbVbalrIntroToLINQ #&21;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_22.vb)]|  
  
 如需詳細資訊[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]查詢子句，請參閱[查詢](../../../../visual-basic/language-reference/queries/queries.md)。  
  
 透過呼叫 LINQ 提供的可列舉和可查詢類型的成員，您可以使用其他的 LINQ 查詢功能。 透過呼叫查詢運算式結果上的特定查詢運算子，您可以使用這些額外的功能。 例如，下列程式碼範例使用<xref:System.Linq.Enumerable.Union%2A>方法將兩個查詢的結果結合成一個查詢的結果。</xref:System.Linq.Enumerable.Union%2A> 它會使用<xref:System.Linq.Enumerable.ToList%2A>方法來傳回查詢結果為一般清單。</xref:System.Linq.Enumerable.ToList%2A>  
  
 [!code-vb[VbVbalrIntroToLINQ #&22;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 如需額外的 LINQ 功能的詳細資訊，請參閱[標準查詢運算子概觀](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)。  
  
##  <a name="ConnectingToADatabase"></a>使用 LINQ to SQL 連接至資料庫  
 在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中，您使用 LINQ to SQL 檔案識別要存取的 SQL Server 資料庫物件，例如資料表、檢視和預存程序。 LINQ to SQL 檔案的副檔名為 .dbml。  
  
 當您有有效的連接到 SQL Server 資料庫時，您可以加入**LINQ to SQL 類別**至您的專案項目範本。 這會顯示物件關聯式設計工具 (O/R 設計工具)。 O/R 設計工具可讓您想要存取您的程式碼中的項目拖曳**伺服器總管**/**資料庫總管**拖曳至設計工具介面上。 LINQ to SQL 檔案加入<xref:System.Data.Linq.DataContext>物件至您的專案。</xref:System.Data.Linq.DataContext> 此物件包含您想要存取的資料表和檢視的屬性和集合，以及您想要呼叫的預存程序方法。 Linq to SQL (.dbml) 檔中儲存您的變更後，您可以藉由參考程式碼中存取這些物件<xref:System.Data.Linq.DataContext>O/R 設計工具所定義的物件。</xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext>物件名為您的專案是根據您 LINQ to SQL 檔案的名稱。</xref:System.Data.Linq.DataContext> 例如，將會建立 LINQ to SQL 檔案命名為 Northwind.dbml<xref:System.Data.Linq.DataContext>物件名為`NorthwindDataContext`。</xref:System.Data.Linq.DataContext>  
  
 如需範例與逐步指示，請參閱[How to︰ 查詢資料庫](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md)和[如何︰ 呼叫預存程序](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md)。  
  
##  <a name="VisualBasicFeaturesThatSupportLINQ"></a>Visual Basic 支援 LINQ 的功能。  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 包含其他值得注意的功能，讓 LINQ 簡單易用，並減少為執行 LINQ 查詢所必須撰寫的程式碼數量。 這些需求包括下列各項：  
  
-   **匿名型別**，可讓您建立新的類型為基礎的查詢結果。  
  
-   **隱含型別變數**可讓您延後指定型別，可讓編譯器推斷型別為基礎的查詢結果。  
  
-   **擴充方法**，可讓您擴充現有類型，使用您自己的方法，而不需修改型別本身。  
  
 如需詳細資訊，請參閱[Visual Basic 功能，支援 LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md)。  
  
##  <a name="QueryExecution"></a>延後和立即查詢執行  
 查詢執行會與建立查詢分開。 查詢建立之後，會另有機制觸發執行。 可以執行查詢，因為它定義 (*立即執行*)，或定義可以儲存和更新版本才能執行查詢 (*延後執行*)。  
  
 當您建立查詢時，查詢本身預設不會立即執行。 反而會將查詢定義儲存在變數中，用以參考查詢結果。 稍後存取程式碼中的查詢結果變數時，例如在 `For…Next` 迴圈中，就會執行查詢。 此程序稱為*延後執行*。  
  
 查詢也可以執行時所定義，這指*立即執行*。 套用要求存取查詢結果個別項目的方法，可觸發立即執行。 這個結果可能會包括彙總函式，例如 `Count`、`Sum`、`Average`、`Min` 或 `Max`。 如需彙總函式的詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 使用 `ToList` 或 `ToArray` 方法也會強制立即執行。 當您想要立即執行查詢並快取結果時，這方法非常好用。 如需有關這些方法的詳細資訊，請參閱[轉換資料型別](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)。  
  
 如需查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
##  <a name="XMLInVisualBasic"></a>在 Visual Basic 中的 XML  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中的 XML 功能包括 XML 常值和 XML 軸屬性，讓您輕鬆建立、存取、查詢及修改程式碼中的 XML。 XML 常值可讓您直接在程式碼中撰寫 XML。 Visual Basic 編譯器將 XML 視為第一級的資料物件。  
  
 下列程式碼範例示範如何建立 XML 項目、存取其子項目和屬性，以及使用 LINQ 查詢項目內容。  
  
 [!code-vb[VbXmlSamples #&8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 如需詳細資訊，請參閱[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)。  
  
##  <a name="RelatedResources"></a>相關的資源  
  
|主題|描述|  
|---|---|  
|[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)|說明 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中可查詢的 XML 功能，它們還可讓您在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式碼中將 XML 當做第一級資料物件納入。|  
|[查詢](../../../../visual-basic/language-reference/queries/queries.md)|提供 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中的查詢子句參考資訊。|  
|[LINQ （語言整合式查詢）](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)|包含 LINQ 的一般資訊、程式設計指南和範例。|  
|[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)|包含 LINQ to SQL 的一般資訊、程式設計指南和範例。|  
|[LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)|包含 LINQ to Objects 的一般資訊、程式設計指南和範例。|  
|[LINQ to ADO.NET (入口網站頁面)](http://msdn.microsoft.com/library/dd7d3c6a-ff98-47e9-a1a7-2d4cfc42d150)|包含 LINQ to [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] 的一般資訊、程式設計指南和範例連結。|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)|包含 LINQ to XML 的一般資訊、程式設計指南和範例。|  
  
##  <a name="HowToAndWalkthroughTopics"></a>How To 和逐步解說主題  
 [如何︰ 查詢資料庫](how-to-query-a-database-by-using-linq.md)  
  
 [如何︰ 呼叫預存程序](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [如何︰ 修改資料庫中的資料](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [如何︰ 使用 Joins 合併資料](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [如何︰ 排序查詢結果](how-to-sort-query-results-by-using-linq.md)  
  
 [如何︰ 篩選查詢結果](how-to-filter-query-results-by-using-linq.md)  
  
 [如何︰ 統計、 加總或平均資料](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [如何︰ 尋找查詢結果中的最小值或最大值](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [如何︰ 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)  
  
## <a name="featured-book-chapters"></a>精選書籍章節  
 [第 17 章︰ LINQ](http://go.microsoft.com/fwlink/?LinkId=195277)中[程式設計 Visual Basic 2008](http://go.microsoft.com/fwlink/?LinkId=195383)  
  
## <a name="see-also"></a>另請參閱  
 [LINQ （語言整合式查詢）](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [LINQ to XML 在 Visual Basic 中的概觀](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)   
 [LINQ to DataSet 概觀](http://msdn.microsoft.com/library/dc20a8fb-03f6-4b68-9c2b-7f7299e3070b)   
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
 [LINQ to SQL 工具，在 Visual Studio 中](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)   
 [DataContext 方法 （O/R 設計工具）](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)
