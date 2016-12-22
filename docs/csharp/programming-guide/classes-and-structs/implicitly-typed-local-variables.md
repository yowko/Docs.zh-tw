---
title: "隱含類型區域變數 (C# 程式設計手冊) | Microsoft Docs"
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
  - "隱含類型區域變數 [C#]"
  - "var [C#]"
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 隱含類型區域變數 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

可以給予區域變數推斷「型別」`var`，而非明確型別。  `var` 關鍵字會指示編譯器從初始化陳述式右側的運算式推斷變數的型別。  推斷的型別可能是內建型別、匿名型別、使用者定義型別，或 .NET Framework 類別程式庫中定義的型別。  如需如何使用 `var` 初始化陣列的詳細資訊，請參閱[隱含類型陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。  
  
 下列範例顯示可以用 `var` 宣告區域變數的各種方法：  
  
 [!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 請務必了解 `var` 關鍵字不代表 "variant"，也不代表變數是不嚴格規定型別或晚期繫結的。  只代表編譯器會判斷並指派最適當的型別。  
  
 `var` 關鍵字可在下列內容中使用：  
  
-   在區域變數上 \(方法範圍中宣告的變數\)，如前述範例所示。  
  
-   在 [for](../../../csharp/language-reference/keywords/for.md) 初始化陳述式中。  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   在 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 初始化陳述式中。  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   在 [using](../../../csharp/language-reference/keywords/using-statement.md) 陳述式中。  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 如需詳細資訊，請參閱 [如何：在查詢運算式中使用隱含類型區域變數和陣列](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)。  
  
## var 和匿名型別  
 在許多情況下，使用 `var` 是選擇性的，並且只為了在語法上便於使用。  不過，當變數以匿名型別初始化時，如果您稍後需要存取物件的屬性，則必須宣告該變數為 `var`。  這是 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 查詢運算式中的常見狀況。  如需詳細資訊，請參閱[匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
 從原始程式碼的角度來看，匿名型別沒有名稱。  因此，如果已使用 `var` 初始化查詢變數，則可以存取傳回的物件序列中屬性的唯一方法，就是使用 `var` 做為 `foreach` 陳述式中反覆運算變數的型別。  
  
 [!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## 備註  
 下列限制會套用至隱含型別變數宣告：  
  
-   `var` 只能在區域變數已宣告且在相同陳述式中初始化時使用，變數無法初始化為 null、方法群組或匿名函式。  
  
-   `var` 無法在類別範圍的欄位中使用。  
  
-   使用 `var` 宣告的變數無法在初始化運算式中使用。  換句話說，此運算式是合格的`: int i = (i = 20);`，但此運算式會產生編譯時期錯誤：`var i = (i = 20);`  
  
-   多個隱含型別的變數無法在相同的陳述式中初始化。  
  
-   如果名為 `var` 的型別在範圍中，則 `var` 關鍵字會解析為該型別名稱，而且不會被當做隱含型別區域變數宣告的一部分。  
  
 您會發現在難以判斷查詢運算式中查詢變數的確切建構型別時，`var` 也相當有用。  這會在群組與排序作業時發生。  
  
 當您不想要老是在鍵盤上輸入變數的特定型別、亦或特定型別十分明顯或未加入至程式碼的可讀性時，`var` 關鍵字也相當有用。  `var` 有用的其中一個範例是用於巢狀泛型型別時，例如用於群組作業的型別。  在下列查詢中，查詢變數的型別是 `IEnumerable<IGrouping<string, Student>>`。  只要您和其他必須維護程式碼的人了解，為求便利和簡潔而使用隱含型別就不會有問題。  
  
 [!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 但是，使用 `var` 可能會使您的程式碼對其他開發人員來講更難以了解。  基於這個原因，C\# 文件通常只有在必要時才會使用 `var`。  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [隱含類型陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)   
 [如何：在查詢運算式中使用隱含類型區域變數和陣列](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)   
 [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [LINQ 查詢運算式](../../../visual-basic/reference/command-line-compiler/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [for](../../../csharp/language-reference/keywords/for.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)