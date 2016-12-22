---
title: "How to: Combine Data with LINQ by Using Joins (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [LINQ in Visual Basic], joins"
  - "joins [LINQ in Visual Basic]"
  - "Join clause [LINQ in Visual Basic]"
  - "Group Join clause [Visual Basic]"
  - "joining [LINQ in Visual Basic]"
  - "queries [LINQ in Visual Basic], how-to topics"
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Combine Data with LINQ by Using Joins (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Visual Basic 提供 `Join` 和 `Group Join` 查詢子句，可以讓您根據集合之間的共同值合併多個集合的內容。  這些值又稱為「*索引鍵*」\(Key\) 值。  熟悉關聯式資料庫概念的開發人員會發現，`Join` 子句就是 INNER JOIN，而 `Group Join` 子句其實就是 LEFT OUTER JOIN。  
  
 本主題中的範例會示範幾個使用 `Join` 和 `Group Join` 查詢子句來合併資料的方法。  
  
## 建立專案和加入範例資料  
  
#### 若要建立含有範例資料和型別的專案  
  
1.  若要執行本主題中的範例，請開啟 Visual Studio 並加入新的 Visual Basic 主控台應用程式專案。  按兩下 Visual Basic 建立的 Module1.vb 檔案。  
  
2.  本主題中的範例使用 `Person` 和 `Pet` 型別，以及下列程式碼範例中的資料。  請將這個程式碼複製至 Visual Basic 建立的預設 `Module1` 模組中。  
  
     [!CODE [VbLINQHowTos#1](../CodeSnippet/VS_Snippets_VBCSharp/VbLINQHowTos#1)]  
    [!CODE [VbLINQHowTos#2](../CodeSnippet/VS_Snippets_VBCSharp/VbLINQHowTos#2)]  
  
## 使用 Join 子句執行內部聯結  
 INNER JOIN 會將兩個集合中的資料合併。  符合指定之索引鍵值的項目都會加入。  兩個集合中無法互相符合的項目則會遭排除。  
  
 在 Visual Basic 中，LINQ 提供兩個執行 INNER JOIN 的選項，即隱含聯結 \(Implicit Join\) 和明確聯結 \(Explicit Join\)。  
  
 隱含聯結在 `From` 子句中指定要聯結 \(Join\) 的集合，並在 `Where` 子句中識別符合的索引鍵欄位。  Visual Basic 會根據指定的索引鍵欄位，隱含地聯結兩個集合。  
  
 當您想要明確指定要在聯結中使用的索引鍵欄位時，可以使用 `Join` 子句指定明確聯結。  在此情況下，仍然可以使用 `Where` 子句篩選查詢結果。  
  
#### 若要使用 Join 子句執行內部聯結  
  
1.  將下列程式碼加入至您專案中的 `Module1` 模組，以查看隱含和明確內部聯結 \(Inner Join\) 的範例。  
  
     [!CODE [VbLINQHowTos#4](../CodeSnippet/VS_Snippets_VBCSharp/VbLINQHowTos#4)]  
  
## 使用 Group Join 子句執行左外部聯結  
 LEFT OUTER JOIN 會加入聯結左邊之集合中的所有項目，並且只加入聯結右邊之集合中相符的值。  聯結右邊之集合中的項目若在左邊之集合中沒有相符合的項目，就會自查詢結果中排除。  
  
 `Group Join` 子句實際上會執行 LEFT OUTER JOIN。  一般所謂的 LEFT OUTER JOIN 跟 `Group Join` 子句傳回的結果有個不同點，即 `Group Join` 子句會依照左邊集合中的每個項目，將從聯結右邊集合得到的結果分組。  在關聯式資料庫中，LEFT OUTER JOIN 會傳回未分組的查詢結果，結果中的每個項目在聯結兩端的集合中都有相符合的項目。  也就是說，每當聯結右邊集合中有相符合的項目時，就會重複列出左邊集合中的項目。  當您完成下面的程序後，就會看到大致情形。  
  
 您可以擴充查詢，針對每個分組的查詢結果各傳回一個項目，即可以仿造未分組的形式擷取 `Group Join` 查詢的結果。  若要完成這項作業，您必須確定是在已分組集合的 `DefaultIfEmpty` 方法上執行查詢。  這可確保聯結左邊之集合中的項目即使在右邊之集合中沒有相符合的結果，仍然會包含在查詢結果中。  您可以將程式碼加入至查詢，以在聯結右邊集合中沒有相符合的值時提供預設結果值。  
  
#### 若要使用 Group Join 子句執行左外部聯結  
  
1.  將下列程式碼加入至您專案中的 `Module1` 模組，以查看分組之左外部聯結 \(Left Outer Join\) 和未分組之左外部聯結的範例。  
  
     [!CODE [VbLINQHowTos#3](../CodeSnippet/VS_Snippets_VBCSharp/VbLINQHowTos#3)]  
  
## 使用複合索引鍵執行聯結  
 在比對要聯結之集合中的值時，您可以在 `Join` 或 `Group Join` 子句中使用 `And` 關鍵字，識別要使用的多個索引鍵欄位。  `And` 關鍵字會指定所有已指定的索引鍵欄位都必須相符，才能聯結項目。  
  
#### 若要使用複合索引鍵執行聯結  
  
1.  將下列程式碼加入至您專案中的 `Module1` 模組，以查看使用複合索引鍵之聯結的範例。  
  
     [!CODE [VbLINQHowTos#5](../CodeSnippet/VS_Snippets_VBCSharp/VbLINQHowTos#5)]  
  
## 執行程式碼  
  
#### 若要加入程式碼以執行範例  
  
1.  將您專案中 `Module1` 模組內的 `Sub Main` 取代為下列程式碼，以執行本主題中的範例。  
  
     [!CODE [VbLINQHowTos#6](../CodeSnippet/VS_Snippets_VBCSharp/VbLINQHowTos#6)]  
  
2.  按 F5 執行範例。  
  
## 請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md)   
 [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [使用 LINQ 轉換資料 \(C\#\)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)