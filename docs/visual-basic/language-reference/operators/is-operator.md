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
ms.openlocfilehash: 8beca1dc8788514224f70cacc5b8ede0974f5230
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601946"
---
# <a name="is-operator-visual-basic"></a>Is 運算子 (Visual Basic)
比較兩個物件參考變數。  
  
## <a name="syntax"></a>語法  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要。 任何`Boolean`值。  
  
 `object1`  
 必要。 任何`Object`名稱。  
  
 `object2`  
 必要。 任何`Object`名稱。  
  
## <a name="remarks"></a>備註  
 `Is`運算子會判斷是否兩個物件參考會參考相同的物件。 不過，它不會執行值比較。 如果`object1`和`object2`完全相同的物件執行個體都會參考`result`是`True`; 如果沒有的話，`result`是`False`。  
  
 `Is` 也可與`TypeOf`關鍵字進行`TypeOf`...`Is`測試是否與資料類型相容的物件變數的運算式。  
  
> [!NOTE]
>  `Is`關鍵字也用於[選取...陳述式的大小寫](../../../visual-basic/language-reference/statements/select-case-statement.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Is`運算子來比較的物件參考的組。 結果會指派給`Boolean`值，表示兩個物件是否相同。  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 如上述範例所示，您可以使用`Is`運算子來測試兩者早期繫結和晚期繫結物件。  
  
## <a name="see-also"></a>另請參閱  
 [TypeOf 運算子](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [在 Visual Basic 中的比較運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
