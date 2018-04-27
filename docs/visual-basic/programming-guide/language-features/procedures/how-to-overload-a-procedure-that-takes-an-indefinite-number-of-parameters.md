---
title: 如何：多載使用不定數目參數的程序 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cb4faa2dfd01f854dcc3bf8c2a330adf5acdcac
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>如何：多載使用不定數目參數的程序 (Visual Basic)
如果程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，您不能定義接受參數陣列的一維陣列的多載的版本。 如需詳細資訊，請參閱 「 隱含多載的參數陣列參數 」[中多載化程序的考量](./considerations-in-overloading-procedures.md)。  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>若要多載使用不定數目參數的程序  
  
1.  確定此程序與呼叫程式碼邏輯受惠於多載版本，從多個`ParamArray`參數。 請參閱中的 < 多載和參數陣列 >[中多載程序的考量](./considerations-in-overloading-procedures.md)。  
  
2.  判斷哪些數字提供值的程序應該接受在參數清單的變數。 這可能包括的任何值，大小寫，且它可能包含單一的一維陣列的大小寫。  
  
3.  對於每個可接受提供的值數目，撰寫`Sub`或`Function`定義對應的參數清單的宣告陳述式。 請勿使用`Optional`或`ParamArray`關鍵字，在這個多載版本。  
  
4.  在每個宣告中前,`Sub`或`Function`關鍵字搭配[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。  
  
5.  下列每個宣告中，撰寫呼叫的程式碼提供與該宣告的參數清單的對應值時應該執行的程序程式碼。  
  
6.  終止與每個程序`End Sub`或`End Function`視陳述式。  
  
## <a name="example"></a>範例  
 下列範例顯示定義的程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，然後再對等一組多載程序。  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 您無法多載會採用參數陣列的一維陣列的參數清單具有這類的程序。 不過，您可以使用其他隱含多載的簽章。 下列宣告來說明這點。  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 若要測試是否呼叫的程式碼提供一個或多個值沒有多載的版本中的程式碼`ParamArray`參數，或如果是這樣，多少。 Visual Basic 會將控制項傳遞至比對呼叫的引數清單的版本。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 因為程序時使用`ParamArray`參數相當於一組多載版本，您無法多載，這種程序對應至任何這些隱含的多載參數清單。 如需詳細資訊，請參閱[中多載化程序的考量](./considerations-in-overloading-procedures.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 只要處理陣列，其中可能會無限期地大，會有風險的造成滿溢內部應用程式的容量。 如果您接受參數陣列，您應該測試呼叫的程式碼傳遞給它，陣列的長度，並採取適當的步驟，是否對您的應用程式而言太大。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [選擇性參數](./optional-parameters.md)  
 [參數陣列](./parameter-arrays.md)  
 [程序多載化](./procedure-overloading.md)  
 [程序的疑難排解](./troubleshooting-procedures.md)  
 [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)  
 [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)  
 [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [多載解析](./overload-resolution.md)
