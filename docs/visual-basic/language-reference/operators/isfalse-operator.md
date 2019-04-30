---
title: IsFalse 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 9f25c406038486224c2c4708c86ef86889c44c15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013539"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse 運算子 (Visual Basic)
判斷運算式是否為`False`。  
  
 您不能呼叫`IsFalse`明確地在您的程式碼，但 Visual Basic 編譯器可以用它來產生程式碼從`AndAlso`子句。 如果您定義類別或結構，然後使用 在該類型的變數`AndAlso`子句中，您必須定義`IsFalse`該類別或結構上。  
  
 編譯器會考慮`IsFalse`並`IsTrue`做為運算子*比對組*。 這表示，如果您定義其中一個，您也必須定義，另一個。  
  
> [!NOTE]
>  `IsFalse`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時其運算元的該類別或結構的類型。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會定義結構，其中包含定義的外框`IsFalse`和`IsTrue`運算子。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>另請參閱

- [IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)
