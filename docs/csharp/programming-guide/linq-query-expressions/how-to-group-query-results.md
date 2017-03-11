---
redirect_url: /dotnet/articles/csharp/linq/group-query-results
caps.handback.revision: 19
---
# 如何：分組查詢結果 (C# 程式設計手冊)
群組是 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 的其中一個最強大的功能。  下列範例顯示如何以不同的方式群組資料：  
  
-   使用單一屬性。  
  
-   使用字串屬性的第一個字母。  
  
-   使用計算的數字範圍。  
  
-   使用 Boolean 述詞或其他運算式。  
  
-   使用複合索引鍵。  
  
 此外，最後兩個查詢會將其結果投射至只包含學生姓名的新匿名型別。  如需詳細資訊，請參閱 [group 子句](../../../csharp/language-reference/keywords/group-clause.md)。  
  
## 範例  
 本主題的所有範例都使用下列 Helper 類別和資料來源。  
  
 [!code-cs[csProgGuideLINQ#15](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#15)]  
  
## 範例  
 下列範例顯示如何使用項目的單一屬性做為群組索引鍵，以群組來源項目。  在此案例中，索引鍵是一個 `string`，也就是學生的姓氏。  也可能使用索引鍵的子字串。  群組作業會使用型別的預設相等比較子。  
  
 將下列方法貼至 `StudentClass` 類別。  將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupBySingleProperty()`。  
  
 [!code-cs[csProgGuideLINQ#17](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#17)]  
  
## 範例  
 下列範例顯示如何使用群組索引鍵之物件屬性以外的其他項目，群組來源項目。  在此範例中，索引鍵是學生姓氏的第一個字母。  
  
 將下列方法貼至 `StudentClass` 類別。  將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupBySubstring()`。  
  
 [!code-cs[csProgGuideLINQ#18](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#18)]  
  
## 範例  
 下列範例顯示如何使用數字範圍做為群組索引鍵，來群組來源項目。  然後查詢會將結果投射至匿名型別，該型別只包含學生的姓名及其所屬的百分位數範圍。  使用匿名型別的原因是因為不需要使用完整的 `Student` 物件顯示結果。  `GetPercentile` 是 Helper 函式，會根據學生的平均分數計算百分位數。  此方法會傳回介於 0 和 10 之間的整數。  
  
 [!code-cs[csProgGuideLINQ#50](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#50)]  
  
 將下列方法貼至 `StudentClass` 類別。  將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByRange()`。  
  
 [!code-cs[csProgGuideLINQ#19](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#19)]  
  
## 範例  
 下列範例顯示如何使用 Boolean 比較運算式來群組來源項目。  在此範例中，Boolean 運算式會測試學生的平均測驗分數是否高於 75。  如前述範例所示，結果會投射至匿名型別，因為不需要完整的來源項目。  請注意，匿名型別中的屬性會變成 `Key` 成員上的屬性，並且可以在執行查詢時以名稱存取。  
  
 將下列方法貼至 `StudentClass` 類別。  將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByBoolean()`。  
  
 [!code-cs[csProgGuideLINQ#20](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#20)]  
  
## 範例  
 下列範例顯示如何使用匿名型別，封裝包含多個值的索引鍵。  在此範例中，第一個索引鍵值是學生姓氏的第一個字母。  第二個索引鍵值是 Boolean，指定第一次測驗時學生的分數是否高於 85 分。  您可以依索引鍵中的任何屬性排序群組。  
  
 將下列方法貼至 `StudentClass` 類別。  將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByCompositeKey()`。  
  
 [!code-cs[csProgGuideLINQ#21](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#21)]  
  
## 編譯程式碼  
 將您要測試的每一個方法複製並貼至 `StudentClass` 類別。  將方法的呼叫陳述式加入至 `Main` 方法，然後按 F5。  
  
 在配合應用程式調整這些方法時，請注意，LINQ 需要 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 3.5 或 4 版，而且專案必須包含 System.Core.dll 的參考，以及 System.Linq 的 using 指示詞。  LINQ to SQL、LINQ to XML 和 LINQ to DataSet 型別都需要額外的 using 指示詞和參考。  如需詳細資訊，請參閱 [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)。  
  
## 請參閱  
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.IGrouping%602>   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [group 子句](../../../csharp/language-reference/keywords/group-clause.md)   
 [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [如何：在分組作業上執行子查詢](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)   
 [如何：建立巢狀群組](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)   
 [Grouping Data](../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)