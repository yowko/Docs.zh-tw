---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50116c6212e919d4b9b35fc933d80dee14bd4ecf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
表示轉換運算子 (`CType`) 將類別或結構轉換成可能無法保留一些可能的值，原始類別或結構的類型。  
  
## <a name="converting-with-the-narrowing-keyword"></a>轉換以縮小關鍵字  
 轉換程序必須指定`Public Shared`除了`Narrowing`。  
  
 縮小轉換執行不一定成功在執行階段，並可能會失敗或者造成資料遺失。 範例包括`Long`至`Integer`，`String`至`Date`，且基底型別衍生型別。 這個最後一個轉換縮小，因為基底型別可能不會包含衍生型別的所有成員，而且不是衍生類型的執行個體。  
  
 如果`Option Strict`是`On`、 使用程式碼必須使用`CType`所有的縮小轉換。  
  
 `Narrowing`關鍵字可用於此內容：  
  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
