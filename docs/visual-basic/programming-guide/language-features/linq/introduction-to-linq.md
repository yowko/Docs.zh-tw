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
ms.openlocfilehash: c9a8149ecf4f2a1c76ba00b0f80bc703114e11ca
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660778"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Visual Basic 中的 LINQ 簡介
語言整合式查詢 (LINQ) 會將查詢功能加入至 Visual Basic, 並在您處理所有類型的資料時提供簡單且功能強大的功能。 LINQ 並不會將查詢傳送至要處理的資料庫, 或針對您要搜尋的每個資料類型使用不同的查詢語法, 而是將查詢引進為 Visual Basic 語言的一部分。 它使用統一的語法，不論資料類型為何。  
  
 LINQ 可讓您從 SQL Server 資料庫、XML、記憶體內部的陣列和集合、ADO.NET 資料集, 或任何支援 LINQ 的其他遠端或本機資料來源查詢資料。 您可以使用通用 Visual Basic 語言專案來執行所有動作。 因為您的查詢是以 Visual Basic 語言撰寫, 所以您的查詢結果會以強型別物件的形式傳回。 這些物件支援 IntelliSense，讓您加快撰寫程式碼的速度，並在編譯階段即捕捉查詢中的錯誤，而不是在執行階段。 LINQ 查詢可用做其他查詢來源，以精簡結果。 它們也可以繫結至控制項，讓使用者輕鬆地檢視和修改查詢結果。  
  
 例如，下列程式碼範例顯示的 LINQ 查詢，會從集合中傳回一份客戶清單，並根據位置分組。  
  
 [!code-vb[VbVbalrIntroToLINQ#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#1)]  
  
## <a name="running-the-examples"></a>執行範例  
 若要執行 [簡介] 和 [ [LINQ 查詢的結構](#structure-of-a-linq-query)] 區段中的範例, 請加入下列程式碼, 這會傳回客戶和訂單的清單。  
  
 [!code-vb[VbVbalrIntroToLINQ#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#31)]  
  
## <a name="linq-providers"></a>LINQ 提供者  
 *Linq 提供者*會將您的 Visual Basic linq 查詢對應至所查詢的資料來源。 當您撰寫 LINQ 查詢時，提供者會接受該查詢，並將它轉譯成資料來源能夠執行的命令。 提供者也會將資料從來源轉換成組成查詢結果的物件。 最後，當您將更新傳送至資料來源時，它會將物件轉換成資料。  
  
 Visual Basic 包括下列的 LINQ 提供者。  
  
|提供者|描述|  
|---|---|  
|LINQ to Objects|LINQ to Objects 提供者讓您查詢記憶體內部的集合和陣列。 如果物件支援 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> 介面，LINQ to Objects 提供者就會讓您查詢。<br /><br /> 您可以匯入<xref:System.Linq>命名空間 (預設會針對所有 Visual Basic 專案匯入) 來啟用 LINQ to Objects 提供者。<br /><br /> 如需有關 LINQ to Objects 提供者的詳細資訊, 請參閱[LINQ to Objects](../../concepts/linq/linq-to-objects.md)。|  
|LINQ to SQL|LINQ to SQL 提供者可讓您查詢及修改 SQL Server 資料庫中的資料。 這可讓您輕鬆對應應用程式的物件模型與資料庫的資料表和物件。<br /><br /> Visual Basic 藉由包含物件關聯式設計工具 (O/R 設計工具), 讓您更輕鬆地使用 LINQ to SQL。 這個設計工具是用於在對應至資料庫物件的應用程式中建立物件模型。 O/R 設計工具也提供將預存程式和函式對應至<xref:System.Data.Linq.DataContext>物件的功能, 它會管理與資料庫的通訊, 並儲存開放式平行存取檢查的狀態。<br /><br /> 如需有關 LINQ to SQL 提供者的詳細資訊, 請參閱[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)。 如需物件關聯式設計工具的詳細資訊, 請參閱[Visual Studio 中的 LINQ to SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。|  
|LINQ to XML|LINQ to XML 提供者可讓您查詢及修改 XML。 您可以修改記憶體內部的 XML，也可以從檔案載入 XML 並將 XML 儲存到檔案。<br /><br /> 此外, LINQ to XML 提供者會啟用 XML 常值和 XML 軸屬性, 讓您可以直接在您的 Visual Basic 程式碼中撰寫 XML。 如需詳細資訊, 請參閱[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)。|  
|LINQ to DataSet|LINQ to DataSet 提供者可讓您查詢和更新 ADO.NET 資料集中的資料。 您可以將 LINQ 的強大功能加入使用資料集的應用程式，以簡化並擴充查詢、彙總及更新資料集資料的能力。<br /><br /> 如需詳細資訊，請參閱 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)。|  
  
## <a name="structure-of-a-linq-query"></a>LINQ 查詢的結構  
 LINQ 查詢, 通常稱為*查詢運算式*, 由查詢子句的組合所組成, 用以識別查詢的資料來源和反復專案變數。 查詢運算式也可以包含排序、篩選、群組和聯結的指示，或套用至來源資料的計算。 查詢運算式語法類似於 SQL 語法，所以您會覺得大部分的語法很熟悉。  
  
 查詢運算式以 `From` 子句開頭。 這個子句會識別查詢和變數的來源資料，這些變數用於分別參考來源資料的每個項目。 這些變數稱為*範圍變數*或*反復專案變數*。 查詢一定要有 `From` 子句，`Aggregate` 查詢除外，因為 `From` 子句對這類查詢為選擇性項目。 識別出 `From` 或 `Aggregate` 子句中的查詢範圍和來源之後，您可以包含任何查詢子句組合以精簡查詢。 如需查詢子句的詳細資訊, 請參閱本主題稍後的 Visual Basic LINQ 查詢運算子。 例如，下列查詢會將客戶資料的來源集合識別為 `customers` 變數，而反覆運算變數則稱之為 `cust`。  
  
 [!code-vb[VbVbalrIntroToLINQ#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#2)]  
  
 這個範例本身就是個有效的查詢；但是當您加入更多的查詢子句來精簡結果時，查詢就會變得更強大。 例如，您可以加入 `Where` 子句，根據一或多個值來篩選結果。 查詢運算式是單行程式碼，您只可以將其他查詢子句附加至查詢結尾。 您可以使用底線 (\_) 行接續字元, 將查詢分解成多行文字, 以改善可讀性。 下列程式碼範例顯示的查詢範例，包含 `Where` 子句。  
  
 [!code-vb[VbVbalrIntroToLINQ#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#3)]  
  
 另一個功能強大的查詢子句是 `Select` 子句，可讓您只傳回從資料來源選取的欄位。 LINQ 查詢會傳回可列舉的強類型物件集合。 查詢可以傳回匿名類型或具名類型的集合。 您可以使用 `Select` 子句，只傳回資料來源的單一欄位。 當您這麼做時，傳回的集合類型就是該單一欄位的類型。 您也可以使用 `Select` 子句，傳回資料來源的多個欄位。 當您這麼做時，傳回的集合類型就是新的匿名類型。 您也可以比對查詢傳回的欄位和指定的具名類型欄位。 下列程式碼範例顯示傳回匿名類型集合的查詢運算式，該類型具有填入來自資料來源之選取欄位資料的成員。  
  
 [!code-vb[VbVbalrIntroToLINQ#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#4)]  
  
 LINQ 查詢也可以用來結合多個資料來源，並傳回單一結果。 使用一或多個 `From` 子句，或使用 `Join` 或 `Group Join` 查詢子句，即可完成。 下列程式碼範例顯示的查詢運算式，結合了客戶和訂單資料，並傳回包含客戶和訂單資料的匿名類型集合。  
  
 [!code-vb[VbVbalrIntroToLINQ#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#5)]  
  
 您可以使用 `Group Join` 子句建立階層式的查詢結果，其包含客戶物件的集合。 每個客戶物件都有一個屬性，包含該客戶所有訂單的集合。 下列程式碼範例顯示的查詢運算式，結合了階層式結果的客戶和訂單資料，並傳回匿名類型的集合。 查詢傳回的類型包含 `CustomerOrders` 屬性，內含客戶訂單資料的集合。 它也包含 `OrderTotal` 屬性，內含該客戶所有訂單小計的總和。 (這個查詢相當於 LEFT OUTER JOIN)。  
  
 [!code-vb[VbVbalrIntroToLINQ#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#6)]  
  
 另有幾個 LINQ 查詢運算子，可讓您建立功能強大的查詢運算式。 本主題的下一節，將討論查詢運算式中可包含的各種查詢子句。 如需 Visual Basic 查詢子句的詳細資訊, 請參閱[查詢](../../../../visual-basic/language-reference/queries/index.md)。  
  
## <a name="visual-basic-linq-query-operators"></a>Visual Basic LINQ 查詢運算子  

<xref:System.Linq> 命名空間和其他支援 LINQ 查詢的命名空間中的類別，包含了依應用程式需求建立並精簡查詢的呼叫方法。 Visual Basic 包含下列常用查詢子句的關鍵字。 如需 Visual Basic 查詢子句的詳細資訊, 請參閱[查詢](../../../language-reference/queries/index.md)。

### <a name="from-clause"></a>From 子句

必須[ `From` ](../../../../visual-basic/language-reference/queries/from-clause.md) 有`Aggregate`子句或子句, 才能開始查詢。 `From` 子句會指定查詢的來源集合和反覆運算變數。 例如：

 [!code-vb[VbVbalrIntroToLINQ#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#7)]

### <a name="select-clause"></a>Select 子句

選擇性。 子句會宣告一組查詢的反復專案變數。 [ `Select` ](../../../../visual-basic/language-reference/queries/select-clause.md) 例如：

 [!code-vb[VbVbalrIntroToLINQ#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#8)]

如果不指定 `Select` 子句，則查詢的反覆運算變數即由 `From` 或 `Aggregate` 子句指定的反覆運算變數組成。

### <a name="where-clause"></a>Where 子句

選擇性。 子句會指定查詢的篩選準則。 [ `Where` ](../../../../visual-basic/language-reference/queries/where-clause.md) 例如：

 [!code-vb[VbVbalrIntroToLINQ#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#9)]

### <a name="order-by-clause"></a>Order By 子句]

|選擇性. 子句會指定查詢中資料行的排序次序。 [ `Order By` ](../../../../visual-basic/language-reference/queries/order-by-clause.md) 例如：

 [!code-vb[VbVbalrIntroToLINQ#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#10)]

### <a name="join-clause"></a>Join 子句

選擇性。 [ `Join`子句](../../../../visual-basic/language-reference/queries/join-clause.md)會將兩個集合合併成單一集合。 例如：

 [!code-vb[VbVbalrIntroToLINQ#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#11)]

### <a name="group-by-clause"></a>Group By 子句

選擇性。 子句會將查詢結果的元素群組在一起。 [ `Group By` ](../../../../visual-basic/language-reference/queries/group-by-clause.md) 它可以用來將彙總函式套用至每個群組。 例如：

 [!code-vb[VbVbalrIntroToLINQ#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#12)]

### <a name="group-join-clause"></a>Group Join 子句

選擇性。 [ `Group Join`子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)會將兩個集合合併成一個階層式集合。 例如：

 [!code-vb[VbVbalrIntroToLINQ#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#13)]

### <a name="aggregate-clause"></a>Aggregate 子句

必須有`From`子句或子句, 才能開始查詢。 [ `Aggregate` ](../../../../visual-basic/language-reference/queries/aggregate-clause.md) `Aggregate` 子句會將一或多個彙總函式套用至集合。 例如, 您可以使用`Aggregate`子句來計算查詢所傳回之所有元素的總和, 如下列範例所示。

 [!code-vb[VbVbalrIntroToLINQ#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#14)]

也可以使用 `Aggregate` 子句修改查詢。 例如，您可以使用 `Aggregate` 子句執行相關查詢集合的計算。 例如：

 [!code-vb[VbVbalrIntroToLINQ#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#15)]

### <a name="let-clause"></a>Let 子句

選擇性。 子句會計算值, 並將它指派給查詢中的新變數。 [ `Let` ](../../../../visual-basic/language-reference/queries/let-clause.md) 例如：

 [!code-vb[VbVbalrIntroToLINQ#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#16)]

### <a name="distinct-clause"></a>Distinct 子句

選擇性。 `Distinct`子句會限制目前反覆運算變數的值, 以排除查詢結果中重複的值。 例如：

 [!code-vb[VbVbalrIntroToLINQ#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#17)]

### <a name="skip-clause"></a>Skip 子句

選擇性。 子句會略過集合中指定數目的元素, 然後傳回其餘的專案。 [ `Skip` ](../../../../visual-basic/language-reference/queries/skip-clause.md) 例如：

 [!code-vb[VbVbalrIntroToLINQ#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#18)]

### <a name="skip-while-clause"></a>Skip While 子句

選擇性。 只要指定的條件為, `true` [子句就會略過集合中的專案,然後傳回其餘的元素。`Skip While` ](../../../../visual-basic/language-reference/queries/skip-while-clause.md) 例如：

 [!code-vb[VbVbalrIntroToLINQ#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#19)]

### <a name="take-clause"></a>Take 子句

選擇性。 子句會從集合開頭傳回指定數目的連續元素。 [ `Take` ](../../../../visual-basic/language-reference/queries/take-clause.md) 例如：

 [!code-vb[VbVbalrIntroToLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#20)]

### <a name="take-while-clause"></a>Take While 子句

選擇性。 只要指定的條件為, `true` [子句就會包含集合中的元素,並略過其餘的專案。`Take While` ](../../../../visual-basic/language-reference/queries/take-while-clause.md) 例如：

 [!code-vb[VbVbalrIntroToLINQ#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#21)]
  
## <a name="use-additional-linq-query-features"></a>使用其他 LINQ 查詢功能  
  
透過呼叫 LINQ 提供的可列舉和可查詢類型的成員，您可以使用其他的 LINQ 查詢功能。 透過呼叫查詢運算式結果上的特定查詢運算子，您可以使用這些額外的功能。 例如, 下列範例會使用<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType>方法, 將兩個查詢的結果結合成一個查詢結果。 它使用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 方法傳回泛型清單的查詢結果。
  
 [!code-vb[VbVbalrIntroToLINQ#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#22)]  
  
 如需其他 LINQ 功能的詳細資訊, 請參閱[標準查詢運算子總覽](../../concepts/linq/standard-query-operators-overview.md)。  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>使用 LINQ to SQL 連接到資料庫  
 在 Visual Basic 中, 您可以使用 LINQ to SQL 檔案來識別您想要存取的 SQL Server 資料庫物件, 例如資料表、視圖和預存程式。 LINQ to SQL 檔案的副檔名為 .dbml。  
  
 當您有 SQL Server 資料庫的有效連接時, 可以將**LINQ to SQL 類別**專案範本新增至您的專案。 這會顯示物件關聯式設計工具 (O/R 設計工具)。 O/R 設計工具可讓您將想要在程式碼中存取的專案從**伺服器總管**/**資料庫總管**拖曳到設計工具介面上。 LINQ to SQL 檔案將 <xref:System.Data.Linq.DataContext> 物件加入專案。 此物件包含您想要存取的資料表和檢視的屬性和集合，以及您想要呼叫的預存程序方法。 將變更儲存至 LINQ to SQL (.dbml) 檔案之後，參考 O/R 設計工具所定義的 <xref:System.Data.Linq.DataContext> 物件，您就可以存取程式碼中的這些物件。 專案的 <xref:System.Data.Linq.DataContext> 物件依據您的 LINQ to SQL 檔案名稱來命名。 例如，名為 Northwind.dbml 的 LINQ to SQL 檔案，會建立名為 `NorthwindDataContext` 的 <xref:System.Data.Linq.DataContext> 物件。  
  
 如需有關逐步指示的範例, 請參閱[如何:查詢資料庫](how-to-query-a-database-by-using-linq.md)和[如何:呼叫預存](how-to-call-a-stored-procedure-by-using-linq.md)程式。  
  
## <a name="visual-basic-features-that-support-linq"></a>支援 LINQ 的 Visual Basic 功能  
 Visual Basic 包含其他顯著的功能, 可讓您使用 LINQ simple, 並減少您必須撰寫來執行 LINQ 查詢的程式碼數量。 這些需求包括下列各項：  
  
- **匿名型別**, 可讓您根據查詢結果建立新的類型。  
  
- **隱含類型變數**, 可讓您延後指定類型, 並讓編譯器根據查詢結果推斷類型。  
  
- **擴充方法**, 可讓您使用自己的方法擴充現有的類型, 而不需要修改類型本身。  
  
 如需詳細資訊, 請參閱[支援 LINQ 的 Visual Basic 功能](../../concepts/linq/features-that-support-linq.md)。  
  
## <a name="deferred-and-immediate-query-execution"></a>延後和立即執行查詢

 查詢執行會與建立查詢分開。 查詢建立之後，會另有機制觸發執行。 查詢可以在定義 (*立即執行*) 時立即執行, 或可以儲存定義, 而且稍後可以執行查詢 (*延後執行*)。  
  
 當您建立查詢時，查詢本身預設不會立即執行。 反而會將查詢定義儲存在變數中，用以參考查詢結果。 稍後存取程式碼中的查詢結果變數時，例如在 `For…Next` 迴圈中，就會執行查詢。 此程式稱為*延後執行*。  
  
 查詢也可以在定義時執行, 這稱為「*立即執行*」。 套用要求存取查詢結果個別項目的方法，可觸發立即執行。 這個結果可能會包括彙總函式，例如 `Count`、`Sum`、`Average`、`Min` 或 `Max`。 如需彙總函式的詳細資訊, 請參閱[Aggregate 子句](../../../language-reference/queries/aggregate-clause.md)。  
  
 使用 `ToList` 或 `ToArray` 方法也會強制立即執行。 當您想要立即執行查詢並快取結果時，這方法非常好用。 如需這些方法的詳細資訊, 請參閱[轉換資料類型](../../concepts/linq/converting-data-types.md)。  
  
 如需查詢執行的詳細資訊, 請參閱[撰寫您的第一個 LINQ 查詢](../../concepts/linq/writing-your-first-linq-query.md)。  
  
## <a name="xml-in-visual-basic"></a>Visual Basic 中的 XML  
 Visual Basic 中的 XML 功能包括 XML 常值和 XML 軸屬性, 可讓您輕鬆地在程式碼中建立、存取、查詢及修改 XML。 XML 常值可讓您直接在程式碼中撰寫 XML。 Visual Basic 編譯器將 XML 視為第一級的資料物件。  
  
 下列程式碼範例示範如何建立 XML 項目、存取其子項目和屬性，以及使用 LINQ 查詢項目內容。  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 如需詳細資訊, 請參閱[XML](../xml/index.md)。  
  
## <a name="related-resources"></a>相關資源  
  
|主題|描述|  
|---|---|  
|[XML](../../language-features/xml/index.md)|描述 Visual Basic 中可查詢的 XML 功能, 並可讓您在 Visual Basic 程式碼中將 XML 當做第一級資料物件包含。|  
|[查詢](../../../language-reference/queries/index.md)|提供 Visual Basic 中可用之查詢子句的相關參考資訊。|  
|[LINQ (Language-Integrated Query)](../../concepts/linq/index.md)|包含 LINQ 的一般資訊、程式設計指南和範例。|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|包含 LINQ to SQL 的一般資訊、程式設計指南和範例。|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|包含 LINQ to Objects 的一般資訊、程式設計指南和範例。|  
|[LINQ to ADO.NET (入口網站頁面)](../../concepts/linq/linq-to-adonet-portal-page.md)|包含 LINQ to ADO.NET 的一般資訊、程式設計指南和範例的連結。|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|包含 LINQ to XML 的一般資訊、程式設計指南和範例。|  
  
## <a name="how-to-and-walkthrough-topics"></a>How to 和逐步解說主題
 [如何：查詢資料庫](how-to-query-a-database-by-using-linq.md)  
  
 [如何：呼叫預存程式](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [如何：修改資料庫中的資料](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [如何：結合資料與聯結](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [如何：排序查詢結果](how-to-sort-query-results-by-using-linq.md)  
  
 [如何：篩選查詢結果](how-to-filter-query-results-by-using-linq.md)  
  
 [如何：計數、加總或平均資料](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [如何：尋找查詢結果中的最小或最大值](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
  
## <a name="featured-book-chapters"></a>精選書籍章節  
 [第17章:程式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10))設計中的 LINQ [Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>另請參閱

- [LINQ (Language-Integrated Query)](../../concepts/linq/index.md)
- [Visual Basic 中的 LINQ to XML 概觀](../../language-features/xml/overview-of-linq-to-xml.md)
- [LINQ to DataSet 概觀](../../../../framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) (Visual Studio 中的 LINQ to SQL 工具)
- [DataContext 方法 (O/R 設計工具)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
