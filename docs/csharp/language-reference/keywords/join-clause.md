---
title: "join 子句 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "join"
  - "join_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "join 子句 [C#]"
  - "join 關鍵字 [C#]"
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# join 子句 (C# 參考)
`join` 子句在使物件模型中沒有直接關係之不同來源序列的項目產生關聯上相當有用。  唯一的需求是每個來源的項目都共用可以比較相等性的某些值。  例如，食品經銷商可能有特定產品供應商的清單，以及買家的清單。  舉例來說，使用 `join` 子句可以建立特定區域中某產品的供應商和買家清單。  
  
 `join` 子句會採用兩個來源序列做為輸入。  每個序列的項目必須是屬性或包含屬性，該屬性可以與其他序列中的對應屬性做比較。  `join` 子句使用特殊的 `equals` 關鍵字比較指定索引鍵的相等性。  `join` 子句執行的所有聯結是等聯結 \(Equijoin\)。  `join` 子句輸出的形狀取決於您執行之聯結的特定類型。  以下是三種最常見的聯結類型：  
  
-   內部聯結  
  
-   群組聯結  
  
-   左外部聯結  
  
## 內部聯結  
 下列範例顯示簡單的內部等聯結。  這個查詢會產生「產品名稱\/分類」配對的一般序列。  相同分類字串會顯示在多個項目中。  如果 `categories` 的項目沒有相符的 `products`，該分類不會顯示在結果中。  
  
 [!code-cs[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_1.cs)]  
  
 如需詳細資訊，請參閱 [如何：執行內部聯結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)。  
  
## Group Join  
 具有 `into` 運算式的 `join` 子句稱為群組聯結。  
  
 [!code-cs[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_2.cs)]  
  
 群組聯結會產生階層式結果序列，使左側來源序列中的項目與右側來源序列中的一個或多個相符項目產生關聯。  群組聯結從關聯式角度來看沒有對等項目，它基本上是物件陣列的序列。  
  
 如果右側來源序列中找不到項目會符合左側來源的項目，`join` 子句會針對該項目產生空的陣列。  因此，群組聯結基本上仍然是內部等聯結，例外為結果序列會組織成群組。  
  
 如果您只選取群組聯結的結果，便可以存取項目，但是無法識別符合的索引鍵。  因此，通常在將群組聯結的結果選取至也具有索引鍵名稱的新類型時較為有用，如前述範例所示。  
  
 當然，您也可以使用群組聯結的結果做為其他子查詢的產生器：  
  
 [!code-cs[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_3.cs)]  
  
 如需詳細資訊，請參閱 [如何：執行群組連結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)。  
  
## 左外部聯結  
 在左外部聯結中，會傳回左來源序列中的所有項目，即使在右序列中沒有相符項目也是如此。  若要在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 中執行左外部聯結，請使用 `DefaultIfEmpty` 方法與群組聯結的組合，指定如果左側項目沒有相符項目時產生預設右側項目。  您可以使用 `null` 做為任何參考型別的預設值，或者可以指定使用者定義的預設型別。  在下列範例中，會顯示使用者定義的預設型別：  
  
 [!code-cs[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_4.cs)]  
  
 如需詳細資訊，請參閱 [如何：執行左外部連結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)。  
  
## 等於運算子  
 `join` 子句會執行等聯結。  也就是說，您只能根據兩個索引鍵的相等性進行比對。  不支援其他類型的比較，例如 "greater than" 或 "not equals"。  為了釐清所有聯結都是等聯結，`join` 子句使用 `equals` 關鍵字而非 `==` 運算子。  `equals` 關鍵字只能用在 `join` 子句，而且與 `==` 運算子有一個重要的差異。  使用 `equals`，則左索引鍵會使用外部來源序列，而右索引鍵會使用內部來源。  外部來源只在 `equals` 的左側範圍中，而內部來源序列只在右側範圍中。  
  
## 非等聯結  
 您可以執行非等聯結、交叉聯結及其他自訂聯結作業，方法是使用多個 `from` 子句單獨將新序列引入查詢。  如需詳細資訊，請參閱 [如何：執行自訂聯結作業](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)。  
  
## 物件集合上的聯結和關聯式資料表  
 在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 查詢運算式中，聯結作業是在物件集合上執行。  物件集合不能用與兩個關聯式資料表完全相同的方法進行「聯結」。  在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 中，只有當兩個來源序列沒有由任何關聯性繫結時，才需要明確 `join` 子句。  使用 [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] 時，外部索引鍵資料表在物件模型中會表示為主要資料表的屬性。  例如，在 Northwind 資料庫中，Customer 資料表與 Orders 資料表有外部索引鍵的關係。  當您將資料表對應至物件模型時，Customer 類別有 Orders 屬性，該屬性包含與 Customer 相關聯之 Orders 的集合。  實際上，您的聯結就已完成。  
  
 如需在 [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] 內容中查詢所有關聯資料表的詳細資訊，請參閱 [HOW TO：對應資料庫關聯性](../Topic/How%20to:%20Map%20Database%20Relationships.md)。  
  
## 複合索引鍵  
 您可以使用複合索引鍵測試多個值的相等性。  如需詳細資訊，請參閱 [如何：使用複合索引鍵執行聯結](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)。  複合索引鍵也可以用於 `group` 子句。  
  
## 範例  
 下列範例使用相同的相符索引鍵，比較相同資料來源上的內部聯結、群組聯結及左外部聯結的結果。  部分額外程式碼會加入至這些範例以釐清主控台顯示中的結果。  
  
 [!code-cs[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_5.cs)]  
  
## 備註  
 後面沒有 `into` 的 `join` 子句會轉譯成 <xref:System.Linq.Enumerable.Join%2A> 方法呼叫。  後面有 `into` 的 `join` 子句會轉譯成 <xref:System.Linq.Enumerable.GroupJoin%2A> 方法呼叫。  
  
## 請參閱  
 [查詢關鍵字 \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [group 子句](../../../csharp/language-reference/keywords/group-clause.md)   
 [如何：執行左外部連結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [如何：執行內部聯結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [如何：執行群組連結](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [如何：排序 Join 子句的結果](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)   
 [如何：使用複合索引鍵執行聯結](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)   
 [如何：安裝範例資料庫](../Topic/How%20to:%20Install%20Sample%20Databases.md)