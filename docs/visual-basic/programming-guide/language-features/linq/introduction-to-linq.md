---
title: Visual Basic 中的 LINQ 簡介
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
ms.openlocfilehash: f5222d51ff2f60dd31ec52a8d5d6d52f37e02443
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739198"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Visual Basic 中的 LINQ 簡介
Language Integrated Query (LINQ) 會將查詢功能新增至 Visual Basic，並提供簡單且功能強大的功能，當您使用所有類型的資料。 而不是將查詢傳送至資料庫，以進行處理，或使用的每一個您要搜尋的資料類型不同的查詢語法，LINQ 導入了查詢，Visual Basic 語言的一部分。 它使用統一的語法，不論資料類型為何。  
  
 LINQ 可讓您查詢資料，從 SQL Server 資料庫、 XML、 記憶體中陣列和集合、 ADO.NET 資料集或任何其他支援 LINQ 的遠端或本機資料來源。 您可以執行這一切搭配一般的 Visual Basic 語言項目。 由於您的查詢以 Visual Basic 語言撰寫的就會將您的查詢結果傳回做為強型別物件。 這些物件支援 IntelliSense，讓您加快撰寫程式碼的速度，並在編譯階段即捕捉查詢中的錯誤，而不是在執行階段。 LINQ 查詢可用做其他查詢來源，以精簡結果。 它們也可以繫結至控制項，讓使用者輕鬆地檢視和修改查詢結果。  
  
 例如，下列程式碼範例顯示的 LINQ 查詢，會從集合中傳回一份客戶清單，並根據位置分組。  
  
 [!code-vb[VbVbalrIntroToLINQ#1](codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
## <a name="running-the-examples"></a>執行範例  
 若要執行的範例簡介中，然後在[LINQ 查詢結構](#structure-of-a-linq-query)區段中，加入下列程式碼，傳回的客戶和訂單的清單。  
  
 [!code-vb[VbVbalrIntroToLINQ#31](codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
## <a name="linq-providers"></a>LINQ 提供者  
 A *LINQ 提供者*將您在 Visual Basic LINQ 查詢對應至資料來源進行查詢。 當您撰寫 LINQ 查詢時，提供者會接受該查詢，並將它轉譯成資料來源能夠執行的命令。 提供者也會將資料從來源轉換成組成查詢結果的物件。 最後，當您將更新傳送至資料來源時，它會將物件轉換成資料。  
  
 Visual Basic 會包含下列 LINQ 提供者。  
  
|提供者|描述|  
|---|---|  
|LINQ to Objects|LINQ to Objects 提供者讓您查詢記憶體內部的集合和陣列。 如果物件支援 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> 介面，LINQ to Objects 提供者就會讓您查詢。<br /><br /> 您可以啟用 LINQ to Objects 提供者匯入<xref:System.Linq>命名空間，其中所有的 Visual Basic 專案預設會匯入。<br /><br /> 如需有關 LINQ to Objects 提供者的詳細資訊，請參閱 < [LINQ to Objects](../../concepts/linq/linq-to-objects.md)。|  
|LINQ to SQL|LINQ to SQL 提供者可讓您查詢及修改 SQL Server 資料庫中的資料。 這可讓您輕鬆對應應用程式的物件模型與資料庫的資料表和物件。<br /><br /> Visual Basic 可讓您更輕鬆地使用 LINQ to SQL，方法包括物件關聯式設計工具 （O/R 設計工具）。 這個設計工具是用於在對應至資料庫物件的應用程式中建立物件模型。 O/R 設計工具也提供功能來對應預存程序和函式<xref:System.Data.Linq.DataContext>物件，它會管理與資料庫通訊，並且儲存開放式並行存取檢查的狀態。<br /><br /> 如需有關 LINQ to SQL 提供者的詳細資訊，請參閱 < [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)。 如需有關物件關聯式設計工具的詳細資訊，請參閱[LINQ to SQL 工具，在 Visual Studio 中](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。|  
|LINQ to XML|LINQ to XML 提供者可讓您查詢及修改 XML。 您可以修改記憶體內部的 XML，也可以從檔案載入 XML 並將 XML 儲存到檔案。<br /><br /> 此外，LINQ to XML 提供者所提供的 XML 常值和 XML 軸屬性，可讓您直接在 Visual Basic 程式碼中撰寫 XML。 如需詳細資訊，請參閱 < [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)。|  
|LINQ to DataSet|LINQ to DataSet 提供者可讓您查詢及更新資料中[!INCLUDE[vstecado](~/includes/vstecado-md.md)]資料集。 您可以將 LINQ 的強大功能加入使用資料集的應用程式，以簡化並擴充查詢、彙總及更新資料集資料的能力。<br /><br /> 如需詳細資訊，請參閱 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)。|  
  
## <a name="structure-of-a-linq-query"></a>LINQ 查詢結構  
 LINQ 查詢，通常是指*查詢運算式*，識別資料來源和查詢的反覆運算變數的查詢子句組合所組成。 查詢運算式也可以包含排序、篩選、群組和聯結的指示，或套用至來源資料的計算。 查詢運算式語法類似於 SQL 語法，所以您會覺得大部分的語法很熟悉。  
  
 查詢運算式以 `From` 子句開頭。 這個子句會識別查詢和變數的來源資料，這些變數用於分別參考來源資料的每個項目。 這些變數稱為*範圍變數*或是*反覆運算變數*。 查詢一定要有 `From` 子句，`Aggregate` 查詢除外，因為 `From` 子句對這類查詢為選擇性項目。 識別出 `From` 或 `Aggregate` 子句中的查詢範圍和來源之後，您可以包含任何查詢子句組合以精簡查詢。 如需查詢子句的詳細資訊，請參閱本主題稍後的 Visual Basic LINQ 查詢運算子。 例如，下列查詢會將客戶資料的來源集合識別為 `customers` 變數，而反覆運算變數則稱之為 `cust`。  
  
 [!code-vb[VbVbalrIntroToLINQ#2](codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 這個範例本身就是個有效的查詢；但是當您加入更多的查詢子句來精簡結果時，查詢就會變得更強大。 例如，您可以加入 `Where` 子句，根據一或多個值來篩選結果。 查詢運算式是單行程式碼，您只可以將其他查詢子句附加至查詢結尾。 您可以跨多行文字，以提高可讀性，使用底線的分解查詢 (\_) 行接續字元。 下列程式碼範例顯示的查詢範例，包含 `Where` 子句。  
  
 [!code-vb[VbVbalrIntroToLINQ#3](codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 另一個功能強大的查詢子句是 `Select` 子句，可讓您只傳回從資料來源選取的欄位。 LINQ 查詢會傳回可列舉的強類型物件集合。 查詢可以傳回匿名類型或具名類型的集合。 您可以使用 `Select` 子句，只傳回資料來源的單一欄位。 當您這麼做時，傳回的集合類型就是該單一欄位的類型。 您也可以使用 `Select` 子句，傳回資料來源的多個欄位。 當您這麼做時，傳回的集合類型就是新的匿名類型。 您也可以比對查詢傳回的欄位和指定的具名類型欄位。 下列程式碼範例顯示傳回匿名類型集合的查詢運算式，該類型具有填入來自資料來源之選取欄位資料的成員。  
  
 [!code-vb[VbVbalrIntroToLINQ#4](codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 LINQ 查詢也可以用來結合多個資料來源，並傳回單一結果。 使用一或多個 `From` 子句，或使用 `Join` 或 `Group Join` 查詢子句，即可完成。 下列程式碼範例顯示的查詢運算式，結合了客戶和訂單資料，並傳回包含客戶和訂單資料的匿名類型集合。  
  
 [!code-vb[VbVbalrIntroToLINQ#5](codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 您可以使用 `Group Join` 子句建立階層式的查詢結果，其包含客戶物件的集合。 每個客戶物件都有一個屬性，包含該客戶所有訂單的集合。 下列程式碼範例顯示的查詢運算式，結合了階層式結果的客戶和訂單資料，並傳回匿名類型的集合。 查詢傳回的類型包含 `CustomerOrders` 屬性，內含客戶訂單資料的集合。 它也包含 `OrderTotal` 屬性，內含該客戶所有訂單小計的總和。 (這個查詢相當於 LEFT OUTER JOIN)。  
  
 [!code-vb[VbVbalrIntroToLINQ#6](codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 另有幾個 LINQ 查詢運算子，可讓您建立功能強大的查詢運算式。 本主題的下一節，將討論查詢運算式中可包含的各種查詢子句。 如需 Visual Basic 查詢子句的詳細資訊，請參閱[查詢](../../../../visual-basic/language-reference/queries/index.md)。  
  
## <a name="visual-basic-linq-query-operators"></a>Visual Basic LINQ 查詢運算子  

<xref:System.Linq> 命名空間和其他支援 LINQ 查詢的命名空間中的類別，包含了依應用程式需求建立並精簡查詢的呼叫方法。 Visual Basic 包括下列常見的查詢子句的關鍵字。 如需 Visual Basic 查詢子句的詳細資訊，請參閱[查詢](../../../language-reference/queries/index.md)。

### <a name="from-clause"></a>From 子句

任一[`From`子句](../../../../visual-basic/language-reference/queries/from-clause.md)或`Aggregate`子句，才能開始查詢。 `From` 子句會指定查詢的來源集合和反覆運算變數。 例如: 

[!code-vb[VbVbalrIntroToLINQ#7](codesnippet/VisualBasic/introduction-to-linq_8.vb)]

### <a name="select-clause"></a>Select 子句

選擇性。 A [ `Select`子句](../../../../visual-basic/language-reference/queries/select-clause.md)宣告一組查詢的反覆運算變數。 例如: 

[!code-vb[VbVbalrIntroToLINQ#8](codesnippet/VisualBasic/introduction-to-linq_9.vb)]

如果不指定 `Select` 子句，則查詢的反覆運算變數即由 `From` 或 `Aggregate` 子句指定的反覆運算變數組成。

### <a name="where-clause"></a>Where 子句

選擇性。 A [ `Where`子句](../../../../visual-basic/language-reference/queries/where-clause.md)指定查詢的篩選條件。 例如: 

[!code-vb[VbVbalrIntroToLINQ#9](codesnippet/VisualBasic/introduction-to-linq_10.vb)]

### <a name="order-by-clause"></a>Order By 子句]

|選擇性的。 [ `Order By`子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)在查詢中指定資料行的排序次序。 例如: 

[!code-vb[VbVbalrIntroToLINQ#10](codesnippet/VisualBasic/introduction-to-linq_11.vb)]

### <a name="join-clause"></a>Join 子句

選擇性。 A [ `Join`子句](../../../../visual-basic/language-reference/queries/join-clause.md)結合成單一集合的兩個集合。 例如: 

[!code-vb[VbVbalrIntroToLINQ#11](codesnippet/VisualBasic/introduction-to-linq_12.vb)]

### <a name="group-by-clause"></a>Group By 子句

選擇性。 A [ `Group By`子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)分組查詢結果的項目。 它可用來將彙總函式套用至每個群組。 例如: 

[!code-vb[VbVbalrIntroToLINQ#12](codesnippet/VisualBasic/introduction-to-linq_13.vb)]

### <a name="group-join-clause"></a>Group Join 子句

選擇性。 A [ `Group Join`子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)結合成單一階層式集合的兩個集合。 例如: 

[!code-vb[VbVbalrIntroToLINQ#13](codesnippet/VisualBasic/introduction-to-linq_14.vb)]

### <a name="aggregate-clause"></a>Aggregate 子句

任一[`Aggregate`子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)或`From`子句，才能開始查詢。 `Aggregate` 子句會將一或多個彙總函式套用至集合。 例如，您可以使用`Aggregate`子句來計算查詢所傳回的所有項目的總和，如下列範例所示。

[!code-vb[VbVbalrIntroToLINQ#14](codesnippet/VisualBasic/introduction-to-linq_15.vb)]

也可以使用 `Aggregate` 子句修改查詢。 例如，您可以使用 `Aggregate` 子句執行相關查詢集合的計算。 例如: 

[!code-vb[VbVbalrIntroToLINQ#15](codesnippet/VisualBasic/introduction-to-linq_16.vb)]

### <a name="let-clause"></a>Let 子句

選擇性。 A [ `Let`子句](../../../../visual-basic/language-reference/queries/let-clause.md)計算值，並將它指派給新的變數，在查詢中。 例如: 

[!code-vb[VbVbalrIntroToLINQ#16](codesnippet/VisualBasic/introduction-to-linq_17.vb)]

### <a name="distinct-clause"></a>Distinct 子句

選擇性。 A`Distinct`子句限制目前的反覆項目變數，以消除重複的值，查詢結果中的值。 例如: 

[!code-vb[VbVbalrIntroToLINQ#17](codesnippet/VisualBasic/introduction-to-linq_18.vb)]

### <a name="skip-clause"></a>Skip 子句

選擇性。 A [ `Skip`子句](../../../../visual-basic/language-reference/queries/skip-clause.md)略過指定的集合中的元素數目，然後傳回其餘項目。 例如: 

[!code-vb[VbVbalrIntroToLINQ#18](codesnippet/VisualBasic/introduction-to-linq_19.vb)]

### <a name="skip-while-clause"></a>Skip While 子句

選擇性。 A [ `Skip While`子句](../../../../visual-basic/language-reference/queries/skip-while-clause.md)略過集合中的項目，只要指定的條件是`true`然後傳回其餘項目。 例如: 

[!code-vb[VbVbalrIntroToLINQ#19](codesnippet/VisualBasic/introduction-to-linq_20.vb)]

### <a name="take-clause"></a>Take 子句

選擇性。 A [ `Take`子句](../../../../visual-basic/language-reference/queries/take-clause.md)從集合開頭傳回指定的數目的連續項目。 例如: 

[!code-vb[VbVbalrIntroToLINQ#20](codesnippet/VisualBasic/introduction-to-linq_21.vb)]

### <a name="take-while-clause"></a>Take While 子句

選擇性。 A [ `Take While`子句](../../../../visual-basic/language-reference/queries/take-while-clause.md)包含集合中的項目，只要指定的條件是`true`並略過其餘項目。 例如: 

[!code-vb[VbVbalrIntroToLINQ#21](codesnippet/VisualBasic/introduction-to-linq_22.vb)]
  
## <a name="use-additional-linq-query-features"></a>使用其他的 LINQ 查詢功能  
  
透過呼叫 LINQ 提供的可列舉和可查詢類型的成員，您可以使用其他的 LINQ 查詢功能。 透過呼叫查詢運算式結果上的特定查詢運算子，您可以使用這些額外的功能。 例如，下列範例會使用<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType>方法，以將兩個查詢的結果結合成一個查詢的結果。 它使用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 方法傳回泛型清單的查詢結果。
  
 [!code-vb[VbVbalrIntroToLINQ#22](codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 如需 LINQ 其他功能的詳細資訊，請參閱[標準查詢運算子概觀](../../concepts/linq/standard-query-operators-overview.md)。  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>連接到資料庫使用 LINQ to SQL  
 在 Visual Basic 中，您會識別 SQL Server 資料庫物件，例如資料表、 檢視和預存程序，您想要使用 LINQ to SQL 檔案存取。 LINQ to SQL 檔案的副檔名為 .dbml。  
  
 當您有 SQL Server 資料庫的有效連接時，您可以加入**LINQ to SQL 類別**項目範本加入專案。 這會顯示物件關聯式設計工具 (O/R 設計工具)。 O/R 設計工具可讓您想要存取您的程式碼中的項目拖曳**伺服器總管**/**資料庫總管**拖曳至設計工具介面上。 LINQ to SQL 檔案將 <xref:System.Data.Linq.DataContext> 物件加入專案。 此物件包含您想要存取的資料表和檢視的屬性和集合，以及您想要呼叫的預存程序方法。 將變更儲存至 LINQ to SQL (.dbml) 檔案之後，參考 O/R 設計工具所定義的 <xref:System.Data.Linq.DataContext> 物件，您就可以存取程式碼中的這些物件。 專案的 <xref:System.Data.Linq.DataContext> 物件依據您的 LINQ to SQL 檔案名稱來命名。 例如，名為 Northwind.dbml 的 LINQ to SQL 檔案，會建立名為 `NorthwindDataContext` 的 <xref:System.Data.Linq.DataContext> 物件。  
  
 如需範例與逐步指示，請參閱[How to:查詢資料庫](how-to-query-a-database-by-using-linq.md)和[How to:呼叫預存程序](how-to-call-a-stored-procedure-by-using-linq.md)。  
  
## <a name="visual-basic-features-that-support-linq"></a>Visual Basic 支援 LINQ 的功能。  
 Visual Basic 包含其他值得注意的功能，讓使用 LINQ 簡單，並減少執行 LINQ 查詢，您必須撰寫的程式碼數量。 這些需求包括下列各項：  
  
-   **匿名型別**，可讓您建立新的類型，根據查詢結果。  
  
-   **隱含類型變數**，可讓您延後指定類型，並讓編譯器推斷為基礎的查詢結果的型別。  
  
-   **擴充方法**，可讓您擴充現有的類型與您自己的方法，而不需修改類型本身。  
  
 如需詳細資訊，請參閱 < [Visual Basic 功能，支援 LINQ](../../concepts/linq/features-that-support-linq.md)。  
  
## <a name="deferred-and-immediate-query-execution"></a>延後和立即查詢執行

 查詢執行會與建立查詢分開。 查詢建立之後，會另有機制觸發執行。 可以執行查詢，因為它定義 (*立即執行*)，或定義可以儲存和更新版本執行查詢 (*延後執行*)。  
  
 當您建立查詢時，查詢本身預設不會立即執行。 反而會將查詢定義儲存在變數中，用以參考查詢結果。 稍後存取程式碼中的查詢結果變數時，例如在 `For…Next` 迴圈中，就會執行查詢。 此程序指*延後執行*。  
  
 查詢也可以在執行時所定義，這指*立即執行*。 套用要求存取查詢結果個別項目的方法，可觸發立即執行。 這個結果可能會包括彙總函式，例如 `Count`、`Sum`、`Average`、`Min` 或 `Max`。 如需有關彙總函式的詳細資訊，請參閱 <<c0> [ 彙總子句](../../../language-reference/queries/aggregate-clause.md)。  
  
 使用 `ToList` 或 `ToArray` 方法也會強制立即執行。 當您想要立即執行查詢並快取結果時，這方法非常好用。 如需這些方法的詳細資訊，請參閱[轉換資料類型](../../concepts/linq/converting-data-types.md)。  
  
 如需有關查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../concepts/linq/writing-your-first-linq-query.md)。  
  
## <a name="xml-in-visual-basic"></a>Visual Basic 中的 XML  
 在 Visual Basic 中的 XML 功能包括 XML 常值和 XML 軸屬性，可讓您輕鬆地建立、 存取、 查詢及修改程式碼中的 XML。 XML 常值可讓您直接在程式碼中撰寫 XML。 Visual Basic 編譯器將 XML 視為第一級的資料物件。  
  
 下列程式碼範例示範如何建立 XML 項目、存取其子項目和屬性，以及使用 LINQ 查詢項目內容。  
  
 [!code-vb[VbXmlSamples#8](../../../language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 如需詳細資訊，請參閱 < [XML](../xml/index.md)。  
  
## <a name="related-resources"></a>相關資源  
  
|主題|描述|  
|---|---|  
|[XML](../../language-features/xml/index.md)|描述在 Visual Basic 可查詢，並可讓您為 Visual Basic 程式碼中的第一級資料物件包含 XML 中的 XML 功能。|  
|[查詢](../../../language-reference/queries/index.md)|提供可在 Visual Basic 中的查詢子句的參考資訊。|  
|[LINQ (Language-Integrated Query)](../../concepts/linq/index.md)|包含 LINQ 的一般資訊、程式設計指南和範例。|  
|[LINQ to SQL](~/docs/framework/data/adonet/sql/linq/index.md)|包含 LINQ to SQL 的一般資訊、程式設計指南和範例。|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|包含 LINQ to Objects 的一般資訊、程式設計指南和範例。|  
|[LINQ to ADO.NET (入口網站頁面)](../../concepts/linq/linq-to-adonet-portal-page.md)|包含 LINQ to ADO.NET 的一般資訊、 程式設計指南和範例的連結。|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|包含 LINQ to XML 的一般資訊、程式設計指南和範例。|  
  
## <a name="how-to-and-walkthrough-topics"></a>如何和逐步解說主題
 [如何：查詢資料庫](how-to-query-a-database-by-using-linq.md)  
  
 [如何：呼叫預存程序](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [如何：修改資料庫中的資料](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [如何：使用 Joins 合併資料](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [如何：排序查詢結果](how-to-sort-query-results-by-using-linq.md)  
  
 [如何：篩選查詢結果](how-to-filter-query-results-by-using-linq.md)  
  
 [如何：計數、 加總或平均資料](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [如何：尋找查詢結果中的最小值或最大值](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
  
## <a name="featured-book-chapters"></a>精選的書籍章節  
 [第 17 章：LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10))在[Visual Basic 2008 程式設計](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>另請參閱

- [LINQ (Language-Integrated Query)](../../concepts/linq/index.md)
- [Visual Basic 中的 LINQ to XML 概觀](../../language-features/xml/overview-of-linq-to-xml.md)
- [LINQ to DataSet 概觀](~/docs/framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](~/docs/framework/data/adonet/sql/linq/index.md)
- [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) (Visual Studio 中的 LINQ to SQL 工具)
- [DataContext 方法 (O/R 設計工具)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
