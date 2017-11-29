---
title: "不正確的 DLL 呼叫慣例"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a>不正確的 DLL 呼叫慣例
引數傳遞至動態連結程式庫 (DLL) 必須完全符合所預期的常式。 呼叫慣例處理數目、 類型和引數的順序。 您的程式可能會呼叫常式傳入的引數數目的錯誤類型的 DLL 中。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定所有引數型別與所呼叫常式的宣告中指定數一致。  
  
2.  請確定您要將您要呼叫常式宣告所示的引數數目相同。  
  
3.  如果 DLL 常式的引數必須為值，請確定`ByVal`指定常式的宣告中的這些引數。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Call 陳述式](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
