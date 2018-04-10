---
title: '&gt;&gt;運算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4eb0ed817c95905a679de5026bf6494eb72df078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;運算子 (Visual Basic)
位元模式上執行算術右移位。  
  
## <a name="syntax"></a>語法  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 整數值。 移位的位元模式的結果。 資料類型是屬於相同`pattern`。  
  
 `pattern`  
 必要項。 整數的數值運算式。 要移位的位元模式。 資料型別必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。  
  
 `amount`  
 必要項。 數值運算式。 要移位的位元模式的位元數。 資料類型必須是`Integer`或擴展為`Integer`。  
  
## <a name="remarks"></a>備註  
 算術排班不是循環，這表示移出結果的一個 end 的位元會重新引入的另一端。 在算術右移位，移位超過右邊的位元位置的位元會捨棄，而且最左邊 （符號） 位元會傳播到左邊空出的位元位置。 這表示如果`pattern`負值，空出的位置會設為其中一個; 否則設定為零。  
  
 請注意，資料型別`Byte`， `UShort`， `UInteger`，和`ULong`是不帶正負號，所以傳播的無正負號位元。 如果`pattern`的任何不帶正負號型別、 空出的位置永遠會設定為零。  
  
 若要避免由多於結果所能容納更多的位元移位，Visual Basic 遮罩的值`amount`大小遮罩的資料類型對應`pattern`。 這些值的二進位 AND 用於移位量。 遮罩的大小如下所示：  
  
|資料型別`pattern`|大小遮罩 （十進位）|大小遮罩 （十六進位）|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|（& S) H00000007|  
|`Short`, `UShort`|15|（& S) H0000000F|  
|`Integer`, `UInteger`|31|（& S) H0000001F|  
|`Long`, `ULong`|63|（& S) H0000003F|  
  
 如果`amount`是零，值`result`等同於值`pattern`。 如果`amount`是負數，它是被視為不帶正負號的值，加上適當的大小遮罩。  
  
 算術移位不會產生溢位例外狀況。  
  
## <a name="overloading"></a>多載化  
 `>>`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`>>`整數值上執行算術右移位運算子。 結果會有相同的資料類型已移位之運算式。  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 前述範例中的結果如下所示：  
  
-   `result1`是 2560 (0000 1010年 0000 0000)。  
  
-   `result2`為 160 (0000 0000 1010年 0000)。  
  
-   `result3`為 2 (0000 0000 0000 0010)。  
  
-   `result4`為 640 (0000 0010 1000年 0000)。  
  
-   `result5`為 0 （右邊的移位 15 位數）。  
  
 移位量的`result4`的計算方式為 18 和 15，等於 2。  
  
 下列範例顯示上一個負數值的算術移位。  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 前述範例中的結果如下所示：  
  
-   `negresult1`是-512 (1111年 1110年 0000 0000)。  
  
-   `negresult2`為-1 （傳播正負號位元）。  
  
## <a name="see-also"></a>另請參閱  
 [位元移位運算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [>>= 運算子](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
