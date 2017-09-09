---
title: "隱含型別區域變數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: 23
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 59bb61d8dd530e87f342d38acb131fab5e25febf
ms.lasthandoff: 03/13/2017

---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>隱含類型區域變數 (C# 程式設計手冊)
您可以為區域變數指定 `var` 的推斷「類型」，而不是明確類型。 `var` 關鍵字會指示編譯器從初始化陳述式右側的運算式推斷變數的類型。 推斷類型可能是內建類型、匿名型別、使用者定義型別，或 .NET Framework 類別庫中定義的類型。 如需如何使用 `var` 初始化陣列的詳細資訊，請參閱[隱含型別陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。  
  
 下列範例顯示可以使用 `var` 宣告區域變數的各種方法：  
  
 [!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 請務必了解 `var` 關鍵字不代表 "variant"，也不代表變數是不嚴格規定類型或晚期繫結的。 只代表編譯器會判斷並指派最適當的類型。  
  
 `var` 關鍵字可在下列內容中使用：  
  
-   在區域變數 (方法範圍中宣告的變數) 上，如前述範例所示。  
  
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
  
 如需詳細資訊，請參閱[如何：在查詢運算式中使用隱含型別區域變數和陣列](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)。  
  
## <a name="var-and-anonymous-types"></a>var 和匿名型別  
 在許多情況下，使用 `var` 是選擇性的，只是為了在語法上便於使用。 不過，當變數以匿名型別初始化時，如果您稍後需要存取物件的屬性，則必須宣告該變數為 `var`。 這是 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 查詢運算式中的常見案例。 如需詳細資訊，請參閱[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。  
  
 從原始程式碼的觀點來看，匿名型別沒有名稱。 因此，如果已使用 `var` 初始化查詢變數，則存取傳回的物件序列中屬性的唯一方法，就是使用 `var` 作為 `foreach` 陳述式中反覆運算變數的類型。  
  
 [!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a>備註  
 下列限制適用於隱含型別變數宣告：  
  
-   `var` 只能在區域變數於相同的陳述式中宣告和初始化時使用；此變數無法初始化為 null、方法群組或匿名函式。  
  
-   `var` 無法在類別範圍的欄位中使用。  
  
-   使用 `var` 宣告的變數無法在初始化運算式中使用。 換句話說，此運算式是合法的 `: int i = (i = 20);`，但此運算式會產生編譯時期錯誤︰`var i = (i = 20);`  
  
-   無法在相同的陳述式中初始化多個隱含型別變數。  
  
-   如果名為 `var` 的類型在範圍之內，則 `var` 關鍵字會解析成該類型名稱，而且不會視為隱含型別區域變數宣告的一部分。  
  
 您會發現在難以判斷查詢運算式中查詢變數的確切建構類型時，`var` 也相當有用。 這會在群組與排序作業時發生。  
  
 當您不想要老是在鍵盤上鍵入變數的特定類型，或是此特定類型很明顯或不會增加程式碼的可讀性時，`var` 關鍵字也相當有用。 `var` 有用的其中一個範例是用於巢狀泛型型別時，例如用於群組作業的類型。 在下列查詢中，查詢變數的類型是 `IEnumerable<IGrouping<string, Student>>`。 只要您及維護程式碼的其他使用者了解這點，為求便利和簡潔而使用隱含型別就不會有問題。  
  
 [!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 無論如何，使用 `var` 都可能會使您的程式碼對其他開發人員而言更難以了解。 基於這個理由，C# 文件通常只有在必要時才會使用 `var`。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [隱含型別陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)   
 [如何：在查詢運算式中使用隱含型別區域變數和陣列](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)   
 [匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [for](../../../csharp/language-reference/keywords/for.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)
