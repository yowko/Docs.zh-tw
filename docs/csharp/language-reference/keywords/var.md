---
title: var (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2be56243f9c4ddafb3903d14fa6d6f9cb0e2f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="var-c-reference"></a>var (C# 參考)
從 Visual C# 3.0 開始，在方法範圍內宣告的變數可以使用隱含的「類型」`var`。 隱含型別區域變數如同您自己宣告的類型一樣是強型別，但是編譯器會判斷類型。 下列兩個 `i` 宣告的功能相同：  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 如需詳細資訊，請參閱[隱含型別區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和 [LINQ 查詢作業中的類型關聯性](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。  
  
## <a name="example"></a>範例  
 下例示範兩個查詢運算式。 在第一個運算式中允許使用 `var`，但並非必要，因為查詢結果的類型可以明確陳述為 `IEnumerable<string>`。 不過，在第二個運算式中必須使用 `var`，因為結果是匿名型別的集合，且該類型的名稱只有編譯器本身可以存取。 請注意，在範例 #2 中，`foreach` 反覆運算變數 `item` 必須也是隱含型別。  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [隱含型別區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
