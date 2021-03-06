---
title: 二進位 'If' 運算式的第一個運算元必須可為 Null 或是參考類型
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: bca9b74a68815b4e5a3bb2dc114b9031cdf24099
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162735"
---
# <a name="bc33107-first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>BC33107：二元 ' If ' 運算式中的第一個運算元必須可為 null 或參考型別

`If`運算式可採用兩個或三個引數。 當您只傳送兩個引數時，第一個引數必須是參考型別或可為 null 的實值型別。 如果第一個引數評估為以外的任何 `Nothing` 值，則會傳回其值。 如果第一個引數評估為 `Nothing` ，則會評估並傳回第二個引數。

 例如，下列程式碼包含兩個 `If` 運算式，一個具有三個引數，另一個包含兩個引數。 運算式會計算並傳回相同的值。

```vb
' firstChoice is a nullable value type.
Dim firstChoice? As Integer = Nothing
Dim secondChoice As Integer = 1128
' If expression with three arguments.
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))
' If expression with two arguments.
Console.WriteLine(If(firstChoice, secondChoice))
```

 下列運算式會導致此錯誤：

```vb
Dim choice1 = 4
Dim choice2 = 5
Dim booleanVar = True

' Not valid.
'Console.WriteLine(If(choice1 < choice2, 1))
' Not valid.
'Console.WriteLine(If(booleanVar, "Test returns True."))
```

 **錯誤識別碼：** BC33107

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果您無法變更程式碼，讓第一個引數是可為 null 的實值型別或參考型別，請考慮轉換成三個引數 `If` 運算式或 `If...Then...Else` 語句。

```vb
Console.WriteLine(If(choice1 < choice2, 1, 2))
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))
```

## <a name="see-also"></a>另請參閱

- [If 運算子](../operators/if-operator.md)
- [If...Then...Else 陳述式](../statements/if-then-else-statement.md)
- [可為 null 的實數值型別](../../programming-guide/language-features/data-types/nullable-value-types.md)
