---
title: "var (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2a96d1c8869edd96cec913f1a868bcc3253dd14f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="var-c-reference"></a>var (C# 參考)
從 Visual C# 3.0 開始，在方法範圍內宣告的變數可以使用隱含的「類型」`var`。 隱含型別區域變數如同您自己宣告的類型一樣是強型別，但是編譯器會判斷類型。 下列兩個 `i` 宣告的功能相同：  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 如需詳細資訊，請參閱 [隱含類型區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和 [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。  
  
## 範例  
 下列範例顯示兩個查詢運算式。  在第一個運算式中，因為查詢結果的型別可以明確陳述為 `IEnumerable<string>`，所以允許使用 `var`，但不需要這麼做。  而在第二個運算式中，因為結果是匿名型別的集合，而且只有編譯器 \(Compiler\) 才可以存取該型別的名稱，所以必須使用 `var`。  請注意，在第二個範例中，`foreach` 反覆運算變數 `item` 也必須是隱含型別。  
  
 [!code-cs[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [隱含類型區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
