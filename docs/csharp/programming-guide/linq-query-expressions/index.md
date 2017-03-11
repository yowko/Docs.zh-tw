---
redirect_url: /dotnet/articles/csharp/linq/index
caps.handback.revision: 21
---
# LINQ 查詢運算式 (C# 程式設計手冊)
[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext-md.md)] 是一組技術的名稱，這組技術所憑藉的基礎是將查詢功能直接整合至 C\# 語言 \(以及 Visual Basic，也可能是其他任何 .NET 語言\) 中。  透過 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)]，查詢現在已成為第一級的語言建構，就如同類別、方法、事件等等。  
  
 對於撰寫查詢的開發人員而言，[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 最明顯的「語言整合」部分就是它的查詢運算式。  查詢運算式是以 C\# 3.0 所引入的宣告式「*查詢語法*」\(Query Syntax\) 來撰寫。  透過使用查詢語法，您可以使用最少的程式碼，在資料來源上執行更為複雜的篩選、排序和群組等作業。  您可以使用相同的基本查詢運算式模式，在 SQL 資料庫、[!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] 資料集、XML 文件和資料流以及 .NET 集合中查詢及轉換資料。  
  
 下列範例顯示完整的查詢作業。  這套完整的作業包括建立資料來源、定義查詢運算式，以及在 `foreach` 陳述式中執行查詢。  
  
 [!code-cs[csProgGuideLINQ#11](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#11)]  
  
 如需 C\# 中 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 之基本概念的詳細資訊，請參閱 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)。  
  
## 查詢運算式概觀  
  
-   查詢運算式可用來查詢及轉換 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 所支援之資料來源中的資料。  例如，單一查詢可以從 SQL 資料庫擷取資料，並產生 XML 資料流做為輸出。  
  
-   查詢運算式非常容易學習，因為它使用了許多類似 C\# 的語言建構。  如需詳細資訊，請參閱 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)。  
  
-   查詢運算式中的變數全都是強式型別變數，不過在許多情況下您並不需要明確提供型別，因為編譯器可以推斷其型別。  如需詳細資訊，請參閱[Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。  
  
-   在您使用 `foreach` 迴圈逐一查看迴圈中的查詢變數之前，查詢都不會執行。  如需詳細資訊，請參閱[Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
-   在編譯時期，查詢運算式會依據 C\# 規格中所訂立的規則，轉換成「標準查詢運算子」方法呼叫。  可以使用查詢語法表示的任何查詢也都可以使用方法語法來表示。  不過，在大部分的情況下，查詢語法的可讀性較高，也較為精簡。  如需詳細資訊，請參閱 [C\# 語言規格](../../../csharp/language-reference/language-specification.md)和[Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
-   撰寫 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 查詢時，我們建議您盡可能使用查詢語法，必要時才使用方法語法。  這兩種不同的形式在語意或效能上並沒有任何差異。  查詢運算式的可讀性通常高於以方法語法撰寫的對等運算式。  
  
-   某些查詢作業 \(例如 <xref:System.Linq.Enumerable.Count%2A> 或 <xref:System.Linq.Enumerable.Max%2A>\) 並沒有對等的查詢運算式子句，因此必須以方法呼叫來表示。  方法語法可以透過各種方式與查詢語法合併使用。  如需詳細資訊，請參閱[Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。  
  
-   根據查詢所套用的型別而定，查詢運算式可以編譯成運算式樹狀架構或委派。  <xref:System.Collections.Generic.IEnumerable%601> 查詢會編譯成委派。  <xref:System.Linq.IQueryable> 和 <xref:System.Linq.IQueryable%601> 查詢則會編譯成運算式樹狀架構。  如需詳細資訊，請參閱 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 下表列出的主題提供了有關查詢的其他資訊以及一般工作的程式碼範例。  
  
|主題|描述|  
|--------|--------|  
|[查詢運算式基本概念](../../../csharp/programming-guide/linq-query-expressions/query-expression-basics.md)|簡介基本查詢概念，並提供 C\# 查詢語法的範例。|  
|[如何：在 C\# 中撰寫 LINQ 查詢](../../../csharp/programming-guide/linq-query-expressions/how-to-write-linq-queries.md)|提供幾種基本查詢運算式類型的範例。|  
|[如何：處理查詢運算式中的例外狀況](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)|將可能擲回例外狀況的程式碼移出查詢運算式的方式和時機。|  
|[How to: Populate Object Collections from Multiple Sources \(LINQ\)](../Topic/How%20to:%20Populate%20Object%20Collections%20from%20Multiple%20Sources%20\(LINQ\).md)|如何使用 `select` 陳述式將不同來源的資料合併成新的型別。|  
|[如何：分組查詢結果](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)|示範使用 `group` 子句的各種不同方式。|  
|[如何：建立巢狀群組](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)|示範如何建立巢狀群組。|  
|[如何：在分組作業上執行子查詢](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)|示範如何使用查詢中的子運算式做為新查詢的資料來源。|  
|[如何：以連續鍵分組結果](../../../csharp/programming-guide/linq-query-expressions/how-to-group-results-by-contiguous-keys.md)|說明如何實作安全執行緒 \(Thread\-Safe\) 標準查詢運算子，這個運算子可以在資料流 \(Streaming\) 資料來源上執行群組作業。|  
|[如何：在執行階段動態指定述詞篩選條件](../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)|示範如何提供任意數目的值，以用於 `where` 子句中的相等比較。|  
|[如何：將查詢的結果儲存在記憶體中](../../../csharp/programming-guide/linq-query-expressions/how-to-store-the-results-of-a-query-in-memory.md)|說明如何在不使用 `foreach` 迴圈的情況下，應用並儲存查詢結果。|  
|[如何：從方法傳回查詢](../../../csharp/programming-guide/linq-query-expressions/how-to-return-a-query-from-a-method.md)|示範如何從方法傳回查詢變數，以及如何將這些變數傳遞至方法做為輸入參數。|  
|[如何：執行自訂聯結作業](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)|示範如何依據任何一種述詞函式來執行聯結作業。|  
|[如何：使用複合索引鍵執行聯結](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)|示範如何依據多個相符索引鍵來聯結兩個來源。|  
|[如何：排序 Join 子句的結果](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)|示範如何排序聯結作業所產生的序列。|  
|[如何：執行內部聯結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)|示範如何在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 中執行內部聯結 \(Inner Join\)。|  
|[如何：執行群組連結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)|示範如何在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 中產生群組聯結。|  
|[如何：執行左外部連結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)|示範如何在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 中產生左外部聯結 \(Left Outer Join\)。|  
|[如何：處理查詢運算式中的 Null 值](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-null-values-in-query-expressions.md)|示範如何處理 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 查詢中的 null 值。|  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Walkthrough: Writing Queries in C\#](../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Basic LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)   
 [Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)   
 [Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [查詢關鍵字 \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Linq to Objects 查詢的運作方式](http://go.microsoft.com/fwlink/?LinkId=112389)   
 [讀取和寫入查詢](http://go.microsoft.com/fwlink/?LinkId=112391)   
 [何謂集合？](http://go.microsoft.com/fwlink/?LinkId=112394)   
 [連結至任何內容：LINQ 提供者清單](http://go.microsoft.com/fwlink/?LinkId=112411)