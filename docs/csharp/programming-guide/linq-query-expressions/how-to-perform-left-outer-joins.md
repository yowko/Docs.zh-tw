---
redirect_url: /dotnet/articles/csharp/linq/perform-left-outer-joins
caps.handback.revision: 23
---
# 如何：執行左外部聯結 (C# 程式設計手冊)
左外部聯結是傳回第一個集合之每個項目的聯結，無論在第二個集合中有無相關項目都一樣。  您可以使用 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 呼叫群組結果的 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 方法執行左外部聯結聯結。  
  
## 範例  
 下列範例示範如何在群組聯結的結果上使用 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 方法，以執行左外部聯結。  
  
 產生兩個集合之左外部聯結的第一個步驟是使用群組聯結執行內部聯結   \(如需此處理序的說明，請參閱 [如何：執行內部聯結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)\)。在此範例中， `Person` 物件的清單內部聯結至以 `Person` 物件的 `Pet` 物件清單符合 `Pet.Owner`。  
  
 第二個步驟是包含結果集中第一個 \(左\) 集合中的每個項目，即使該項目在右集合中沒有相符項目也一樣。  這個動作可以藉由從群組聯結在相符項目的每個序列上呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 而達成。  在此範例中，呼叫 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> 符合 `Pet` 物件序列。  方法會傳回包含單一的集合，因此，如果符合 `Pet` 物件序列的任何 `Person` 物件為 null，如此可確保預設值的每個 `Person` 物件在結果集來表示。  
  
> [!NOTE]
>  參考型別的預設值是 `null`;因此，這個範例會檢查 null 參考在存取每個 `Pet` 集合中的每一個項目之前。  
  
 [!code-cs[CsLINQProgJoining#7](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/Joins/joins.cs#7)]  
  
## 編譯程式碼  
  
-   在 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] 中建立一個新的主控台應用程式。  
  
-   將參考加入至 System.Core.dll \(如果尚未參考\)。  
  
-   包括 <xref:System.Linq> 命名空間。  
  
-   複製和貼上此範例的程式碼放入 program.cs 檔，包含 `Program` 類別之 `Main` 方法的下方。  將程式碼新增至 `Main` 方法呼叫 `LeftOuterJoinExample` 方法。  
  
-   執行程式。  
  
## 請參閱  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [如何：執行內部聯結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [如何：執行群組連結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)