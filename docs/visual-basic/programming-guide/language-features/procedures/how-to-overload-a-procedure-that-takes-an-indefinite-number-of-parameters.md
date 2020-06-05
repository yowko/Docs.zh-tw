---
title: 如何：多載使用不確定參數數目的程序
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
ms.openlocfilehash: ddff8c8cd82593b7d89fb0847e56123c287e364b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387877"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>如何：多載使用不定數目參數的程序 (Visual Basic)
如果程式具有[ParamArray](../../../language-reference/modifiers/paramarray.md)參數，您就無法為參數陣列定義接受一維陣列的多載版本。 如需詳細資訊，請參閱多載[程式的考慮](./considerations-in-overloading-procedures.md)中的「ParamArray 參數的隱含多載」。  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>若要多載採用可變數目參數的程式  
  
1. 確定程式和呼叫程式碼邏輯從多載版本中獲益，而不是從 `ParamArray` 參數。 請參閱多載[程式的考慮](./considerations-in-overloading-procedures.md)中的「多載和 ParamArrays」。  
  
2. 判斷程式應在參數清單的變數部分中接受的提供值數目。 這可能包括不含任何值的案例，而且可能包含單一一維陣列的大小寫。  
  
3. 針對每個可接受的提供值數目， `Sub` 撰寫 `Function` 定義對應參數清單的或宣告語句。 請勿在此多載 `Optional` `ParamArray` 版本中使用或關鍵字。  
  
4. 在每個宣告中，在或關鍵字前面加上 `Sub` `Function` [Overloads](../../../language-reference/modifiers/overloads.md)關鍵字。  
  
5. 在每個宣告後面，撰寫呼叫程式碼提供對應至該宣告之參數清單的值時，應執行的程式碼。  
  
6. `End Sub`視需要使用或語句來終止每個程式 `End Function` 。  
  
## <a name="example"></a>範例  
 下列範例顯示使用[ParamArray](../../../language-reference/modifiers/paramarray.md)參數定義的程式，然後是一組對等的多載程式。  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 您無法使用參數清單來多載這類程式，其中會採用一維陣列做為參數陣列。 不過，您可以使用其他隱含多載的簽章。 下列宣告說明這種情況。  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 多載版本中的程式碼不需要測試呼叫程式碼是否提供參數的一個或多個值 `ParamArray` ，如果有的話，也不需這麼做。 Visual Basic 會將控制權傳遞至符合呼叫引數清單的版本。  
  
## <a name="compile-the-code"></a>編譯程式碼  
 因為具有 `ParamArray` 參數的程式相當於一組多載版本，所以您無法使用對應至這些隱含多載的參數清單來多載這類程式。 如需詳細資訊，請參閱多載[程式的考慮](./considerations-in-overloading-procedures.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 當您處理可能會無限大的陣列時，會有 overrunning 應用程式的一些內部容量的風險。 如果您接受參數陣列，您應該測試呼叫的程式碼傳遞給它的陣列長度，如果對您的應用程式而言太大，則採取適當的步驟。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [選擇性參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [程序多載化](./procedure-overloading.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [多載解析](./overload-resolution.md)
