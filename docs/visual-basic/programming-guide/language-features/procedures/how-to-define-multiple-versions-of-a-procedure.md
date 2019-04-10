---
title: HOW TO：定義多個版本的程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: fc7a8e18394b904f0c22a80f71dee091d4f786ab
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324028"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>HOW TO：定義多個版本的程序 (Visual Basic)
您可以在多個版本中所定義的程序*多載*它針對每個版本使用相同名稱但不同的參數清單。 多載的用途是定義程序的數個密切相關的版本，而不需要依名稱加以區隔。  
  
 如需詳細資訊，請參閱 [Procedure Overloading](./procedure-overloading.md)。  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>若要定義多個版本的程序  
  
1. 撰寫`Sub`或`Function`宣告陳述式，針對您想要定義的程序的每個版本。 在每個宣告中使用相同的程序名稱。  
  
2. 在前面`Sub`或是`Function`在每個宣告中的關鍵字[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。 您可以選擇性地省略`Overloads`在宣告中，但包含在任何宣告，您必須將它包含在每個宣告。  
  
3. 每個宣告陳述式後面，撰寫程序程式碼以處理呼叫的程式碼提供的比對該版本的參數清單的引數的特定情況。 您不必測試呼叫程式碼已提供的參數。 Visual Basic 會將控制項傳遞至您的程序版本相符。  
  
4. 終止此程序的每個版本`End Sub`或`End Function`適當的陳述式。  
  
## <a name="example"></a>範例  
 下列範例會定義`Sub`張貼對客戶的餘額交易的程序。 它會使用`Overloads`關鍵字來定義兩個版本的程序，可接受由名稱和其他客戶的帳戶號碼。  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 呼叫端程式碼可以取得客戶識別為`String`或`Integer`，然後在任一情況下使用相同的呼叫陳述式。  
  
 如需如何呼叫這些版本資訊`post`程序，請參閱[How to:呼叫多載程序](./how-to-call-an-overloaded-procedure.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請確定每個多載的版本具有相同的程序名稱，但有不同的參數清單。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [針對程序進行疑難排解](./troubleshooting-procedures.md)
- [HOW TO：多載使用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [HOW TO：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載程序的考量](./considerations-in-overloading-procedures.md)
- [Overload Resolution](./overload-resolution.md)
