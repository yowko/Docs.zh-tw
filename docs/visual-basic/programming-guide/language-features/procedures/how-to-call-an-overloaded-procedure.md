---
title: 如何：呼叫多載程序 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5eca03de6b6dd2ca2b992196b1ae224f8fbf5068
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>如何：呼叫多載程序 (Visual Basic)
多載化程序的優點是在呼叫的彈性。 呼叫程式碼可以取得傳遞至程序，然後再呼叫單一程序名稱，不論所傳遞的引數需要的資訊。  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>若要呼叫的程序具有多個定義的版本  
  
1.  在呼叫的程式碼，判斷哪些資料来傳遞至程序。  
  
2.  撰寫一般的方式，將資料呈現在引數清單的程序呼叫。 請確定引數符合其中一個版本為程序定義中的參數清單。  
  
3.  您不需要判斷哪一個版本的程序呼叫。 Visual Basic 會將控制項傳遞至比對引數清單的版本。  
  
     下列範例會呼叫`post`程序宣告中[如何： 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)。 它會取得客戶識別，判斷它是否`String`或`Integer`，然後在任一情況下呼叫相同的程序。  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [程序多載化](./procedure-overloading.md)  
 [程序的疑難排解](./troubleshooting-procedures.md)  
 [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)  
 [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)  
 [多載解析](./overload-resolution.md)  
 [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
