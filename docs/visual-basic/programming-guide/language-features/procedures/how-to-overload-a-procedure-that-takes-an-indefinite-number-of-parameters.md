---
title: "如何︰ 多載不定數目參數 (Visual Basic) 的程序 |Microsoft 文件"
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
- procedures, parameters
- procedure overloading, indefinite number of parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters
- procedures, overloading
- procedures, multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
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
ms.openlocfilehash: c7e09bd482e35c7ce7f28a6cc7de0379b7cc89f6
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>如何：多載使用不定數目參數的程序 (Visual Basic)
如果程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，您不能定義採取參數陣列的一維陣列的多載的版本。 如需詳細資訊，請參閱 「 隱含多載的參數陣列參數 」 中[中多載化程序的考量](./considerations-in-overloading-procedures.md)。  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>若要多載接受可變數目之參數的程序  
  
1.  確定此程序與呼叫程式碼邏輯也可利用多載版本，從多個`ParamArray`參數。 請參閱 < 多載和參數陣列"[多載化程序的考量](./considerations-in-overloading-procedures.md)。  
  
2.  決定程序應該接受的參數清單的變動部分的提供值的數目。 這可能包括大小寫的任何值，且可能包含單一的一維陣列的大小寫。  
  
3.  針對每個可接受提供的值數目，寫入`Sub`或`Function`宣告陳述式來定義對應的參數清單。 請勿使用 `Optional`或`ParamArray`這個多載版本中的關鍵字。  
  
4.  在每個宣告中前,`Sub`或`Function`關鍵字[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。  
  
5.  下列每個宣告，撰寫呼叫的程式碼提供與該宣告的參數清單的對應值時所應執行的程序程式碼。  
  
6.  終止與每個程序`End Sub`或`End Function`視陳述式。  
  
## <a name="example"></a>範例  
 下列範例顯示定義的程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，然後再組多載程序。  
  
 [!code-vb[VbVbcnProcedures #&69;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&70;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 您無法多載，這樣的程序的參數清單，會採用參數陣列的一維陣列。 不過，您可以使用其他隱含多載的簽章。 下列宣告可說明這點。  
  
 [!code-vb[VbVbcnProcedures #&71;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 若要測試是否呼叫的程式碼提供一個或多個值並沒有多載版本中的程式碼`ParamArray`參數，或如果是這樣，多少。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將控制項傳遞到符合呼叫的引數清單的版本。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 因為程序時使用`ParamArray`參數相當於一組多載版本，您無法多載，這樣的程序使用的參數清單，對應到任何這些隱含多載。 如需詳細資訊，請參閱[中多載化程序的考量](./considerations-in-overloading-procedures.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 只要處理陣列，其中可能會無限期地大，會造成您的應用程式內部容量滿溢的風險。 如果您接受參數陣列時，您應該測試呼叫程式碼傳遞給它，陣列的長度，並採取適當步驟，如果您的應用程式而言太大。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [選擇性參數](./optional-parameters.md)   
 [參數陣列](./parameter-arrays.md)   
 [多載化程序](./procedure-overloading.md)   
 [疑難排解程序](./troubleshooting-procedures.md)   
 [如何︰ 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)   
 [如何︰ 呼叫多載程序](./how-to-call-an-overloaded-procedure.md)   
 [如何︰ 多載使用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [多載解析](./overload-resolution.md)
