---
redirect_url: /dotnet/articles/csharp/linq/store-the-results-of-a-query-in-memory
caps.handback.revision: 13
---
# 如何：將查詢的結果儲存在記憶體中 (C# 程式設計手冊)
查詢基本上是如何擷取及組織資料的一組指示。  若要執行查詢，需要呼叫其 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法。  在您使用 `foreach` 迴圈反覆查看項目時會進行此呼叫。  要評估查詢並儲存它的結果，而不執行 `foreach` 迴圈，請呼叫在查詢變數的下列其中一種方法:  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 建議當您儲存查詢結果時，將傳回的集合物件指派給新變數，如下列範例所示：  
  
## 範例  
 [!code-cs[csProgGuideLINQ#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  
## 編譯程式碼  
  
-   建立以 .NET Framework 3.5 版為目標的 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] 專案。  根據預設，專案有 System.Core.dll 的參考，以及 System.Linq 命名空間的 `using` 指示詞。  
  
-   將程式碼複製至您的專案中。  
  
-   按 F5 編譯和執行程式。  
  
-   按任何鍵離開主控台視窗。  
  
## 請參閱  
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)