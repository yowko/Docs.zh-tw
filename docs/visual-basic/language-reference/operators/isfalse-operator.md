---
title: IsFalse 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 51b7bfb2cf5301a39818e6566b408ee0677689f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349522"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse 運算子 (Visual Basic)
判斷運算式是否 `False`。  
  
 您無法在程式碼中明確地呼叫 `IsFalse`，但 Visual Basic 編譯器可以使用它從 `AndAlso` 子句產生程式碼。 如果您定義了類別或結構，然後在 `AndAlso` 子句中使用該類型的變數，就必須在該類別或結構上定義 `IsFalse`。  
  
 編譯器會將 `IsFalse` 和 `IsTrue` 運算子視為相符的*配對*。 這表示如果您定義其中一個，則也必須定義另一個。  
  
> [!NOTE]
> `IsFalse` 運算子可以多載 *，這*表示當類別或結構的運算元具有該類別或結構的類型時，就可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會定義結構的外框，其中包含 `IsFalse` 和 `IsTrue` 運算子的定義。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>請參閱

- [IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)
