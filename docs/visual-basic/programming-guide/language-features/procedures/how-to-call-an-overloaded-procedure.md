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
ms.openlocfilehash: f13fdae9617fa2af21978979cad6f90a15140a4a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969993"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>HOW TO：呼叫多載程序 (Visual Basic)
多載化程序的優點是在呼叫的彈性。 呼叫端程式碼可以取得它需要傳遞至程序，並接著呼叫單一程序名稱，不論它傳遞引數的資訊。  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>呼叫已定義的多個版本的程序  
  
1.  在呼叫的程式碼，判斷要傳遞至程序的資料。  
  
2.  寫入程序呼叫一般的方式，將資料呈現在引數清單。 請確定引數符合其中一個版本的程序定義中的參數清單。  
  
3.  您不必決定哪個版本的程序呼叫。 Visual Basic 會將控制項傳遞至比對引數清單的版本。  
  
     下列範例會呼叫`post`程序宣告於[How to:定義多個版本的程序](./how-to-define-multiple-versions-of-a-procedure.md)。 它會取得客戶識別碼、 判斷是否`String`或`Integer`，然後在任一情況下呼叫相同的程序。  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
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
