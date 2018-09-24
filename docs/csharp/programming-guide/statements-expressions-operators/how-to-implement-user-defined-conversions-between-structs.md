---
title: 如何：在結構之間實作使用者定義的轉換 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: cff85d60c1b59f4d1ca028f8fc02fee5728fa3d6
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46696648"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>如何：在結構之間實作使用者定義的轉換 (C# 程式設計手冊)
這個範例會定義兩個結構 `RomanNumeral` 和 `BinaryNumeral`，並示範它們的轉換。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a>穩固程式設計  
  
-   上例中，陳述式：  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     執行從 `RomanNumeral` 到 `BinaryNumeral` 的轉換。 因為沒有直接從 `RomanNumeral` 轉換至 `BinaryNumeral`，所以使用 cast 從 `RomanNumeral` 轉換成 `int`，再使用另一個 cast 從 `int` 轉換成 `BinaryNumeral`。  
  
-   也是陳述式  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     執行從 `BinaryNumeral` 到 `RomanNumeral` 的轉換。 因為 `RomanNumeral` 定義 `BinaryNumeral` 的隱含轉換，所以不需要任何轉換。  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
