---
title: LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
ms.openlocfilehash: da9529da9b45fc8ac2fdf0b19d65634dd33450fc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304573"
---
# <a name="linq-to-entities"></a>LINQ to Entities
LINQ to Entities 提供了 Language-Integrated Query (LINQ) 支援，可讓開發人員使用 Visual Basic 或 Visual C# 針對 Entity Framework 概念模型撰寫查詢。 針對 Entity Framework 執行的查詢是以命令樹查詢來表示，每一個查詢都會針對物件內容來執行。 LINQ to Entities 會將 Language-Integrated Queries (LINQ) 查詢轉換成命令樹查詢、針對 Entity Framework 執行查詢，並傳回 Entity Framework 和 LINQ 都可以使用的物件。 下列是建立及執行 LINQ to Entities 查詢的程序：  
  
1. 從 <xref:System.Data.Objects.ObjectQuery%601> 建構 <xref:System.Data.Objects.ObjectContext> 執行個體。  
  
2. 使用 <xref:System.Data.Objects.ObjectQuery%601> 執行個體，在 C# 或 Visual Basic 中撰寫 LINQ to Entities 查詢。  
  
3. 將 LINQ 標準查詢運算子和運算式轉換成命令樹。  
  
4. 在命令樹中會針對資料來源查詢執行。 執行期間於資料來源上擲回的任何例外狀況都會直接傳遞給用戶端。  
  
5. 將查詢結果傳回用戶端。  
  
## <a name="constructing-an-objectquery-instance"></a>建構 ObjectQuery 執行個體  
 <xref:System.Data.Objects.ObjectQuery%601> 泛型類別表示傳回零個或多個具型別實體之集合的查詢。 物件查詢通常是從現有的物件內容所建構 (而不是手動建構)，而且一定會屬於該物件內容。 此內容提供了撰寫及執行查詢所需的連接和中繼資料 (Metadata) 資訊。 <xref:System.Data.Objects.ObjectQuery%601> 泛型類別會實作 <xref:System.Linq.IQueryable%601> 泛型介面，此介面的 builder 方法可累加建置 LINQ 查詢。 使用 C# `var` 關鍵字 (在 Visual Basic 中啟用區域型別推斷的話為 `Dim`)，您也可以讓編譯器推斷實體類型。  
  
## <a name="composing-the-queries"></a>撰寫查詢  
 實作泛型 <xref:System.Data.Objects.ObjectQuery%601> 介面之 <xref:System.Linq.IQueryable%601> 泛型類別的執行個體會當做 LINQ to Entities 查詢的資料來源。 在查詢中，您可以精確地指定想要從資料來源中擷取的資訊。 此外，查詢也可以指定該項資訊傳回之前應該如何排序、分組和成形。 在 LINQ 中，查詢會儲存在變數內。 這個查詢變數不會採取任何動作，也不會傳回任何資料。它只會儲存查詢資訊。 在您建立查詢之後，必須執行該查詢以便擷取任何資料。  
  
 LINQ to Entities 查詢可以使用兩個不同的語法來撰寫：查詢運算式語法和以方法為基礎的查詢語法。 查詢運算式語法和以方法為基礎的查詢語法都是 C# 3.0 和 Visual Basic 9.0 中的新增功能。  
  
 如需詳細資訊，請參閱 < [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)。  
  
## <a name="query-conversion"></a>查詢轉換  
 若要針對 Entity Framework 執行 LINQ to Entities 查詢，LINQ 查詢必須轉換成可以針對 Entity Framework 執行的命令樹表示法。  
  
 包含 LINQ to Entities 查詢的 LINQ 標準查詢運算子 (例如<xref:System.Linq.Queryable.Select%2A>， <xref:System.Linq.Queryable.Where%2A>，和<xref:System.Linq.Queryable.GroupBy%2A>) 和 (x > 10、 10、contact.lastname 等等） 的運算式。 LINQ 運算子並不是由類別所定義，而是類別上的方法。 在 LINQ 中，運算式可以包含 <xref:System.Linq.Expressions> 命名空間內類型所允許的任何項目，以及能以 Lambda 函式表示的任何項目 (依擴充而定)。 這是 Entity Framework 所允許之運算式的超集，根據定義，這些運算式限制為只有資料庫上允許且 <xref:System.Data.Objects.ObjectQuery%601> 支援的作業。  
  
 在 Entity Framework 中，運算子和運算式都是由單一型別階層所代表，然後會將它們置於命令樹中。 Entity Framework 會使用此命令樹來執行查詢。 如果 LINQ 查詢不能表示為命令樹，則當轉換查詢時，將會擲回例外狀況。 LINQ to Entities 查詢的轉換牽涉到兩個子轉換：標準查詢運算子的轉換及運算式的轉換。  
  
 許多 LINQ 標準查詢運算子沒有 LINQ to Entities 中的有效轉譯。 嘗試使用這些運算子將會在查詢轉譯時產生例外狀況。 如需支援的 LINQ to Entities 運算子的清單，請參閱 <<c0> [ 支援和不受支援的 LINQ 方法 (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)。  
  
 如需使用 LINQ to Entities 中的標準查詢運算子的詳細資訊，請參閱 < [LINQ to Entities 查詢中的標準查詢運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md)。  
  
 一般來說，LINQ to Entities 中的運算式會在伺服器上評估，所以運算式的行為不需要遵循 CLR 語意。 如需詳細資訊，請參閱 < [LINQ to Entities 查詢中的運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)。  
  
 如需 CLR 方法呼叫如何對應到資料來源中的標準函式的詳細資訊，請參閱[標準函式對應的 CLR 方法](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)。  
  
 如需如何呼叫標準、 資料庫，以及自訂函式內[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]查詢，請參閱[LINQ to Entities 查詢中呼叫的函式](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)。  
  
## <a name="query-execution"></a>查詢執行  
 當使用者建立 LINQ 查詢之後，會將它轉換成與 Entity Framework 相容的表示法 (命令樹的形式)，然後針對資料來源執行此查詢。 在執行查詢時，所有的查詢運算式 (或是查詢的元件) 都會在用戶端或伺服器上評估， 這包括用於結果具體化或實體投影的運算式。 如需詳細資訊，請參閱 <<c0> [ 查詢執行](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)。 如需如何改善效能的查詢編譯一次，然後加以執行數次使用不同的參數資訊，請參閱[編譯的查詢 (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)。  
  
## <a name="materialization"></a>具體化  
 具體化是將查詢結果以 CLR 型別形式傳回用戶端的程序。 在 LINQ to Entities 中，絕對不會傳回查詢結果資料記錄；一定會有支援的 CLR 型別，該型別是由使用者或 Entity Framework 所定義或是由編譯器所產生 (匿名型別)。 所有物件具體化都是由 Entity Framework 執行。 因為無法在 Entity Framework 與 CLR 之間對應而產生的任何錯誤，都將導致物件具體化期間擲回例外狀況。  
  
 查詢結果通常會以下列其中一個項目的形式來傳回：  
  
-   零個或多個具型別實體物件的集合，或是概念模型中所定義的複雜類型的投影。  
  
-   [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 所支援的 CLR 型別。  
  
-   內嵌集合。  
  
-   匿名型別。  
  
 如需詳細資訊，請參閱 <<c0> [ 查詢結果](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
  
 [LINQ to Entities 查詢中的運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)  
  
 [在 LINQ to Entities 查詢中呼叫函式](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
  
 [已編譯查詢 (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)  
  
 [查詢執行](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)  
  
 [查詢結果](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md)  
  
 [LINQ to Entities 查詢中的標準查詢運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md)  
  
 [標準函式的對應 CLR 方法](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)  
  
 [支援與不支援的 LINQ 方法 (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
  
 [LINQ to Entities 中的已知問題和考量](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)  
  
## <a name="see-also"></a>另請參閱

- [LINQ to Entities 中的已知問題和考量](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
- [Language Integrated Query (LINQ)C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [語言整合式的查詢 (LINQ)-Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ 和 ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
