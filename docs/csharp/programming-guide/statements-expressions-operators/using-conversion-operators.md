---
title: 使用轉換運算子 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: 17a722f7160ae9cd03caa2dff9c4436fcf0f9d9e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45593695"
---
# <a name="using-conversion-operators-c-programming-guide"></a>使用轉換運算子 (C# 程式設計手冊)
您可以使用比較容易上手的 `implicit` 轉換運算子，或者使用可以向任何人清楚指出您要轉換程式碼的 `explicit` 轉換運算子。 本主題將示範這兩種類型的轉換運算子。  
  
> [!NOTE]
>  如需簡單類型轉換的資訊，請參閱[如何：將字串轉換為數值](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)、[如何：將位元組陣列轉換成整數](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)、[如何：在十六進位字串和數字類型間轉換](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)或 <xref:System.Convert>。  
  
## <a name="example"></a>範例  
 這是明確轉換運算子範例。 這個運算子會從 <xref:System.Byte> 類型轉換成稱為 `Digit` 的實值型別。 因為並非所有位元組都可以轉換成數字，所以會明確進行轉換，這表示必須使用轉型，如 `Main` 方法所示。  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a>範例  
 此範例透過定義可復原上一個範例所執行作業的轉換運算子來示範隱含轉換運算子：它會從稱為 `Digit` 的實值類別轉換成整數 <xref:System.Byte> 類型。 因為任何數字都可以轉換成 <xref:System.Byte>，所以不需要強制使用者進行明確轉換。  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
- [is](../../../csharp/language-reference/keywords/is.md)
