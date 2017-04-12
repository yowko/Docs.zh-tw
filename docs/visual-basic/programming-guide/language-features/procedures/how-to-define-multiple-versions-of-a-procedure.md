---
title: "如何︰ 定義程序 (Visual Basic) 的多個版本 |Microsoft 文件"
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
- procedures, defining
- Visual Basic code, procedures
- procedures, overloading
- procedures, multiple versions
- procedure overloading, multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
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
ms.openlocfilehash: 0228083ce00a0f552227fd7ae8f0f5a24f65148e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>如何：定義程序的多個版本 (Visual Basic)
您可以定義程序中由多個版本*多載*它使用相同名稱但不同的參數清單，每個版本。 多載的用途是定義數個版本密切相關的程序而不需要名稱區隔它們。  
  
 如需詳細資訊，請參閱[程序多載](./procedure-overloading.md)。  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>若要定義程序的多個版本  
  
1.  撰寫`Sub`或`Function`宣告陳述式，您想要定義的程序的每個版本。 每個宣告中使用相同的程序名稱。  
  
2.  在前面`Sub`或`Function`關鍵字與每個宣告中的[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。 您可以選擇性地略過`Overloads`在宣告中，但包含在任何宣告，您必須將它納入每個宣告。  
  
3.  每個宣告陳述式後面，撰寫程序程式碼以處理呼叫的程式碼提供的比對該版本的參數清單的引數的特定情況。 您不必測試呼叫程式碼已提供的參數。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將控制項傳遞到符合您的程序的版本。  
  
4.  終止的程序的每個版本`End Sub`或`End Function`視陳述式。  
  
## <a name="example"></a>範例  
 下列範例會定義`Sub`張貼客戶的平衡一筆交易的程序。 它會使用`Overloads`關鍵字來定義兩個版本的程序，可接受的名稱，而另一個客戶的帳戶號碼。  
  
 [!code-vb[VbVbcnProcedures #&72;](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 呼叫程式碼可以取得客戶識別為`String`或`Integer`，然後在任一情況下使用相同的呼叫陳述式。  
  
 如需如何呼叫這些版本資訊`post`程序，請參閱[如何︰ 呼叫多載程序](./how-to-call-an-overloaded-procedure.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請確定每個多載版本都有相同的程序名稱，但有不同的參數清單。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [疑難排解程序](./troubleshooting-procedures.md)   
 [如何︰ 多載使用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [如何︰ 多載使用不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [多載化程序的考量](./considerations-in-overloading-procedures.md)   
 [多載解析](./overload-resolution.md)
