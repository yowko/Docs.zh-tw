---
title: HOW TO：多載的程序會接受選擇性參數 (Visual Basic)
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
ms.openlocfilehash: 070d641d5a8b683ddfe06039117cc4a8507102df
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827624"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>HOW TO：多載的程序會接受選擇性參數 (Visual Basic)
如果程序中的一或多個[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數，您不能定義比對任何其隱含的多載的多載的版本。 如需詳細資訊，請參閱 < 隱含多載的選擇性參數 」 中[多載化程序中的考量](./considerations-in-overloading-procedures.md)。  
  
## <a name="one-optional-parameter"></a>一個選擇性參數  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>若要多載會接受一個選擇性參數的程序  
  
1.  撰寫`Sub`或`Function`參數清單中包含選擇性參數的宣告陳述式。 請勿使用`Optional`在這個多載的版本中的關鍵字。  
  
2.  在前面`Sub`或是`Function`關鍵字搭配[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。  
  
3.  撰寫呼叫程式碼提供的選擇性引數時，應該執行的程序程式碼。  
  
4.  終止此程序`End Sub`或`End Function`適當的陳述式。  
  
5.  撰寫等同於第一個宣告不同之處在於它不包含選擇性的參數在參數清單中的第二個宣告陳述式。  
  
6.  撰寫呼叫程式碼中未提供選擇性的引數時應該執行的程序程式碼。 終止此程序`End Sub`或`End Function`適當的陳述式。  
  
     下列範例顯示具有選擇性參數，對等設定兩個多載程序，以及最後的範例不正確且有效的多載版本定義的程序。  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>多個選用參數  
 一個以上的選擇性參數的程序，您通常需要兩個以上的多載的版本。 例如，如果有兩個選擇性參數，而且呼叫程式碼可以提供或省略每個彼此獨立，您會需要四個多載的版本，一個用於每個可能的組合，提供的引數。  
  
 選擇性的參數數目增加時，會增加複雜度的多載。 某些組合提供的引數不是可接受的除非 N 選擇性參數要為 2 ^ N 多載版本。 根據程序的本質，您可能會發現清楚的邏輯靠右對齊多花費一些心力定義所有多載的版本。  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>若要多載會接受一個以上的選擇性參數的程序  
  
1.  判斷哪些組合提供的選擇性引數是可接受的程序的邏輯。 一個選擇性參數相依於另一個時，可能導致無法接受的組合。 比方說，如果有一個參數接受配偶的名稱，而另一個接受配偶的時代，是無法接受的引數提供的時代，但省略名稱組合。  
  
2.  針對提供的選擇性引數的每個可接受的組合，撰寫`Sub`或`Function`定義對應的參數清單的宣告陳述式。 請勿使用`Optional`關鍵字。  
  
3.  在每個宣告中，在前面`Sub`或是`Function`關鍵字搭配[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。  
  
4.  下列每個宣告中，寫入時呼叫的程式碼提供與該宣告的參數清單中對應的引數清單執行的程序程式碼。  
  
5.  終止與每個程序`End Sub`或`End Function`適當的陳述式。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [選擇性參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [程序多載化](./procedure-overloading.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義多個版本的程序](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：多載不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載解析](./overload-resolution.md)
