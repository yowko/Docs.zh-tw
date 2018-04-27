---
title: 如何：定義程序的多個版本 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6db075e9b31355d4a0a593040b1fe7c96a0c730
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>如何：定義程序的多個版本 (Visual Basic)
您可以定義程序中由多個版本*多載*它使用相同名稱但不同的參數清單，每個版本。 多載的用途是定義程序的數個密切相關的版本，而不需要加以區分名稱。  
  
 如需詳細資訊，請參閱[程序多載](./procedure-overloading.md)。  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>若要定義多個版本的程序  
  
1.  寫入`Sub`或`Function`您想要定義的程序的每個版本的宣告陳述式。 每個宣告中使用相同的程序名稱。  
  
2.  在前面`Sub`或`Function`關鍵字與每個宣告中的[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。 您可以選擇性地省略`Overloads`在宣告中，但包含在任何宣告，必須將它包含在每個宣告中。  
  
3.  每個宣告陳述式後面，撰寫程序程式碼以處理呼叫的程式碼提供的比對該版本的參數清單的引數的特定情況。 您不必測試呼叫的程式碼已提供的參數。 Visual Basic 會將控制項傳遞至程序的版本相符。  
  
4.  終止與程序的每個版本`End Sub`或`End Function`視陳述式。  
  
## <a name="example"></a>範例  
 下列範例會定義`Sub`張貼客戶餘額一筆交易的程序。 它會使用`Overloads`關鍵字來定義兩個版本的程序，一次可接受依名稱和其他客戶的帳戶號碼。  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 呼叫程式碼可以取得客戶識別為`String`或`Integer`，然後在任一情況下使用相同的呼叫陳述式。  
  
 如需有關如何呼叫這些版本資訊`post`程序，請參閱[如何： 呼叫多載程序](./how-to-call-an-overloaded-procedure.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請確定每個多載版本都有相同的程序名稱，但不同的參數清單。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [程序的疑難排解](./troubleshooting-procedures.md)  
 [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)  
 [多載解析](./overload-resolution.md)
