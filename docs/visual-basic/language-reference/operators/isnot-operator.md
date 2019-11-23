---
title: IsNot 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336067"
---
# <a name="isnot-operator-visual-basic"></a>IsNot 運算子 (Visual Basic)

Compares two object reference variables.

## <a name="syntax"></a>語法

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>組件
 需要 `result`。 `Boolean` 值。

 需要 `object1`。 Any `Object` variable or expression.

 需要 `object2`。 Any `Object` variable or expression.

## <a name="remarks"></a>備註
 The `IsNot` operator determines if two object references refer to different objects. However, it does not perform value comparisons. If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.

 `IsNot` is the opposite of the `Is` operator. The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.

 You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.

## <a name="example"></a>範例
 The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>請參閱

- [Is 運算子](is-operator.md)
- [TypeOf 運算子](typeof-operator.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [如何：測試兩個物件是否相同](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
