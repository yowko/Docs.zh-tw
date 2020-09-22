---
title: /= 運算子
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: d47a69e454305ce9417a46b5bbfbbb55a1ad1dc3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867070"
---
# <a name="-operator-visual-basic"></a>/= 運算子 (Visual Basic)

將變數或屬性的值除以運算式的值，並將浮點結果指派給變數或屬性。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>組件  

 `variableorproperty`  
 必要。 任何數值變數或屬性。  
  
 `expression`  
 必要。 任何數值運算式。  
  
## <a name="remarks"></a>備註  

 運算子左邊的元素 `/=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。  
  
 `/=`運算子會先將運算子左邊的變數或 (屬性值除以運算子左邊的運算式 (的值，) ) 的右邊運算式的值。 然後，運算子會將該運算的浮點結果指派給變數或屬性。  
  
 這個語句會將 `Double` 值指派給左邊的變數或屬性。 如果 `Option Strict` 為 `On` ，則 `variableorproperty` 必須是 `Double` 。 如果 `Option Strict` 為 `Off` ，Visual Basic 會執行隱含轉換，並將產生的值指派給 `variableorproperty` ，在執行時間可能發生錯誤。 如需詳細資訊，請參閱 [擴展和縮小轉換](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) 和 [Option Strict 語句](../statements/option-strict-statement.md)。  
  
## <a name="overloading"></a>多載化  

 您可以多載 [ (Visual Basic) 的/運算子 ](floating-point-division-operator.md) *，這*表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 多載 `/` 運算子會影響運算子的行為 `/=` 。 如果您的程式碼在多載的 `/=` 類別或結構上使用 `/` ，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `/=` 運算子將一個變數除以 `Integer` 第二個變數，並將該商指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>另請參閱

- [/運算子 (Visual Basic) ](floating-point-division-operator.md)
- [\\= 運算子](integer-division-assignment-operator.md)
- [指派運算子](assignment-operators.md)
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
