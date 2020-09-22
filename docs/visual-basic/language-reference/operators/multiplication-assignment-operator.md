---
title: '*= 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 4e2f18fb2b8110d97390390b3934d3c1761baa35
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866738"
---
# <a name="-operator-visual-basic"></a>*= 運算子 (Visual Basic)

將變數或屬性的值乘以運算式的值，並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>組件  

 `variableorproperty`  
 必要。 任何數值變數或屬性。  
  
 `expression`  
 必要。 任何數值運算式。  
  
## <a name="remarks"></a>備註  

 運算子左邊的元素 `*=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。  
  
 `*=`運算子會先將運算子右邊的運算式 (值乘以運算子左邊的變數或屬性（ (property）值) 的值，) 的。 然後，運算子會將該操作的結果指派給變數或屬性。  
  
## <a name="overloading"></a>多載化  

 您可以多載 [* 運算子](multiplication-operator.md) ，這表示當運算元的類型為該類別或結構 *時，類別*或結構可以重新定義其行為。 多載 `*` 運算子會影響運算子的行為 `*=` 。 如果您的程式碼在多載的 `*=` 類別或結構上使用 `*` ，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `*=` 運算子來將一個 `Integer` 變數乘以第二個變數，並將結果指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [* 運算子](multiplication-operator.md)
- [指派運算子](assignment-operators.md)
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
