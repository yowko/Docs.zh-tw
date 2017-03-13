---
redirect_url: /dotnet/articles/csharp/linq/handle-exceptions-in-query-expressions
caps.handback.revision: 15
---
# 如何：處理查詢運算式中的例外狀況 (C# 程式設計手冊)
可以在查詢運算式的內容中呼叫任何方法。  但是，建議您避免在會導致副作用的查詢運算式中呼叫任何方法，副作用包括修改資料來源的內容或擲回例外狀況。  此範例顯示如何避免在查詢運算式中呼叫方法時引發例外狀況，而不違反一般的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 例外狀況處理方針。  這些方針會說明當您了解為何會在指定內容中擲回特定例外狀況時，是可以攔截該例外狀況。  如需詳細資訊，請參閱[例外狀況的最佳作法](../Topic/Best%20Practices%20for%20Exceptions.md)。  
  
 最後的範例顯示在必須於查詢執行期間擲回例外狀況時，如何處理這些情況。  
  
## 範例  
 下列範例顯示如何移動查詢運算式外的例外狀況處理程式碼。  這只有在方法不依賴查詢的任何區域變數時可行。  
  
 [!code-cs[csProgGuideLINQ#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## 範例  
 在某些情況下，對於從查詢內擲回之例外狀況最好的回應可能是立即停止執行查詢。  下列範例顯示如何處理從查詢主體內擲回的例外狀況。  假設 `SomeMethodThatMightThrow` 可能會造成需要停止執行查詢的例外狀況。  
  
 請注意，`try` 區塊包含 `foreach` 迴圈，但不包含查詢本身。  這是因為 `foreach` 迴圈是查詢實際執行的點。  如需詳細資訊，請參閱[Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
 [!code-cs[csProgGuideLINQ#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  
## 編譯程式碼  
  
-   建立以 .NET Framework 3.5 版為目標的 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] 專案。  根據預設，專案有 System.Core.dll 的參考，以及 System.Linq 命名空間的 `using` 指示詞。  
  
-   將程式碼複製至您的專案中。  
  
-   按 F5 編譯和執行程式。  
  
 按任何鍵離開主控台視窗。  
  
## 請參閱  
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)