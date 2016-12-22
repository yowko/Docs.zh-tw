---
title: "如何：執行內部聯結 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "內部聯結 [C# 中的 LINQ]"
  - "聯結 [C#], 內部"
  - "查詢 [C# 中的 LINQ], 聯結"
  - "查詢運算式 [C# 中的 LINQ], 聯結"
ms.assetid: d9edb404-8314-413e-ae51-83bb86c7a4b5
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：執行內部聯結 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在關聯式資料庫詞彙中，「*內部聯結*」\(Inner Join\) 會產生結果集，其中第一個集合的每個項目會針對第二個集合中的每個相符項目顯示一次。  如果第一個集合中的項目沒有相符項目，就不會顯示在結果集中。  在 C\# 中由 `join` 子句呼叫的 <xref:System.Linq.Enumerable.Join%2A> 方法會實作內部聯結。  
  
 本主題會顯示如何執行四種不同的內部聯結：  
  
-   根據簡單索引鍵，使兩個資料來源的項目相互關聯的簡單內部聯結。  
  
-   根據「*複合*」\(Composite\) 索引鍵，使兩個資料來源的項目相互關聯的內部聯結。  複合索引鍵是由一個以上的值組成的索引鍵，可以讓您根據一個以上的屬性相互關聯各個項目。  
  
-   「*多重聯結*」\(Multiple Join\)，在其中後續的聯結作業會互相附加。  
  
-   使用群組聯結實作的內部聯結。  
  
## 範例  
  
## 簡單索引鍵聯結範例  
 下列範例建立兩個集合，包含兩個使用者定義型別 \(`Person` 和 `Pet`\) 的物件。  查詢會在 C\# 中使用 `join` 子句比對 `Person` 物件與 `Pet` 物件 \(其 `Owner` 就是該 `Person`\)。  C\# 中的 `select` 子句會定義結果物件的外觀。  在這個範例中，結果物件是匿名型別，由擁有者的名字和寵物的名稱組成。  
  
 [!code-cs[CsLINQProgJoining#1](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-inner-joins_1.cs)]  
  
 請注意，`LastName` 為 "Huff" 的 `Person` 物件不會顯示在結果集中，因為沒有 `Pet` 物件的 `Pet.Owner` 等於 `Person`。  
  
## 範例  
  
## 複合索引鍵聯結範例  
 並非只根據一個屬性使項目相互關聯，而是可以使用複合索引鍵根據多個屬性比較項目。  若要這麼做，請針對每個集合指定索引鍵選取器函式以傳回匿名型別，該型別是由您要比較的屬性組成。  如果您標示屬性，屬性在每個索引鍵匿名型別中必須有相同的標籤。  屬性也必須以相同順序顯示。  
  
 下列範例使用 `Employee` 物件清單和 `Student` 物件清單，判斷哪位員工同時也是學生。  這些型別都有型別為 <xref:System.String> 的 `FirstName` 和 `LastName` 屬性。  根據每個清單項目建立聯結索引鍵的函式會傳回匿名型別，該型別是由每個項目的 `FirstName` 和 `LastName` 屬性組成。  聯結作業會比較這些複合索引鍵的相等性，並且傳回每個清單之物件的配對，其中名字和姓氏都是相符的。  
  
 [!code-cs[CsLINQProgJoining#2](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-inner-joins_2.cs)]  
  
## 範例  
  
## 多重聯結範例  
 任意數量的聯結作業可以互相附加以執行多重聯結。  C\# 中的每個 `join` 子句都會使指定資料來源與先前聯結的結果相互關聯。  
  
 下列範例建立三個集合：`Person` 物件清單、`Cat` 物件清單及 `Dog` 物件清單。  
  
 C\# 中的第一個 `join` 子句會根據符合 `Cat.Owner` 的 `Person` 物件比對人和貓。  傳回由 `Person` 物件和 `Cat.Name` 組成之匿名型別的序列。  
  
 C\# 中的第二個 `join` 子句會根據由型別 `Person` 的 `Owner` 屬性和動物名稱的第一個字母組成的複合索引鍵，使第一個聯結傳回之匿名型別與所提供狗清單中的 `Dog` 物件相互關聯。  傳回包含每個相符配對之 `Cat.Name` 和 `Dog.Name` 屬性的匿名型別序列。  因為這是內部聯結，只會傳回在第二個資料來源中有相符項目之第一個資料來源中的物件。  
  
 [!code-cs[CsLINQProgJoining#3](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-inner-joins_3.cs)]  
  
## 範例  
  
## 使用群組聯結進行內部聯結的範例  
 下列範例顯示如何使用群組聯結實作內部聯結。  
  
 在 `query1` 中，`Person` 物件清單是根據符合 `Pet.Owner` 屬性的 `Person`，與 `Pet` 物件清單群組聯結。  群組聯結會建立中繼群組的集合，每個群組是由 `Person` 物件和相符 `Pet` 物件的序列組成。  
  
 藉由將第二個 `from` 子句加入至查詢，此序列會結合 \(或簡維\) 至更長的序列。  最後序列之項目的型別是由 `select` 子句指定。  在這個範例中，該型別是匿名型別，由每個相符配對的 `Person.FirstName` 和 `Pet.Name` 屬性組成。  
  
 `query1` 的結果等同於使用 `join` 子句而不使用 `into` 子句執行內部聯結所取得的結果集。  `query2` 變數示範此同等查詢。  
  
 [!code-cs[CsLINQProgJoining#4](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-inner-joins_4.cs)]  
  
## 編譯程式碼  
  
-   在 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] 中建立一個新的主控台應用程式。  
  
-   將參考加入至 System.Core.dll \(如果尚未參考\)。  
  
-   包括 <xref:System.Linq> 命名空間。  
  
-   從範例複製程式碼，並將其貼入 program.cs 檔中 `Main` 方法的下方。  將一行程式碼加入至 `Main` 方法，以呼叫您所貼上的方法。  
  
-   執行程式。  
  
## 請參閱  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [如何：執行群組連結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [如何：執行左外部連結](../Topic/How%20to:%20Perform%20Left%20Outer%20Joins%20\(C%23%20Programming%20Guide\).md)   
 [HOW TO：聯結兩個集合](../Topic/How%20to:%20Join%20Two%20Collections%20\(C%23\)%20\(LINQ%20to%20XML\).md)   
 [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)