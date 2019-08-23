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
ms.openlocfilehash: a5481a9bce01e84ce4f078335c8cd15a747a3c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917222"
---
# <a name="is-operator-visual-basic"></a>Is 運算子 (Visual Basic)
比較兩個物件參考變數。  
  
## <a name="syntax"></a>語法  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何`Boolean`值。  
  
 `object1`  
 必要項。 任何`Object`名稱。  
  
 `object2`  
 必要項。 任何`Object`名稱。  
  
## <a name="remarks"></a>備註  
 `Is`運算子會判斷兩個物件參考是否參考相同的物件。 不過, 它不會執行值比較。 如果`object1`和`True` `result` `result` `False`兩者都參考完全相同的物件實例, 則為; 如果不是, 則為。 `object2`  
  
 `Is`也可以與`TypeOf`關鍵字搭配使用來`TypeOf`建立 .。。`Is`運算式, 用來測試物件變數是否與資料類型相容。  
  
> [!NOTE]
> `Is`關鍵字也用於 [[選取 ...]Case 語句](../../../visual-basic/language-reference/statements/select-case-statement.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Is`運算子來比較物件參考的配對。 結果會指派給一個`Boolean`值, 表示兩個物件是否相同。  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 如上述範例所示, 您可以使用`Is`運算子來測試早期繫結和晚期繫結物件。  
  
## <a name="see-also"></a>另請參閱

- [TypeOf 運算子](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Visual Basic 中的比較運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
