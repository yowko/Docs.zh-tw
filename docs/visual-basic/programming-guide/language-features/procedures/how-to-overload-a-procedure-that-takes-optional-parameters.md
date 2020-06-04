---
title: 如何：使用選擇性參數的多載程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 9ae6818b1e03ccd00ed554e98690e02ffa45de99
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387838"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>如何：多載使用選擇性參數的程序 (Visual Basic)
如果程式有一或多個[選擇性](../../../language-reference/modifiers/optional.md)參數，您就無法定義多載版本來符合它的任何隱含多載。 如需詳細資訊，請參閱多載[程式的考慮](./considerations-in-overloading-procedures.md)中的「選擇性參數的隱含多載」。  
  
## <a name="one-optional-parameter"></a>一個選擇性參數  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>若要多載採用一個選擇性參數的程式  
  
1. 撰寫一個 `Sub` 或宣告 `Function` 語句，其中包含參數清單中的選擇性參數。 請勿在此多載的 `Optional` 版本中使用關鍵字。  
  
2. 在或關鍵字之前加上 `Sub` `Function` [Overloads](../../../language-reference/modifiers/overloads.md)關鍵字。  
  
3. 撰寫當呼叫程式碼提供選擇性引數時應執行的程式碼。  
  
4. `End Sub` `End Function` 視需要使用或語句來終止程式。  
  
5. 撰寫與第一個宣告相同的第二個宣告語句，不同之處在于它不會在參數清單中包含選擇性參數。  
  
6. 撰寫當呼叫程式碼未提供選擇性引數時，應執行的程式碼。 `End Sub` `End Function` 視需要使用或語句來終止程式。  
  
     下列範例顯示的程式是以選擇性參數、一組對等的兩個多載程式來定義，最後是無效和有效的多載版本的範例。  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>多個選擇性參數  
 針對具有多個選擇性參數的程式，您通常需要兩個以上的多載版本。 例如，如果有兩個選擇性參數，而且呼叫程式碼可以單獨提供或省略彼此，則您需要四個多載版本，每個可能的提供引數組合一個。  
  
 當選擇性參數數目增加時，多載的複雜度會增加。 除非提供的引數組合無法接受，否則針對 N 個選擇性參數，您需要 2 ^ N 個多載版本。 視程式的本質而定，您可能會發現邏輯的清楚，是要定義所有多載版本的額外工作。  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>若要多載接受一個以上選用參數的程式  
  
1. 判斷程式邏輯可以接受哪些提供的選擇性引數組合。 如果一個選擇性參數相依于另一個，則可能會發生無法接受的組合。 例如，如果一個參數接受個人名稱，另一個則接受該人員的年齡，則提供年齡但省略名稱的引數組合就無法接受。  
  
2. 針對所提供之選擇性引數的每個可接受組合，撰寫 `Sub` `Function` 定義對應參數清單的或宣告語句。 請勿使用 `Optional` 關鍵字。  
  
3. 在每個宣告中，在或關鍵字前面加上 `Sub` `Function` [Overloads](../../../language-reference/modifiers/overloads.md)關鍵字。  
  
4. 遵循每個宣告，撰寫呼叫程式碼提供對應至該宣告之參數清單的引數清單時，應執行的程式碼。  
  
5. `End Sub`視需要使用或語句來終止每個程式 `End Function` 。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [選擇性參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [程序多載化](./procedure-overloading.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載解析](./overload-resolution.md)
