---
title: Widening (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 034099397c1d296a42712b8c202e2ac99a0fb43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
表示轉換運算子 (`CType`) 將類別或結構轉換成可容納原始類別或結構的所有可能值的類型。  
  
## <a name="converting-with-the-widening-keyword"></a>轉換以擴展關鍵字  
 轉換程序必須指定`Public Shared`除了`Widening`。  
  
 擴展轉換，一定要成功執行階段，並永遠不會造成資料遺失。 範例包括`Single`至`Double`，`Char`至`String`，和其基底類型的衍生型別。 因為衍生的類型包含基底型別的所有成員，因此基底類型的執行個體，就會擴展這個最後一個轉換。  
  
 使用的程式碼不需要使用`CType`的擴展轉換，即使`Option Strict`是`On`。  
  
 `Widening`關鍵字可用於此內容：  
  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 定義擴展和縮小轉換的運算子，例如看到[如何： 定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
