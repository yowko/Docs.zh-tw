---
title: IsNot 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ffafff915af8a94e9bc135246064e4c049d41838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596458"
---
# <a name="isnot-operator-visual-basic"></a>IsNot 運算子 (Visual Basic)
比較兩個物件參考變數。  
  
## <a name="syntax"></a>語法  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 `Boolean` 值。  
  
 `object1`  
 必要項。 任何`Object`變數或運算式。  
  
 `object2`  
 必要項。 任何`Object`變數或運算式。  
  
## <a name="remarks"></a>備註  
 `IsNot`運算子會判斷是否兩個物件參考會參考不同的物件。 不過，它不會執行值比較。 如果`object1`並`object2`都會參考完全相同的物件執行個體`result`是`False`; 如果沒有的話，`result`是`True`。  
  
 `IsNot` 相反`Is`運算子。 善用`IsNot`是您可以避免使用不便的語法`Not`和`Is`，可能會難以閱讀。  
  
 您可以使用`Is`和`IsNot`運算子來測試早期繫結和晚期繫結物件。  
  
> [!NOTE]
>  `IsNot`運算子不能用來比較運算式傳回`TypeOf`運算子。 相反地，您必須使用`Not`和`Is`運算子。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用這兩者`Is`運算子和`IsNot`運算子來完成相同的比較。  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- [Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)
- [TypeOf 運算子](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [如何：測試兩個物件是否相同](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
