---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: ba09bdbc35779afba3dd24f6352cb99a49f931c8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583048"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
指定可以讀取但不能寫入變數或屬性。

## <a name="remarks"></a>備註

## <a name="rules"></a>規則

- **宣告內容。** 您只能在模組層級使用 `ReadOnly`。 這表示 `ReadOnly` 元素的宣告內容必須是類別、結構或模組，而且不能是原始程式檔、命名空間或程式。

- **合併的修飾詞。** 您不能在相同的宣告中同時指定與 `Static` `ReadOnly`。

- **指派值。** 使用 `ReadOnly` 屬性的程式碼無法設定其值。 但可存取基礎儲存體的程式碼可以隨時指派或變更此值。

     您只能在其宣告中，或在其定義所在之類別或結構的函式中，將值指派給 `ReadOnly` 變數。

## <a name="when-to-use-a-readonly-variable"></a>使用 ReadOnly 變數的時機

在某些情況下，您無法使用[Const 語句](../../../visual-basic/language-reference/statements/const-statement.md)來宣告和指派常數值。 例如，`Const` 語句可能不會接受您想要指派的資料類型，或者您可能無法在編譯時期使用常數運算式來計算該值。 您甚至可能不知道編譯時間的值。 在這些情況下，您可以使用 `ReadOnly` 變數來保存常數值。

> [!IMPORTANT]
> 如果變數的資料類型是參考型別（例如陣列或類別實例），即使變數本身 `ReadOnly`，也可以變更其成員。 下列範例將說明這點。

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

當初始化時，由 `characterArray()` 指向的陣列會保留 "x"、"y" 和 "z"。 因為變數 `characterArray` 是 `ReadOnly`，所以在初始化之後，您就無法變更它的值;也就是說，您無法為它指派新的陣列。 不過，您可以變更一個或多個陣列成員的值。 呼叫程式 `ChangeArrayElement` 之後，`characterArray()` 所指向的陣列會保留 "x"、"M" 和 "z"。

請注意，這類似于將程式參數宣告為[ByVal](byval.md)，這可防止程式變更呼叫引數本身，但允許它變更其成員。

## <a name="example"></a>範例

下列範例會針對雇用員工的日期定義 `ReadOnly` 屬性。 類別會在內部將屬性值儲存為 `Private` 變數，而且只有類別內的程式碼可以變更該值。 不過，屬性是 `Public`，而且任何可存取類別的程式碼都可以讀取屬性。

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

`ReadOnly` 修飾詞可用於以下內容：

- [Dim 陳述式](../statements/dim-statement.md)
- [Property 陳述式](../statements/property-statement.md)

## <a name="see-also"></a>請參閱

- [WriteOnly](writeonly.md)
- [關鍵字](../keywords/index.md)
