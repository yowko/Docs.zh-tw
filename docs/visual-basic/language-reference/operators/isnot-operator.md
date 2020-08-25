---
title: IsNot 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ea978f8874cee20fb3a005189fd846f7564da777
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811037"
---
# <a name="isnot-operator-visual-basic"></a>IsNot 運算子 (Visual Basic)

比較兩個物件參考變數。

## <a name="syntax"></a>Syntax

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>組件

- `result`

  必要。 `Boolean` 值。

- `object1`

  必要。 任何 `Object` 變數或運算式。

- `object2`

  必要。 任何 `Object` 變數或運算式。

## <a name="remarks"></a>備註

`IsNot`運算子會判斷兩個物件參考是否參考不同的物件。 但是，它不會執行值比較。 如果 `object1` 和 `object2` 兩者都參考完全相同的物件實例，則為 `result` `False` ; 如果不是，則 `result` 為 `True` 。

`IsNot` 這是運算子的相反 `Is` 。 的優點 `IsNot` 是您可以避免使用和的語法不 `Not` `Is` 困難，這可能很難閱讀。

 您可以使用 `Is` 和 `IsNot` 運算子來測試早期繫結和晚期繫結的物件。

## <a name="example"></a>範例

下列程式碼範例會使用 `Is` 運算子和 `IsNot` 運算子來完成相同的比較。

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a>使用 TypeOf 運算子搭配 IsNot 運算子

從 Visual Basic 14 開始，您可以使用 `TypeOf` 運算子搭配 `IsNot` 運算子來測試物件是否與資料類型 *不* 相容。 例如：

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a>另請參閱

- [Is 運算子](is-operator.md)
- [TypeOf 運算子](typeof-operator.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [如何：測試兩個物件是否相同](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
