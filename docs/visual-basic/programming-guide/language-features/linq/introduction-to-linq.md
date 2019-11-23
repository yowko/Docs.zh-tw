---
title: LINQ 簡介
ms.date: 08/28/2018
helpviewer_keywords:
- queries [LINQ in Visual Basic], about LINQ in Visual Basic queries
- query execution [LINQ in Visual Basic]
- range variables [Visual Basic]
- LINQ [Visual Basic]
- LINQ [Visual Basic], about LINQ in Visual Basic
- query expressions [LINQ in Visual Basic]
- LINQ
- deferred execution
- iteration variables [Visual Basic]
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
ms.openlocfilehash: 610f2a1020cc15f855b3ddfc0917e14aae34fb82
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344929"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Visual Basic 中的 LINQ 簡介
Language-Integrated Query (LINQ) adds query capabilities to Visual Basic and provides simple and powerful capabilities when you work with all kinds of data. Rather than sending a query to a database to be processed, or working with different query syntax for each type of data that you are searching, LINQ introduces queries as part of the Visual Basic language. 它使用統一的語法，不論資料類型為何。  
  
 LINQ enables you to query data from a SQL Server database, XML, in-memory arrays and collections, ADO.NET datasets, or any other remote or local data source that supports LINQ. You can do all this with common Visual Basic language elements. Because your queries are written in the Visual Basic language, your query results are returned as strongly-typed objects. 這些物件支援 IntelliSense，讓您加快撰寫程式碼的速度，並在編譯階段即捕捉查詢中的錯誤，而不是在執行階段。 LINQ 查詢可用做其他查詢來源，以精簡結果。 它們也可以繫結至控制項，讓使用者輕鬆地檢視和修改查詢結果。  
  
 例如，下列程式碼範例顯示的 LINQ 查詢，會從集合中傳回一份客戶清單，並根據位置分組。  
  
 [!code-vb[VbVbalrIntroToLINQ#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#1)]  
  
## <a name="running-the-examples"></a>執行範例  
 To run the examples in the introduction and in the [Structure of a LINQ Query](#structure-of-a-linq-query) section, include the following code, which returns lists of customers and orders.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#31)]  
  
## <a name="linq-providers"></a>LINQ providers  
 A *LINQ provider* maps your Visual Basic LINQ queries to the data source being queried. 當您撰寫 LINQ 查詢時，提供者會接受該查詢，並將它轉譯成資料來源能夠執行的命令。 提供者也會將資料從來源轉換成組成查詢結果的物件。 最後，當您將更新傳送至資料來源時，它會將物件轉換成資料。  
  
 Visual Basic includes the following LINQ providers.  
  
|Provider|描述|  
|---|---|  
|LINQ to Objects|LINQ to Objects 提供者讓您查詢記憶體內部的集合和陣列。 如果物件支援 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> 介面，LINQ to Objects 提供者就會讓您查詢。<br /><br /> You can enable the LINQ to Objects provider by importing the <xref:System.Linq> namespace, which is imported by default for all Visual Basic projects.<br /><br /> For more information about the LINQ to Objects provider, see [LINQ to Objects](../../concepts/linq/linq-to-objects.md).|  
|LINQ to SQL|LINQ to SQL 提供者可讓您查詢及修改 SQL Server 資料庫中的資料。 這可讓您輕鬆對應應用程式的物件模型與資料庫的資料表和物件。<br /><br /> Visual Basic makes it easier to work with LINQ to SQL by including the Object Relational Designer (O/R Designer). 這個設計工具是用於在對應至資料庫物件的應用程式中建立物件模型。 The O/R Designer also provides functionality to map stored procedures and functions to the <xref:System.Data.Linq.DataContext> object, which manages communication with the database and stores state for optimistic concurrency checks.<br /><br /> For more information about the LINQ to SQL provider, see [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). For more information about the Object Relational Designer, see [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ to XML|LINQ to XML 提供者可讓您查詢及修改 XML。 您可以修改記憶體內部的 XML，也可以從檔案載入 XML 並將 XML 儲存到檔案。<br /><br /> Additionally, the LINQ to XML provider enables XML literals and XML axis properties that enable you to write XML directly in your Visual Basic code. For more information, see [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ to DataSet|The LINQ to DataSet provider enables you to query and update data in an ADO.NET dataset. 您可以將 LINQ 的強大功能加入使用資料集的應用程式，以簡化並擴充查詢、彙總及更新資料集資料的能力。<br /><br /> 如需詳細資訊，請參閱 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)。|  
  
## <a name="structure-of-a-linq-query"></a>Structure of a LINQ query  
 A LINQ query, often referred to as a *query expression*, consists of a combination of query clauses that identify the data sources and iteration variables for the query. 查詢運算式也可以包含排序、篩選、群組和聯結的指示，或套用至來源資料的計算。 查詢運算式語法類似於 SQL 語法，所以您會覺得大部分的語法很熟悉。  
  
 查詢運算式以 `From` 子句開頭。 這個子句會識別查詢和變數的來源資料，這些變數用於分別參考來源資料的每個項目。 These variables are named *range variables* or *iteration variables*. 查詢一定要有 `From` 子句，`Aggregate` 查詢除外，因為 `From` 子句對這類查詢為選擇性項目。 識別出 `From` 或 `Aggregate` 子句中的查詢範圍和來源之後，您可以包含任何查詢子句組合以精簡查詢。 For details about query clauses, see Visual Basic LINQ Query Operators later in this topic. 例如，下列查詢會將客戶資料的來源集合識別為 `customers` 變數，而反覆運算變數則稱之為 `cust`。  
  
 [!code-vb[VbVbalrIntroToLINQ#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#2)]  
  
 這個範例本身就是個有效的查詢；但是當您加入更多的查詢子句來精簡結果時，查詢就會變得更強大。 例如，您可以加入 `Where` 子句，根據一或多個值來篩選結果。 查詢運算式是單行程式碼，您只可以將其他查詢子句附加至查詢結尾。 You can break up a query across multiple lines of text to improve readability by using the underscore (\_) line-continuation character. 下列程式碼範例顯示的查詢範例，包含 `Where` 子句。  
  
 [!code-vb[VbVbalrIntroToLINQ#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#3)]  
  
 另一個功能強大的查詢子句是 `Select` 子句，可讓您只傳回從資料來源選取的欄位。 LINQ 查詢會傳回可列舉的強類型物件集合。 查詢可以傳回匿名類型或具名類型的集合。 您可以使用 `Select` 子句，只傳回資料來源的單一欄位。 當您這麼做時，傳回的集合類型就是該單一欄位的類型。 您也可以使用 `Select` 子句，傳回資料來源的多個欄位。 當您這麼做時，傳回的集合類型就是新的匿名類型。 您也可以比對查詢傳回的欄位和指定的具名類型欄位。 下列程式碼範例顯示傳回匿名類型集合的查詢運算式，該類型具有填入來自資料來源之選取欄位資料的成員。  
  
 [!code-vb[VbVbalrIntroToLINQ#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#4)]  
  
 LINQ 查詢也可以用來結合多個資料來源，並傳回單一結果。 使用一或多個 `From` 子句，或使用 `Join` 或 `Group Join` 查詢子句，即可完成。 下列程式碼範例顯示的查詢運算式，結合了客戶和訂單資料，並傳回包含客戶和訂單資料的匿名類型集合。  
  
 [!code-vb[VbVbalrIntroToLINQ#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#5)]  
  
 您可以使用 `Group Join` 子句建立階層式的查詢結果，其包含客戶物件的集合。 每個客戶物件都有一個屬性，包含該客戶所有訂單的集合。 下列程式碼範例顯示的查詢運算式，結合了階層式結果的客戶和訂單資料，並傳回匿名類型的集合。 查詢傳回的類型包含 `CustomerOrders` 屬性，內含客戶訂單資料的集合。 它也包含 `OrderTotal` 屬性，內含該客戶所有訂單小計的總和。 (這個查詢相當於 LEFT OUTER JOIN)。  
  
 [!code-vb[VbVbalrIntroToLINQ#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#6)]  
  
 另有幾個 LINQ 查詢運算子，可讓您建立功能強大的查詢運算式。 本主題的下一節，將討論查詢運算式中可包含的各種查詢子句。 For details about Visual Basic query clauses, see [Queries](../../../../visual-basic/language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Visual Basic LINQ query operators  

<xref:System.Linq> 命名空間和其他支援 LINQ 查詢的命名空間中的類別，包含了依應用程式需求建立並精簡查詢的呼叫方法。 Visual Basic includes keywords for the following common query clauses. For details about Visual Basic query clauses, see [Queries](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>From 子句

Either a [`From` clause](../../../../visual-basic/language-reference/queries/from-clause.md) or an `Aggregate` clause is required to begin a query. `From` 子句會指定查詢的來源集合和反覆運算變數。 例如:

 [!code-vb[VbVbalrIntroToLINQ#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#7)]

### <a name="select-clause"></a>Select 子句

選擇項。 A [`Select` clause](../../../../visual-basic/language-reference/queries/select-clause.md) declares a set of iteration variables for a query. 例如:

 [!code-vb[VbVbalrIntroToLINQ#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#8)]

如果不指定 `Select` 子句，則查詢的反覆運算變數即由 `From` 或 `Aggregate` 子句指定的反覆運算變數組成。

### <a name="where-clause"></a>Where 子句

選擇項。 A [`Where` clause](../../../../visual-basic/language-reference/queries/where-clause.md) specifies a filtering condition for a query. 例如:

 [!code-vb[VbVbalrIntroToLINQ#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#9)]

### <a name="order-by-clause"></a>Order By clause]

|Optional. An [`Order By` clause](../../../../visual-basic/language-reference/queries/order-by-clause.md) specifies the sort order for columns in a query. 例如:

 [!code-vb[VbVbalrIntroToLINQ#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#10)]

### <a name="join-clause"></a>Join 子句

選擇項。 A [`Join` clause](../../../../visual-basic/language-reference/queries/join-clause.md) combines two collections into a single collection. 例如:

 [!code-vb[VbVbalrIntroToLINQ#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#11)]

### <a name="group-by-clause"></a>Group By 子句

選擇項。 A [`Group By` clause](../../../../visual-basic/language-reference/queries/group-by-clause.md) groups the elements of a query result. It can be used to apply aggregate functions to each group. 例如:

 [!code-vb[VbVbalrIntroToLINQ#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#12)]

### <a name="group-join-clause"></a>Group Join 子句

選擇項。 A [`Group Join` clause](../../../../visual-basic/language-reference/queries/group-join-clause.md) combines two collections into a single hierarchical collection. 例如:

 [!code-vb[VbVbalrIntroToLINQ#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#13)]

### <a name="aggregate-clause"></a>Aggregate 子句

Either an [`Aggregate` clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) or a `From` clause is required to begin a query. `Aggregate` 子句會將一或多個彙總函式套用至集合。 For example, you can use the `Aggregate` clause to calculate a sum for all the elements returned by a query, as the following example does.

 [!code-vb[VbVbalrIntroToLINQ#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#14)]

也可以使用 `Aggregate` 子句修改查詢。 例如，您可以使用 `Aggregate` 子句執行相關查詢集合的計算。 例如:

 [!code-vb[VbVbalrIntroToLINQ#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#15)]

### <a name="let-clause"></a>Let 子句

選擇項。 A [`Let` clause](../../../../visual-basic/language-reference/queries/let-clause.md) computes a value and assigns it to a new variable in the query. 例如:

 [!code-vb[VbVbalrIntroToLINQ#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#16)]

### <a name="distinct-clause"></a>Distinct 子句

選擇項。 A `Distinct` clause restricts the values of the current iteration variable to eliminate duplicate values in query results. 例如:

 [!code-vb[VbVbalrIntroToLINQ#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#17)]

### <a name="skip-clause"></a>Skip 子句

選擇項。 A [`Skip` clause](../../../../visual-basic/language-reference/queries/skip-clause.md) bypasses a specified number of elements in a collection and then returns the remaining elements. 例如:

 [!code-vb[VbVbalrIntroToLINQ#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#18)]

### <a name="skip-while-clause"></a>Skip While 子句

選擇項。 A [`Skip While` clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md) bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements. 例如:

 [!code-vb[VbVbalrIntroToLINQ#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#19)]

### <a name="take-clause"></a>Take 子句

選擇項。 A [`Take` clause](../../../../visual-basic/language-reference/queries/take-clause.md) returns a specified number of contiguous elements from the start of a collection. 例如:

 [!code-vb[VbVbalrIntroToLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#20)]

### <a name="take-while-clause"></a>Take While 子句

選擇項。 A [`Take While` clause](../../../../visual-basic/language-reference/queries/take-while-clause.md) includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements. 例如:

 [!code-vb[VbVbalrIntroToLINQ#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#21)]
  
## <a name="use-additional-linq-query-features"></a>Use additional LINQ query features  
  
透過呼叫 LINQ 提供的可列舉和可查詢類型的成員，您可以使用其他的 LINQ 查詢功能。 透過呼叫查詢運算式結果上的特定查詢運算子，您可以使用這些額外的功能。 For example, the following example uses the <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType> method to combine the results of two queries into one query result. 它使用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 方法傳回泛型清單的查詢結果。
  
 [!code-vb[VbVbalrIntroToLINQ#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#22)]  
  
 For details about additional LINQ capabilities, see [Standard Query Operators Overview](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>Connect to a database by using LINQ to SQL  
 In Visual Basic, you identify the SQL Server database objects, such as tables, views, and stored procedures, that you want to access by using a LINQ to SQL file. LINQ to SQL 檔案的副檔名為 .dbml。  
  
 When you have a valid connection to a SQL Server database, you can add a **LINQ to SQL Classes** item template to your project. 這會顯示物件關聯式設計工具 (O/R 設計工具)。 The O/R Designer enables you to drag the items that you want to access in your code from the **Server Explorer**/**Database Explorer** onto the designer surface. LINQ to SQL 檔案將 <xref:System.Data.Linq.DataContext> 物件加入專案。 此物件包含您想要存取的資料表和檢視的屬性和集合，以及您想要呼叫的預存程序方法。 將變更儲存至 LINQ to SQL (.dbml) 檔案之後，參考 O/R 設計工具所定義的 <xref:System.Data.Linq.DataContext> 物件，您就可以存取程式碼中的這些物件。 專案的 <xref:System.Data.Linq.DataContext> 物件依據您的 LINQ to SQL 檔案名稱來命名。 例如，名為 Northwind.dbml 的 LINQ to SQL 檔案，會建立名為 `NorthwindDataContext` 的 <xref:System.Data.Linq.DataContext> 物件。  
  
 For examples with step-by-step instructions, see [How to: Query a Database](how-to-query-a-database-by-using-linq.md) and [How to: Call a Stored Procedure](how-to-call-a-stored-procedure-by-using-linq.md).  
  
## <a name="visual-basic-features-that-support-linq"></a>Visual Basic features that support LINQ  
 Visual Basic includes other notable features that make the use of LINQ simple and reduce the amount of code that you must write to perform LINQ queries. 這些需求包括下列各項：  
  
- **Anonymous types**, which enable you to create a new type based on a query result.  
  
- **Implicitly typed variables**, which enable you to defer specifying a type and let the compiler infer the type based on the query result.  
  
- **Extension methods**, which enable you to extend an existing type with your own methods without modifying the type itself.  
  
 For details, see [Visual Basic Features That Support LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Deferred and immediate query execution

 查詢執行會與建立查詢分開。 查詢建立之後，會另有機制觸發執行。 A query can be executed as soon as it is defined (*immediate execution*), or the definition can be stored and the query can be executed later (*deferred execution*).  
  
 當您建立查詢時，查詢本身預設不會立即執行。 反而會將查詢定義儲存在變數中，用以參考查詢結果。 稍後存取程式碼中的查詢結果變數時，例如在 `For…Next` 迴圈中，就會執行查詢。 This process is referred to as *deferred execution*.  
  
 Queries can also be executed when they are defined, which is referred to as *immediate execution*. 套用要求存取查詢結果個別項目的方法，可觸發立即執行。 這個結果可能會包括彙總函式，例如 `Count`、`Sum`、`Average`、`Min` 或 `Max`。 For more information about aggregate functions, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md).  
  
 使用 `ToList` 或 `ToArray` 方法也會強制立即執行。 當您想要立即執行查詢並快取結果時，這方法非常好用。 For more information about these methods, see [Converting Data Types](../../concepts/linq/converting-data-types.md).  
  
 For more information about query execution, see [Writing Your First LINQ Query](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>Visual Basic 中的 XML  
 The XML features in Visual Basic include XML literals and XML axis properties, which enable you easily to create, access, query, and modify XML in your code. XML 常值可讓您直接在程式碼中撰寫 XML。 Visual Basic 編譯器將 XML 視為第一級的資料物件。  
  
 下列程式碼範例示範如何建立 XML 項目、存取其子項目和屬性，以及使用 LINQ 查詢項目內容。  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 For more information, see [XML](../xml/index.md).  
  
## <a name="related-resources"></a>相關資源  
  
|主題|描述|  
|---|---|  
|[XML](../../language-features/xml/index.md)|Describes the XML features in Visual Basic that can be queried and that enable you to include XML as first-class data objects in your Visual Basic code.|  
|[查詢](../../../language-reference/queries/index.md)|Provides reference information about the query clauses that are available in Visual Basic.|  
|[LINQ (Language-Integrated Query)](../../concepts/linq/index.md)|包含 LINQ 的一般資訊、程式設計指南和範例。|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|包含 LINQ to SQL 的一般資訊、程式設計指南和範例。|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|包含 LINQ to Objects 的一般資訊、程式設計指南和範例。|  
|[LINQ to ADO.NET (入口網站頁面)](../../concepts/linq/linq-to-adonet-portal-page.md)|Includes links to general information, programming guidance, and samples for LINQ to ADO.NET.|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|包含 LINQ to XML 的一般資訊、程式設計指南和範例。|  
  
## <a name="how-to-and-walkthrough-topics"></a>How to and walkthrough topics
 [如何：查詢資料庫](how-to-query-a-database-by-using-linq.md)  
  
 [如何：呼叫預存程序](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [如何：修改資料庫中的資料](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [如何：使用 Joins 合併資料](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [如何：排序查詢結果](how-to-sort-query-results-by-using-linq.md)  
  
 [如何：篩選查詢結果](how-to-filter-query-results-by-using-linq.md)  
  
 [如何：統計、加總或平均資料](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [如何：尋找查詢結果中的最小或最大值](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
  
## <a name="featured-book-chapters"></a>Featured book chapters  
 [Chapter 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) in [Programming Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>請參閱

- [LINQ (Language-Integrated Query)](../../concepts/linq/index.md)
- [Visual Basic 中的 LINQ to XML 概觀](../../language-features/xml/overview-of-linq-to-xml.md)
- [LINQ to DataSet 概觀](../../../../framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) (Visual Studio 中的 LINQ to SQL 工具)
- [DataContext 方法 (O/R 設計工具)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
