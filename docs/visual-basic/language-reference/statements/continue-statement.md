---
title: "Continue 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a47819600a6c1d58f09c2f8ed3443632e9dab68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="continue-statement-visual-basic"></a>Continue 陳述式 (Visual Basic)
將控制權立即迴圈的下一個反覆項目。  
  
## <a name="syntax"></a>語法  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>備註  
 您可以從傳輸內`Do`， `For`，或`While`迴圈，該迴圈的下一個反覆項目。 控制會傳遞給迴圈的條件測試，這相當於將傳送至立即`For`或`While`陳述式，或`Do`或`Loop`包含陳述式`Until`或`While`子句。  
  
 您可以使用`Continue`允許傳輸的迴圈中的任何位置。 允許將控制項的規則是與使用相同[GoTo 陳述式](../../../visual-basic/language-reference/statements/goto-statement.md)。  
  
 比方說，如果迴圈是完全包含在`Try`區塊，`Catch`區塊，或`Finally`區塊中，您可以使用`Continue`迴圈之外傳輸。 另一方面，如果`Try`...`End Try`結構是否包含在迴圈中，您無法使用`Continue`傳輸超出控制項`Finally`區塊，以及您可以使用它來傳送出`Try`或`Catch`完全轉移出時才會封鎖`Try`...`End Try`結構。  
  
 如果您有巢狀的迴圈屬於相同的類型，例如`Do`另迴圈內`Do`迴圈，`Continue Do`陳述式會略過的最內層的下一個反覆運算`Do`包含它的迴圈。 您無法使用`Continue`跳至包含相同類型的迴圈的下一個反覆項目。  
  
 如果您有巢狀的迴圈的不同型別，例如`Do`迴圈內`For`迴圈中，您可以使用跳至其中一個迴圈的下一個反覆運算`Continue Do`或`Continue For`。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用`Continue While`陳述式跳至下一個資料行的陣列，如果除數為零。 `Continue While`位於`For`迴圈。 它會傳送到`While col < lastcol`陳述式，這是最內層的下一個反覆運算`While`迴圈，其中包含`For`迴圈。  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
