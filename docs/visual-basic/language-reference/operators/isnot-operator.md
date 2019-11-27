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

比較兩個物件參考變數。

## <a name="syntax"></a>語法

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>組件
 `result` 必要。 `Boolean` 值。

 `object1` 必要。 任何 `Object` 變數或運算式。

 `object2` 必要。 任何 `Object` 變數或運算式。

## <a name="remarks"></a>備註
 `IsNot` 運算子會判斷兩個物件參考是否參考不同的物件。 不過，它不會執行值比較。 如果 `object1` 和 `object2` 都參考完全相同的物件實例，`result` 會 `False`;如果沒有，則會 `True``result`。

 `IsNot` 是 `Is` 運算子的相反。 `IsNot` 的優點是，您可以使用 `Not` 和 `Is`來避免語法不太容易閱讀。

 您可以使用 `Is` 和 `IsNot` 運算子來測試早期繫結和晚期繫結物件。

## <a name="example"></a>範例
 下列程式碼範例會使用 `Is` 運算子和 `IsNot` 運算子來完成相同的比較。

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>請參閱

- [Is 運算子](is-operator.md)
- [TypeOf 運算子](typeof-operator.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [如何：測試兩個物件是否相同](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
