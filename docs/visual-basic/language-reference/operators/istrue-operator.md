---
title: IsTrue 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: b2ec1a20e815ad38c2fdd984b9f9c35247dae81a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971308"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue 運算子 (Visual Basic)
判斷運算式是否為`True`。  
  
 您不能呼叫`IsTrue`明確地在您的程式碼，但 Visual Basic 編譯器可以用它來產生程式碼從`OrElse`子句。 如果您定義類別或結構，然後使用 在該類型的變數`OrElse`子句中，您必須定義`IsTrue`該類別或結構上。  
  
 編譯器會考慮`IsTrue`並`IsFalse`做為運算子*比對組*。 這表示，如果您定義其中一個，您也必須定義，另一個。  
  
## <a name="compiler-use-of-istrue"></a>IsTrue 的編譯器使用  
 當您已定義類別或結構時，您可以使用在該類型的變數`For`， `If`， `Else If`，或`While`陳述式，或在`When`子句。 如果您這麼做時，編譯器需要轉換成您類型的運算子`Boolean`值讓它可以測試條件。 它會搜尋適當的運算子，以下列順序：  
  
1.  擴展的轉換運算子，從您的類別或結構`Boolean`。  
  
2.  擴展的轉換運算子，從您的類別或結構`Boolean?`。  
  
3.  `IsTrue`運算子，在您自己的類別或結構。  
  
4.  若要縮小轉換`Boolean?`，未牽涉到從轉換`Boolean`至`Boolean?`。  
  
5.  縮小的轉換運算子，從您的類別或結構`Boolean`。  
  
 如果您還沒有定義任何轉換成`Boolean`或`IsTrue`運算子，編譯器會發出錯誤信號。  
  
> [!NOTE]
>  `IsTrue`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時其運算元的該類別或結構的類型。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會定義結構，其中包含定義的外框`IsFalse`和`IsTrue`運算子。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>另請參閱
- [IsFalse 運算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)
