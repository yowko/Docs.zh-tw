---
title: "如何：在結構之間實作使用者定義的轉換 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d86cbd48347e6951f6b6883a385d80d68697c9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
