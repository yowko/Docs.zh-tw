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
ms.openlocfilehash: a546d8b0c9b3852386970f80d3da96794da2351c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370943"
---
# <a name="-operator"></a>\\= 運算子
將變數或屬性的值除以運算式的值，並將整數結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要。 任何數值變數或屬性。  
  
 `expression`  
 必要。 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 運算子左邊的元素 `\=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可為[ReadOnly](../modifiers/readonly.md)。  
  
 運算子會將 `\=` 變數或屬性的值除以其右邊的值，並將整數結果指派給其左邊的變數或屬性  
  
 如需整數除法的進一步資訊，請參閱[\ 運算子（Visual Basic）](integer-division-operator.md)。  
  
## <a name="overloading"></a>多載化  
 `\`運算子可以多載*overloaded*，這表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 多載 `\` 運算子會影響運算子的行為 `\=` 。 如果您的程式碼在多載 `\=` 的類別或結構上使用 `\` ，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用運算子，將 `\=` 一個 `Integer` 變數除以一秒，並將整數結果指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>另請參閱

- [\ 運算子（Visual Basic）](integer-division-operator.md)
- [/= 運算子（Visual Basic）](floating-point-division-assignment-operator.md)
- [指派運算子](assignment-operators.md)
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
