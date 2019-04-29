---
title: 遞迴程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: de9a2af9fc3cd78879b6525245727a6f52d51c63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791842"
---
# <a name="recursive-procedures-visual-basic"></a>遞迴程序 (Visual Basic)
A*遞迴*程序會呼叫其本身。 一般情況下，這不是撰寫 Visual Basic 程式碼的最有效方式。  
  
 下列程序會使用遞迴來計算其原始的引數的階乘。  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>遞迴程序的考量  
 **限制條件**。 您必須設計的遞迴程序，以測試可終止遞迴時，至少一個條件，而且您也必須處理在合理的遞迴呼叫數內中成立到任何這類條件的情況。 缺少至少一個可以在不失敗的情況下符合的條件，您的程序會執行無限迴圈中執行的較高的風險。  
  
 **記憶體使用量**。 您的應用程式具有本機變數的空間量有限。 每次程序呼叫本身，它會使用更多空間其本機變數的其他複本。 如果會無限期繼續此程序，它最終會導致<xref:System.StackOverflowException>時發生錯誤。  
  
 **效率**。 您幾乎可以取代遞迴迴圈。 迴圈並沒有傳遞引數，初始化其他的儲存體，並傳回值的額外負荷。 您的效能可能會遞迴呼叫沒有更好的。  
  
 **相互遞迴**。 您可能發現，效能非常低落或甚至是無限迴圈，如果兩個程序彼此呼叫。 此種設計呈現單一的遞迴程序中，相同的問題，但可以就很難偵測及偵錯。  
  
 **呼叫以括號**。 當`Function`程序呼叫本身以遞迴方式，您必須請依照下列程序名稱，加上括弧，即使沒有任何引數清單。 否則，函式名稱會視為函式的傳回值。  
  
 **測試**。 如果您撰寫遞迴程序，您應該測試它非常小心地以確定它一律符合某些限制狀況。 您也應該確定您無法執行太多遞迴呼叫，因為記憶體不足。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.StackOverflowException>
- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [函式程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [程序多載化](./procedure-overloading.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
