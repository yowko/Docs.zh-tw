---
title: "如何︰ 呼叫多載程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- procedures, overloading
- procedures, calling
- procedures, multiple versions
- procedure calls, overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 0da83aa63bf013d841f2a01a535726f3b03497a1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>如何：呼叫多載程序 (Visual Basic)
多載化程序的優點是在呼叫的彈性。 呼叫程式碼可以取得的資訊，以便將傳遞至程序，然後呼叫單一程序名稱，不論所傳遞的引數。  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>呼叫已定義多個版本的程序  
  
1.  在呼叫的程式碼，判斷哪些資料来傳遞至程序。  
  
2.  以一般方式，將資料呈現在引數清單中撰寫的程序呼叫。 請確定引數符合其中一個版本為程序定義中的參數清單。  
  
3.  您不需要以判斷要呼叫的程序的版本。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將控制項傳遞到符合的引數清單的版本。  
  
     下列範例會呼叫`post`程序宣告於[How to︰ 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)。 它會取得客戶識別碼、 判斷它是否為`String`或`Integer`，然後在任一情況下呼叫相同的程序。  
  
     [!code-vb[VbVbcnProcedures #&56;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures #&57;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [多載化程序](./procedure-overloading.md)   
 [疑難排解程序](./troubleshooting-procedures.md)   
 [如何︰ 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)   
 [如何︰ 多載使用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [如何︰ 多載使用不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [多載化程序的考量](./considerations-in-overloading-procedures.md)   
 [多載解析](./overload-resolution.md)   
 [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
