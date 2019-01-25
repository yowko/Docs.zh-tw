---
title: HOW TO：呼叫多載程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 8320bc550c818fd2bea53f75107709eab8456096
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706413"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>HOW TO：呼叫多載程序 (Visual Basic)
多載化程序的優點是在呼叫的彈性。 呼叫端程式碼可以取得它需要傳遞至程序，並接著呼叫單一程序名稱，不論它傳遞引數的資訊。  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>呼叫已定義的多個版本的程序  
  
1.  在呼叫的程式碼，判斷要傳遞至程序的資料。  
  
2.  寫入程序呼叫一般的方式，將資料呈現在引數清單。 請確定引數符合其中一個版本的程序定義中的參數清單。  
  
3.  您不必決定哪個版本的程序呼叫。 Visual Basic 會將控制項傳遞至比對引數清單的版本。  
  
     下列範例會呼叫`post`程序宣告於[How to:定義多個版本的程序](./how-to-define-multiple-versions-of-a-procedure.md)。 它會取得客戶識別碼、 判斷是否`String`或`Integer`，然後在任一情況下呼叫相同的程序。  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>另請參閱
- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [程序多載化](./procedure-overloading.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義多個版本的程序](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：多載會採用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)
- [多載解析](./overload-resolution.md)
- [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
