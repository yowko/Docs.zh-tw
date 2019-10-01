---
title: Is 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 0351d224d9bf08a8f3ca74090de7b9c51c2c61bf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701371"
---
# <a name="is-operator-visual-basic"></a>Is 運算子 (Visual Basic)
比較兩個物件參考變數。  
  
## <a name="syntax"></a>語法  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何 `Boolean` 值。  
  
 `object1`  
 必要項。 任何 `Object` 名稱。  
  
 `object2`  
 必要項。 任何 `Object` 名稱。  
  
## <a name="remarks"></a>備註  
 @No__t-0 運算子會判斷兩個物件參考是否參考相同的物件。 不過，它不會執行值比較。 如果 `object1` 和 `object2` 都參考完全相同的物件實例，`result` 會 `True`;如果不是，`result` `False`。  
  
 `Is` 也可以與 `TypeOf` 關鍵字搭配使用，以建立 `TypeOf` ... `Is` 運算式，以測試物件變數是否與資料類型相容。  
  
> [!NOTE]
> [@No__t-0] 關鍵字也用於 [[選取 ...]Case 語句](../../../visual-basic/language-reference/statements/select-case-statement.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Is` 運算子來比較物件參考的配對。 結果會指派給 @no__t 0 值，表示兩個物件是否相同。  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 如上述範例所示，您可以使用 `Is` 運算子來測試早期繫結和晚期繫結物件。  
  
## <a name="see-also"></a>另請參閱

- [TypeOf 運算子](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Visual Basic 中的比較運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
