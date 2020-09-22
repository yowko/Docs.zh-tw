---
title: IsFalse 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: bbcdb9bcf645a4e9cb54c657ccd46e04437d207e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873378"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse 運算子 (Visual Basic)

判斷運算式是否為 `False` 。  
  
 您無法 `IsFalse` 在程式碼中明確呼叫，但是 Visual Basic 編譯器可以使用它從子句產生程式碼 `AndAlso` 。 如果您定義類別或結構，然後在子句中使用該類型的變數 `AndAlso` ，則必須 `IsFalse` 在該類別或結構上定義。  
  
 編譯器會將 `IsFalse` 和 `IsTrue` 運算子視為相符的 *配對*。 這表示，如果您定義其中一個，您也必須定義另一個。  
  
> [!NOTE]
> 可以多載 `IsFalse` 運算子*overloaded*，這表示類別或結構在其運算元具有該類別或結構的型別時，可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列程式碼範例會定義結構的外框，其中包含 `IsFalse` 和運算子的定義 `IsTrue` 。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>另請參閱

- [IsTrue 運算子](istrue-operator.md)
- [如何：定義運算子](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso 運算子](andalso-operator.md)
