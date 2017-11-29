---
title: "&lt;&lt;運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56cfb227f7e5c68de802c1f2cfb842a770f65ae0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt;運算子 (Visual Basic)
位元模式上執行算術左的移位。  
  
## <a name="syntax"></a>語法  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 整數值。 移位的位元模式的結果。 資料類型是屬於相同`pattern`。  
  
 `pattern`  
 必要項。 整數的數值運算式。 要移位的位元模式。 資料型別必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。  
  
 `amount`  
 必要項。 數值運算式。 要移位的位元模式的位元數。 資料類型必須是`Integer`或擴展為`Integer`。  
  
## <a name="remarks"></a>備註  
 算術排班不是循環，這表示移出結果的一個 end 的位元會重新引入的另一端。 在算術左移位，移位超出結果資料類型之範圍的位元會捨棄，而且右方空出的位元位置會設定為零。  
  
 若要避免多於結果所能容納更多的位元位移，Visual Basic 遮罩的值`amount`與對應的資料類型的大小遮罩`pattern`。 這些值的二進位 AND 用於移位量。 遮罩的大小如下所示：  
  
|資料型別`pattern`|大小遮罩 （十進位）|大小遮罩 （十六進位）|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|（& S) H00000007|  
|`Short`, `UShort`|15|（& S) H0000000F|  
|`Integer`, `UInteger`|31|（& S) H0000001F|  
|`Long`, `ULong`|63|（& S) H0000003F|  
  
 如果`amount`是零，值`result`等同於值`pattern`。 如果`amount`是負數，它是被視為不帶正負號的值，加上適當的大小遮罩。  
  
 算術移位不會產生溢位例外狀況。  
  
> [!NOTE]
>  `<<`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`<<`運算子來執行算術左移位整數值。 結果會有相同的資料類型已移位之運算式。  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 前一個範例的結果如下所示：  
  
-   `result1`為 192 (0000 0000 1100年 0000)。  
  
-   `result2`會 3072 (0000 1100年 0000 0000)。  
  
-   `result3`是介於-32768 (1000年 0000 0000 0000)。  
  
-   `result4`為 384 (0000 0001 1000年 0000)。  
  
-   `result5`為 0 （左邊的移位 15 位數）。  
  
 移位量的`result4`的計算方式為 17 和 15，等於 1。  
  
## <a name="see-also"></a>另請參閱  
 [位元移位運算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<<= 運算子](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
