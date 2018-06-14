---
title: IsTrue 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: fc01b074d9aba245b1c55b75b841a7f195f7ec04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605143"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue 運算子 (Visual Basic)
判斷運算式是否為`True`。  
  
 您不能呼叫`IsTrue`明確地在您的程式碼，但 Visual Basic 編譯器可以用它來產生程式碼從`OrElse`子句。 如果您定義類別或結構，然後使用 在該類型的變數`OrElse`子句，您必須定義`IsTrue`該類別或結構上。  
  
 編譯器會考慮`IsTrue`和`IsFalse`運算子*相符配對*。 這表示，如果您定義其中一個，您也必須定義，另一個。  
  
## <a name="compiler-use-of-istrue"></a>IsTrue 的編譯器使用  
 當您已經定義類別或結構時，您可以使用在該類型的變數`For`， `If`， `Else``If`，或`While`陳述式，或在`When`子句。 如果這樣做，編譯器會要求將轉換成您類型的運算子`Boolean`值讓它可以測試條件。 它會搜尋適當的運算子，以下列順序：  
  
1.  擴展的轉換運算子，從您的類別或結構`Boolean`。  
  
2.  擴展的轉換運算子，從您的類別或結構`Boolean?`。  
  
3.  `IsTrue`上類別或結構的運算子。  
  
4.  若要縮小轉換`Boolean?`並不會從轉換`Boolean`至`Boolean?`。  
  
5.  從您的類別或結構，以縮小轉換運算子`Boolean`。  
  
 如果您還沒有定義任何轉換`Boolean`或`IsTrue`運算子，編譯器會發出錯誤信號。  
  
> [!NOTE]
>  `IsTrue`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時其運算元的該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例定義的結構，其中包含定義外框`IsFalse`和`IsTrue`運算子。  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [IsFalse 運算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)
