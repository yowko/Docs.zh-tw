---
redirect_url: /dotnet/articles/csharp/linq/perform-grouped-joins
caps.handback.revision: 23
---
# 如何：執行群組聯結 (C# 程式設計手冊)
群組聯結對產生階層式資料結構相當有用。  它會將第一個集合的每個項目與第二個集合的相關項目組進行配對。  
  
 例如，名為 Student 的類別或關聯式資料庫資料表可能包含兩個欄位：\[ID\] 和 \[名稱\]。  名為 Course 的第二個類別或關聯式資料庫資料表可能包含兩個欄位：\[StudentId\] 和 \[CourseTitle\]。  這兩個資料來源的群組聯結會根據相符的 Student.Id 和 Course.StudentId，將每個 Student 與 Course 物件集合 \(可能是空的\) 群組在一起。  
  
> [!NOTE]
>  無論是否在第二個集合中找到相關項目，第一個集合的每個項目都會顯示在群組聯結的結果集中。  在沒有找到相關項目的情況下，該項目的相關項目序列是空的。  結果選取器因此可以存取第一個集合的每個項目。  這與無群組聯結的結果選取器不同，如果在第二個集合中沒有相符項目，該選取器就無法存取第一個集合中的項目。  
  
 本主題中的第一個範例顯示如何執行群組聯結。  第二個範例顯示如何使用群組聯結建立 XML 項目。  
  
## 範例  
  
### 群組聯結範例  
 下列範例根據符合 `Pet.Owner` 屬性的 `Person`，執行型別 `Person` 和 `Pet` 之物件的群組聯結。  不像無群組聯結會產生每個相符項目的配對，群組聯結只會針對第一個集合的每個項目產生一個結果物件，在此範例中為 `Person` 物件。  第二個集合的對應項目 \(在此範例中為 `Pet` 物件\) 會群組至集合。  最後，結果選取器函式會針對由 `Person.FirstName` 和 `Pet` 物件集合組成的每個相符項目建立匿名型別。  
  
 [!code-cs[CsLINQProgJoining#5](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-grouped-joins_1.cs)]  
  
## 範例  
  
### 建立 XML 範例的群組聯結  
 群組聯結適合用於使用 [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 建立 XML。  下列範例類似於前述範例，除了結果選取器函式不是建立匿名型別，而是建立代表聯結物件的 XML 項目。  如需 [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 的詳細資訊，請參閱 [LINQ to XML](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)。  
  
 [!code-cs[CsLINQProgJoining#6](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-grouped-joins_2.cs)]  
  
## 編譯程式碼  
  
-   在 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] 中建立 \[**主控台應用程式**\] 專案。  
  
-   如果未參考 System.Core.dll 和 System.Xml.Linq.dll，請加入參考。  
  
-   包含 <xref:System.Linq> 和 <xref:System.Xml.Linq> 命名空間。  
  
-   從範例複製程式碼，並將其貼入 program.cs 檔中 `Main` 方法的下方。  將一行程式碼加入至 `Main` 方法，以呼叫您所貼上的方法。  
  
-   執行程式。  
  
## 請參閱  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [如何：執行內部聯結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [如何：執行左外部連結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [LINQ to XML](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)   
 [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)