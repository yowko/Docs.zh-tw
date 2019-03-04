---
title: 作法：在結構之間實作使用者定義的轉換 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: bc792562b4849d402e03328e50dedac030520011
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201140"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>作法：在結構之間實作使用者定義的轉換 (C# 程式設計指南)
這個範例會定義兩個結構 `RomanNumeral` 和 `BinaryNumeral`，並示範它們的轉換。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideStatements#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#13)]  
  
## <a name="robust-programming"></a>穩固程式設計  
  
-   上例中，陳述式：  
  
     [!code-csharp[csProgGuideStatements#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#14)]  
  
     執行從 `RomanNumeral` 到 `BinaryNumeral` 的轉換。 因為沒有直接從 `RomanNumeral` 轉換至 `BinaryNumeral`，所以使用 cast 從 `RomanNumeral` 轉換成 `int`，再使用另一個 cast 從 `int` 轉換成 `BinaryNumeral`。  
  
-   也是陳述式  
  
     [!code-csharp[csProgGuideStatements#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#15)]  
  
     執行從 `BinaryNumeral` 到 `RomanNumeral` 的轉換。 因為 `RomanNumeral` 定義 `BinaryNumeral` 的隱含轉換，所以不需要任何轉換。  
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
