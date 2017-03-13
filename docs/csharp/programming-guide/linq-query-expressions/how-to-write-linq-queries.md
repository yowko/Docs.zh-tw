---
redirect_url: /dotnet/articles/csharp/linq/write-linq-queries
caps.handback.revision: 25
---
# 如何：在 C# 中撰寫 LINQ 查詢
本主題說明可在 C\# 中撰寫 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 查詢的三種方式：  
  
1.  使用查詢語法。  
  
2.  使用方法語法。  
  
3.  使用查詢語法和方法語法的組合。  
  
 下列範例使用上列各種方法來示範幾種簡單的 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 查詢。  一般的規則是盡可能使用 \(1\)，必要時才使用 \(2\) 和 \(3\)。  
  
> [!NOTE]
>  雖然這些查詢是在記憶體中的集合上操作，但是基本語法與 [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] 和 [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 中使用的語法相同。  
  
## 範例  
  
## 查詢語法  
 撰寫多數查詢的建議方式是使用「*查詢語法*」\(Query Syntax\) 來建立「*查詢運算式*」\(Query Expression\)。  下列範例顯示三個查詢運算式。  第一個查詢運算式示範如何藉由套用具有 `where` 子句的條件來篩選或限制結果；  它會傳回來源序列中值大於 7 或小於 3 的所有項目。  第二個運算式示範如何排序傳回的結果。  第三個運算式則示範如何依據索引鍵來群組結果；  這項查詢會根據單字的第一個字母傳回兩個群組。  
  
 [!code-cs[csProgGuideLINQ#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_1.cs)]  
  
 請注意，這些查詢的型別都是 <xref:System.Collections.Generic.IEnumerable%601>。  所有的查詢都可使用 `var` 來撰寫，如下列範例所示：  
  
 `var query = from num in numbers...`  
  
 在前述各個範例中，必須等到您逐一查看 `foreach` 陳述式中的查詢變數之後，才會實際執行查詢。  如需詳細資訊，請參閱[Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
## 範例  
  
## 方法語法  
 某些查詢作業必須以方法呼叫來表示。  這種方法最常見的是傳回單一數值的方法，例如 <xref:System.Linq.Enumerable.Sum%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Average%2A> 等。  這些方法在任何查詢中永遠都是最後呼叫的方法，因為它們只代表單一值，而且不能當做其他查詢作業的來源。  下列範例顯示查詢運算式中的方法呼叫：  
  
 [!code-cs[csProgGuideLINQ#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_2.cs)]  
  
## 範例  
 如果方法具有參數，這些參數將以 [Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) 運算式的形式提供，如下列範例所示：  
  
 [!code-cs[csProgGuideLINQ#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_3.cs)]  
  
 在前面的查詢中，只有查詢 \#4 會立即執行。  這是因為這項查詢會傳回單一值，而非泛型 <xref:System.Collections.Generic.IEnumerable%601> 集合。  該方法本身必須使用 `foreach` 才能計算它的值。  
  
 前述每一項查詢都可使用 [var](../../../csharp/language-reference/keywords/var.md) 的隱含型別來撰寫，如下列範例所示：  
  
 [!code-cs[csProgGuideLINQ#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_4.cs)]  
  
## 範例  
  
## 混合查詢和方法語法  
 本範例示範如何在查詢子句的結果上使用方法語法。  您只需將查詢運算式放在括號內，然後再套用點運算子並呼叫方法即可。  在下列範例中，查詢 \#7 會傳回值介於 3 到 7 之間的數值計數。  不過，一般情況下最好使用第二個變數來存放方法呼叫的結果。  透過這種方式，查詢就比較不會與查詢的結果混淆。  
  
 [!code-cs[csProgGuideLINQ#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_5.cs)]  
  
 因為查詢 \#7 會傳回單一值而非集合，所以查詢將會立即執行。  
  
 前述查詢可以使用內含 `var` 的隱含型別來撰寫，如下列範例所示：  
  
```  
var numCount = (from num in numbers...  
```  
  
 此查詢可以使用下列方法語法來撰寫：  
  
```  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 此查詢也可以使用以下明確指定型別的方式來撰寫：  
  
```  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## 請參閱  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Walkthrough: Writing Queries in C\#](../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [where 子句](../../../csharp/language-reference/keywords/where-clause.md)