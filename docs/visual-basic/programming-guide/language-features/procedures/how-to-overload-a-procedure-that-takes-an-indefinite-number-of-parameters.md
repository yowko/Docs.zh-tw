---
title: HOW TO：多載不定數目參數 (Visual Basic) 的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: bae420e88a74fbe3f7e8ad3592133fdcaf191029
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838985"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>HOW TO：多載不定數目參數 (Visual Basic) 的程序
如果程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，您不能定義採用的參數陣列的一維陣列的多載的版本。 如需詳細資訊，請參閱 「 隱含多載的參數陣列參數 」 中[多載化程序中的考量](./considerations-in-overloading-procedures.md)。  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>若要多載接受各種數目參數的程序  
  
1.  確認此程序與呼叫程式碼邏輯方面，從多載版本，從多個`ParamArray`參數。 請參閱中的 < 多載和參數陣列 >[多載化程序的考量](./considerations-in-overloading-procedures.md)。  
  
2.  判斷程序應該接受的提供值的數字中變數參數清單的一部分。 這可能包括的任何值，大小寫，且它可能包含單一的一維陣列的大小寫。  
  
3.  針對每個可接受提供的值數目，撰寫`Sub`或`Function`定義對應的參數清單的宣告陳述式。 請勿使用`Optional`或`ParamArray`在這個多載的版本中的關鍵字。  
  
4.  在每個宣告中，在前面`Sub`或是`Function`關鍵字搭配[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。  
  
5.  下列每個宣告中，撰寫呼叫程式碼提供與該宣告的參數清單的對應值時執行的程序程式碼。  
  
6.  終止與每個程序`End Sub`或`End Function`適當的陳述式。  
  
## <a name="example"></a>範例  
 下列範例示範使用定義的程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，然後按一下 對等一組多載程序。  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 您無法多載會採用參數陣列的一維陣列的參數清單的這類的程序。 不過，您可以使用其他隱含的多載的簽章。 下列宣告將說明這點。  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 若要測試是否呼叫程式碼提供一個或多個值並沒有多載的版本中的程式碼`ParamArray`參數，或如果是的話，多少。 Visual Basic 會將控制項傳遞至比對呼叫的引數清單的版本。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 因為程序時使用`ParamArray`參數相當於一組多載版本，您無法多載，這樣的程序對應到任何這些隱含的多載的參數清單。 如需詳細資訊，請參閱 <<c0> [ 多載化程序中的考量](./considerations-in-overloading-procedures.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 每當您處理陣列，其中可能會無限期地大，會有風險的造成滿溢內部應用程式的容量。 如果您接受參數陣列時，您應該測試呼叫程式碼傳遞給它，陣列的長度，並採取適當的步驟，如果它是對您的應用程式而言太大。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [選擇性參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [程序多載化](./procedure-overloading.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義多個版本的程序](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：多載會採用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [多載解析](./overload-resolution.md)
