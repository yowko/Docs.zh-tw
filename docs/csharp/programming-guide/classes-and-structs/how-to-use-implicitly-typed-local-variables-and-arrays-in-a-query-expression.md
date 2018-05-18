---
title: 如何：在查詢運算式中使用隱含類型區域變數和陣列 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: c2bc990f9dda4b91928c176cf7f10bfb349ba343
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>如何：在查詢運算式中使用隱含類型區域變數和陣列 (C# 程式設計手冊)
每次您希望編譯器判斷區域變數的類型時，可以使用隱含型別區域變數。 您必須使用隱含型別區域變數來儲存查詢運算式中常用的匿名型別。 下列範例說明在查詢中選擇性使用和必須使用隱含型別區域變數的情況。  
  
 隱含型別區域變數是透過 [var](../../../csharp/language-reference/keywords/var.md) 內容關鍵字宣告。 如需詳細資訊，請參閱[隱含型別區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和[隱含型別陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示需要 `var` 關鍵字的常見案例：產生一系列匿名型別的查詢運算式。 在此案例中，`foreach` 陳述式中的查詢變數和反覆運算變數都必須使用 `var` 來隱含輸入，因為您無法存取匿名型別的類型名稱。 如需匿名型別的詳細資訊，請參閱[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。  
  
 [!code-csharp[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例會在類似情況下使用 `var` 關鍵字，但可選擇是否使用 `var`。 因為 `student.LastName` 是字串，所以執行查詢會傳回一系列的字串。 因此，`queryID` 的類型會宣告為 `System.Collections.Generic.IEnumerable<string>`，而不是 `var`。 關鍵字 `var` 是為了方便起見。 在範例中，`foreach` 陳述式中的反覆運算變數明確輸入為字串，但它可以改為使用 `var` 來宣告。 因為反覆運算變數的類型不是匿名型別，所以使用 `var` 是選項而非需求。 請記住，`var` 本身不是類型，而是編譯器用來推斷和指派類型的指令。  
  
 [!code-csharp[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)
