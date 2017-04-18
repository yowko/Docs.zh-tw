---
title: "函式評估已停用，因為先前的函式評估逾時 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
dev_langs:
- VB
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b861b5c6c151c5d3aeec2810c7f2a228f22fdf6e
ms.lasthandoff: 03/13/2017

---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>函式評估已停用，因為先前的函式評估逾時
函式評估已停用，因為先前的函式評估逾時。 若要重新啟用函式評估，再次逐步執行或重新啟動偵錯。  
  
 在 Visual Studio 偵錯工具運算式指定的程序呼叫，但其他評估已逾時。  
  
 程序呼叫的逾時時間的可能原因包括無限迴圈或*永無止盡的迴圈*。 如需詳細資訊，請參閱[For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)。  
  
 無限迴圈的特殊案例是*遞迴*。 如需詳細資訊，請參閱[遞迴程序](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)。  
  
 **錯誤識別碼︰** BC30957  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  可能的話，請判斷先前的函式評估的是和逾時時間的原因。 否則，您可能會遇到這個錯誤一次。  
  
2.  同樣地，逐步偵錯工具或終止，並重新啟動偵錯。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)   
 [使用偵錯工具巡覽程式碼](https://docs.microsoft.com/visualstudio/debugger/navigating-through-code-with-the-debugger)
