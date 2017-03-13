---
title: "如何：在查詢中使用 Lambda 運算式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Lambda 運算式 [C#], 在 LINQ 中"
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 如何：在查詢中使用 Lambda 運算式 (C# 程式設計手冊)
您不會在查詢語法中直接使用 Lambda 運算式，而是在方法呼叫中使用它們，因此查詢運算式可以包含方法呼叫。  事實上，某些查詢作業只能以方法語法來表示。  如需關於查詢語法與方法語法之間差異的詳細資訊，請參閱[Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。  
  
## 範例  
 下列範例會示範如何透過利用 <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> 標準查詢運算子，在方法架構的查詢中使用 Lambda 運算式。  請注意，在此範例中的 <xref:System.Linq.Enumerable.Where%2A> 方法具有委派型別 \(Delegate Type\) <xref:System.Func%601> 的輸入參數，而且該委派會接受整數做為輸入並傳回布林值 \(Boolean\)。  Lambda 運算式可以轉換為該委派。  如果這是使用 <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName> 方法的 [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] 查詢，參數型別就會是 `Expression<Func\<int,bool>>`，不過 Lambda 運算式看起來會完全相同。  如需運算式型別的詳細資訊，請參閱 <xref:System.Linq.Expressions.Expression?displayProperty=fullName>。  
  
 [!code-cs[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## 範例  
 下列範例會示範如何在查詢運算式的方法呼叫中使用 Lambda 運算式。  因為使用查詢語法時無法叫用 <xref:System.Linq.Enumerable.Sum%2A> 標準查詢運算子，所以這時必須使用 Lambda。  
  
 此查詢會先根據學生的年級 \(已定義於 `GradeLevel` 列舉\) 來進行分組。  接著，針對每一組加總計算每個學生的總分數。  這個作業需要兩個 `Sum` 運算。  內部的 `Sum` 會計算每個學生的總分數，而外部的 `Sum` 會不斷執行，以加總該組中所有學生的總分數。  
  
 [!code-cs[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## 編譯程式碼  
 若要執行這段程式碼，請將此方法複製並貼入 [如何：查詢物件集合](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) 中所提供的 `StudentClass`，並且從 `Main` 方法來呼叫該方法。  
  
## 請參閱  
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)