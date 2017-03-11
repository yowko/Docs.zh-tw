---
title: "如何：在查詢運算式中使用隱含類型區域變數和陣列 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "隱含類型區域變數 [C#], 使用方法"
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 如何：在查詢運算式中使用隱含類型區域變數和陣列 (C# 程式設計手冊)
只要您想要編譯器判斷區域變數的型別，就可以使用隱含型別區域變數。  您必須使用隱含型別區域變數來儲存匿名型別，這些型別經常在查詢運算式中使用。  下列範例顯示在查詢中選擇性和必要的隱含型別區域變數用法。  
  
 隱含型別區域變數是使用 [var](../../../csharp/language-reference/keywords/var.md) 內容關鍵字宣告。  如需詳細資訊，請參閱[隱含類型區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) 和[隱含類型陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。  
  
## 範例  
 下列範例說明必須使用 `var` 關鍵字的常見情節：產生匿名型別序列的查詢運算式。  在此情節中，`foreach` 陳述式中的查詢變數和反覆運算變數必須使用 `var` 設為隱含型別，因為您未具備存取匿名型別之型別名稱的權限。  如需匿名型別的詳細資訊，請參閱[匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。  
  
 [!code-cs[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#32)]  
  
## 範例  
 下列範例會在類似的情況中使用 `var` 關鍵字，但是在這個情況中，`var` 是選用的。  因為 `student.LastName` 是字串，所以執行查詢會傳回字串序列。  因此，`queryID` 的型別可以宣告為 `System.Collections.Generic.IEnumerable<string>` 而不是 `var`。  使用 `var` 關鍵字的目的在於方便性。  在此範例中，`foreach` 陳述式中的反覆運算變數會明確設為字串型別，但是也可以使用 `var` 宣告。  因為反覆運算變數的型別不是匿名型別，所以 `var` 是選用的，並非必要。  請記住，`var` 本身不是型別，而是讓編譯器推斷及指派型別的指示。  
  
 [!code-cs[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#33)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)