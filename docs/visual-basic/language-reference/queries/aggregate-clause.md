---
title: "Aggregate Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryAggregateIn"
  - "vb.QueryAggregate"
  - "vb.QueryAggregateInto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Aggregate clause"
  - "Aggregate statement"
  - "queries [Visual Basic], Aggregate"
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# Aggregate Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

將一個或多個彙總函式 \(Aggregate Function\) 套用至集合。  
  
## 語法  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`element`|必要項。  用來逐一查看集合項目的變數。|  
|`type`|選擇項。  `element` 的型別。  如果未指定型別，則會從 `collection` 推斷 `element` 的型別。|  
|`collection`|必要項。  參考要操作的集合。|  
|`clause`|選擇項。  一個或多個查詢子句，例如 `Where` 子句，以限定套用 Aggregate 子句的查詢結果。|  
|`expressionList`|必要項。  一個或多個以逗號分隔的運算式，會識別套用至集合的彙總函式。  您可以將別名 \(Alias\) 套用至彙總函式以指定查詢結果的成員名稱。  如果未提供別名，則會使用彙總函式的名稱。  如需範例，請參閱本主題稍後關於彙總函式的章節。|  
  
## 備註  
 `Aggregate` 子句可以用來將彙總函式包含在查詢中。  彙總函式會對值集執行檢查及計算，並傳回單一值。  您可以使用查詢結果型別的成員來存取計算值。  您可以使用的標準彙總函式為 `All`, `Any`、`Average`、`Count`、`LongCount`、`Max`、`Min` 及 `Sum` 函式。  熟悉 SQL 中彙總的開發人員，一定都熟悉這些函式。  本主題的下列章節會加以說明。  
  
 彙總函式的結果包含在查詢結果中，做為查詢結果型別的欄位。  您可以套用彙總函式結果的別名，以指定會保留彙總值之查詢結果型別之成員名稱。  如果未提供別名，則會使用彙總函式的名稱。  
  
 `Aggregate` 子句可以用來開始查詢，也可以包含在查詢中做為額外子句。  如果 `Aggregate` 子句用來開始查詢，則結果會是單一值，此值是 `Into` 子句中指定之彙總函式的結果。  如果在 `Into` 子句中指定一個以上的彙總函式，查詢會傳回具有個別屬性的單一型別，以參考 `Into` 子句中每個彙總函式的結果。  如果將 `Aggregate` 子句做為查詢中的額外子句，則查詢集合中傳回的型別會有個別的屬性，用以參考 `Into` 子句中每個彙總函式的結果。  
  
## 彙總函式  
 下列清單描述可以與 `Aggregate` 子句一起使用的標準彙總函式。  
  
|||  
|-|-|  
|Function|描述|  
|`All`|如果集合中的所有項目都滿足指定的條件則傳回 `true`，否則會傳回 `false`。  下列為範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|如果集合中的任何項目滿足指定的條件則傳回 `true`，否則會傳回 `false`。  下列為範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|計算集合中所有項目的平均值，或計算針對集合中所有項目而提供的運算式。  下列為範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|計算集合中的項目數。  您可以提供選擇性的 `Boolean` 運算式，只計算集合中滿足條件的項目數。  下列為範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|參考 `Group By` 或 `Group Join` 子句之群組結果的查詢結果。  `Group` 函式只有在 `Group By` 或 `Group Join` 子句的 `Into` 子句中才有效。  如需詳細資訊與範例，請參閱 [Group By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)與 [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)。|  
|`LongCount`|計算集合中的項目數。  您可以提供選擇性的 `Boolean` 運算式，只計算集合中滿足條件的項目數。  傳回 `Long` 的結果。  如需範例，請參閱 `Count` 彙總函式。|  
|`Max`|計算集合的最大值，或計算針對集合中所有項目而提供的運算式。  下列為範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|計算集合的最小值，或計算針對集合中所有項目而提供的運算式。  下列為範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|計算集合中所有項目的總和，或計算針對集合中所有項目而提供的運算式。  下列為範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## 範例  
 下列程式碼範例顯示如何使用 `Aggregate` 子句將彙總函式套用至查詢結果。  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## 建立使用者定義的彙總函式  
 您可以在查詢運算式中包含自己的自訂彙總函式，方法是將擴充方法加入至 <xref:System.Collections.Generic.IEnumerable%601> 型別。  接著，您的自訂方法就可以在參考您的彙總函式的可列舉集合上，執行計算或作業。  如需擴充方法的詳細資訊，請參閱[擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
 例如，下列程式碼範例顯示用於計算數值集合中間值的自訂彙總函式。  `Median` 擴充方法有兩個多載。  第一個多載會接受型別 `IEnumerable(Of Double)` 的集合，做為輸入。  如果 `Median` 彙總函式是針對型別 `Double` 的查詢欄位進行呼叫，就會呼叫此方法。  `Median` 方法的第二個多載可以傳遞任何泛型型別。  `Median` 方法的泛型多載會採用第二個參數，該參數參考 `Func(Of T, Double)` Lambda 運算式，將型別的值 \(根據集合\) 投射為型別 `Double` 的對應值。  接著將中間值的計算委派 \(Delegate\) 至 `Median` 方法的其他多載。  如需 Lambda 運算式的詳細資訊，請參閱 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 下列程式碼範例顯示在型別 `Integer` 的集合和型別 `Double` 的集合上，呼叫 `Median` 彙總函式的範例查詢。  在型別 `Double` 的集合上呼叫 `Median` 彙總函式的查詢會呼叫 `Median` 方法的多載，接受型別 `Double` 的集合以做為輸入。  在型別 `Integer` 的集合上呼叫 `Median` 彙總函式的查詢，則會呼叫 `Median` 方法的泛型多載。  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Group By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)