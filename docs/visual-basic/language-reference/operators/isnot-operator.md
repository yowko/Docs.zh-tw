---
title: IsNot 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966929"
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
 `IsNot`運算子會判斷兩個物件參考是否參考不同的物件。 不過, 它不會執行值比較。 如果`object1`和`False` `result` `result` `True`兩者都參考完全相同的物件實例, 則為; 如果不是, 則為。 `object2`  
  
 `IsNot`是`Is`運算子的相反。 的優點`IsNot`是, 您可以避免使用`Not`和`Is`的語法不好, 這可能難以閱讀。  
  
 您可以使用`Is`和`IsNot`運算子來測試早期繫結和晚期繫結物件。  
  
> [!NOTE]
> 運算子不能用來比較`TypeOf`從運算子傳回的運算式。 `IsNot` 相反`Not`地, 您必須使用和`Is`運算子。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用`Is`運算子`IsNot`和運算子來完成相同的比較。  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a>另請參閱

- [Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)
- [TypeOf 運算子](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [如何：測試兩個物件是否相同](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
