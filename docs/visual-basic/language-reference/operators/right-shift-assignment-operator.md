---
title: "&gt;&gt;= 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7e388471b9adf424c55b1ad1042e5aed1ea8ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;= 運算子 (Visual Basic)
執行算術右移位的變數或屬性的值，並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 變數或屬性的整數類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。  
  
 `amount`  
 必要項。 數值運算式的資料類型可擴展成`Integer`。  
  
## <a name="remarks"></a>備註  
 在左邊的項目`>>=`運算子可以是簡單的純量變數、 屬性或陣列的項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `>>=`運算子會先執行算術右移位的變數或屬性的值。 然後，運算子會將該作業的結果指派給變數或屬性。  
  
 算術排班不是循環，這表示移出結果的一個 end 的位元會重新引入的另一端。 在算術右移位，移位超過右邊的位元位置的位元會捨棄，並最左邊的位元會傳播到左邊空出的位元位置。 這表示如果`variableorproperty`負值，空出的位置會設定為其中一個。 如果`variableorproperty`是正數，或其資料類型是不帶正負號的類型，如果空出的位置會設定為零。  
  
## <a name="overloading"></a>多載化  
 [>> 運算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)可以*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 多載`>>`運算子會影響行為`>>=`運算子。 如果您的程式碼使用`>>=`上類別或結構的多載`>>`，確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`>>=`要移位的位元模式的運算子`Integer`向右旋轉指定的數量並指派結果給變數的變數。  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [>> 運算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [位元移位運算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
