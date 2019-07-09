---
title: 運算子 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 551d4cd8bf26a1c1caf3cbf611d9f338ae2581be
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609509"
---
# <a name="operators-c-programming-guide"></a>運算子 (C# 程式設計手冊)

在 C# 中，「 *運算子* 」(Operator) 是程式的元素，這類元素會套用至運算式或陳述式中的一個或多個「 *運算元* 」(Operand)。 只使用一個運算元的運算子稱為`++`「一元」 `new`(Unary) 運算子，例如遞增運算子 ( *) 或* 。 使用兩個運算元的運算子稱為`+`「二元」`-`(Binary) 運算子，例如算術運算子 (`*`、`/`、 *及* )。 還有一種運算子稱為條件運算子 (`?:`)，它會使用三個運算元而且是 C# 中唯一的三元運算子。  
  
 下列 C# 陳述式包含一個一元運算子和一個運算元。 遞增運算子 `++`會修改運算元 `y`的值。  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 下列 C# 陳述式包含兩個二元運算子，這兩個運算子各有兩個運算元。 指派運算子 `=`的運算元為整數變數 `y` 和運算式 `2 + 3` 。 運算式 `2 + 3` 本身包含加法運算子和兩個運算元 `2` 和 `3`。  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
運算元可以是由任何長度的程式碼撰寫而成的有效運算式，而且可以包含任何數量的子運算式。 在包含多個運算子的運算式中，套用運算子的順序取決於「 *運算子優先順序*」(Operator Precedence)、「 *順序關聯性*」(Associativity) 以及括號。  

## <a name="operator-precedence"></a>運算子優先順序
  
每個運算子都有定義的優先順序。 在包含多個運算子且運算子具有不同優先順序層級的運算式中，運算子的優先順序決定評估運算子的順序。 例如，下列陳述式會將 3 指派給 `n1`：

```csharp
n1 = 11 - 2 * 4;
```

因為乘法的優先順序高於減法，所以會先執行乘法。

如需按優先順序層級排序的 C# 運算子完整清單，請參閱 [C# 運算子](../../language-reference/operators/index.md)。
  
## <a name="associativity"></a>順序關聯性

 當運算式中有兩個以上具有相同優先順序的運算子時，會根據順序關聯性評估這些運算子。 左向關聯運算子會依由左至右的順序進行評估。 例如， `x * y / z` 會判斷值為 `(x * y) / z`。 右向關聯運算子會依由右至左的順序進行評估。 例如，指派運算子就是右向關聯。 如果不是的話，下列程式碼將會產生錯誤。  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 另一個範例是右向關聯的三元運算子 ([?:](../../../csharp/language-reference/operators/conditional-operator.md))。 大部分的二元運算子都是左向關聯。  
  
 不論運算式中的運算子是左向關聯還是右向關聯，都會由左至右先行評估每個運算式的運算元。 下列範例將說明運算子和運算元的評估順序。  
  
|陳述式|評估的順序|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>加入括號

 您可以使用括號變更運算子優先順序和順序關聯性強制執行的順序。 例如， `2 + 3 * 2` 正常情況下會判斷值為 8，這是因為乘法類運算子的優先順序高於加法類運算子。 但是，如果您將運算式撰寫為 `(2 + 3) * 2`，則會先評估加法再評估乘法，而得到的結果會是 10。 下列範例將說明以括號括住之運算式中的評估順序。 如先範例所示，套用運算子之前會先評估運算元。  
  
|陳述式|評估的順序|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>運算子多載

您可以定義自訂類別和結構的某些運算子行為。 這個程序稱為「 *運算子多載*」(Operator Overloading)。 如需詳細資訊，請參閱[運算子多載](../../language-reference/operators/operator-overloading.md)。
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [陳述式、運算式和運算子](index.md)
- [C# 運算子](../../language-reference/operators/index.md)
