---
title: IsFalse 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: e84b2162eb0763725f05bc52d5c4223d7c430b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600042"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse 運算子 (Visual Basic)
判斷運算式是否為`False`。  
  
 您不能呼叫`IsFalse`明確地在您的程式碼，但 Visual Basic 編譯器可以用它來產生程式碼從`AndAlso`子句。 如果您定義類別或結構，然後使用 在該類型的變數`AndAlso`子句，您必須定義`IsFalse`該類別或結構上。  
  
 編譯器會考慮`IsFalse`和`IsTrue`運算子*相符配對*。 這表示，如果您定義其中一個，您也必須定義，另一個。  
  
> [!NOTE]
>  `IsFalse`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時其運算元的該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例定義的結構，其中包含定義外框`IsFalse`和`IsTrue`運算子。  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)
