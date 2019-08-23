---
title: IsFalse 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 49b8493575685a220808df1522ce16835b3ce0ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917149"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse 運算子 (Visual Basic)
判斷運算式是否為`False`。  
  
 您無法在`IsFalse`程式碼中明確呼叫, 但是 Visual Basic 編譯器可以使用它來產生來自子句`AndAlso`的程式碼。 如果您定義了類別或結構, 然後在`AndAlso`子句中使用該類型的變數, 您必須在該類別或結構上定義。 `IsFalse`  
  
 編譯器會將`IsFalse`和`IsTrue`運算子視為相符的*配對*。 這表示如果您定義其中一個, 則也必須定義另一個。  
  
> [!NOTE]
> 運算子可以多載, 這表示當類別或結構的運算元具有該類別或結構的類型時, 可以重新定義其行為。 `IsFalse` 如果您的程式碼在這類類別或結構上使用這個運算子, 請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會定義包含`IsFalse`和`IsTrue`運算子之定義的結構外框。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>另請參閱

- [IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)
