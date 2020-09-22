---
title: '\= 運算子'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: 6e749e13c0427354db9e361538d4bef10b6c6b04
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873400"
---
# <a name="-operator"></a>\\= 運算子

將變數或屬性的值除以運算式的值，並將整數結果指派給變數或屬性。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>組件  

 `variableorproperty`  
 必要。 任何數值變數或屬性。  
  
 `expression`  
 必要。 任何數值運算式。  
  
## <a name="remarks"></a>備註  

 運算子左邊的元素 `\=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。  
  
 運算子會將 `\=` 變數或屬性的值除以其右邊的值，然後將整數結果指派給左邊的變數或屬性。  
  
 如需整數除法的詳細資訊，請參閱 [\ 運算子 (Visual Basic) ](integer-division-operator.md)。  
  
## <a name="overloading"></a>多載化  

 可以多載 `\` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 多載 `\` 運算子會影響運算子的行為 `\=` 。 如果您的程式碼在多載的 `\=` 類別或結構上使用 `\` ，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `\=` 運算子將一個變數除以 `Integer` 第二個變數，然後將整數結果指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>另請參閱

- [\ 運算子 (Visual Basic) ](integer-division-operator.md)
- [/= 運算子 (Visual Basic) ](floating-point-division-assignment-operator.md)
- [指派運算子](assignment-operators.md)
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
