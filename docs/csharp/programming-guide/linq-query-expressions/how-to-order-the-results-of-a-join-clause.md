---
redirect_url: /dotnet/articles/csharp/linq/order-the-results-of-a-join-clause
caps.handback.revision: 6
---
# 如何：排序 Join 子句的結果 (C# 程式設計手冊)
這個範例會示範如何排序聯結作業的結果。  請注意，在聯結後才會進行排序。  雖然您可以在聯結之前搭配一個或多個來源序列 \(Sequence\) 使用 `orderby` 子句，但是我們通常不建議這種做法。  一些 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 提供者可能不會保留在聯結後的排序。  
  
## 範例  
 這個查詢會建立群組聯結，並接著根據仍在範圍中的分類項目來排序這些群組。  在匿名型別初始設定式內，子查詢 \(Subquery\) 會排序產品序列中的所有相符項目。  
  
 [!code-cs[csProgGuideLINQ#81](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#81)]  
  
## 編譯程式碼  
  
-   建立以 .NET Framework 3.5 版為目標的 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] 專案。  根據預設，專案有 System.Core.dll 的參考，以及 System.Linq 命名空間的 `using` 指示詞。  
  
-   將程式碼複製至您的專案中。  
  
-   按 F5 編譯和執行程式。  
  
-   按任何鍵離開主控台視窗。  
  
## 請參閱  
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [orderby 子句](../../../csharp/language-reference/keywords/orderby-clause.md)   
 [join 子句](../../../csharp/language-reference/keywords/join-clause.md)   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)