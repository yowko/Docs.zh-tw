---
title: "遞迴程序 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 444eeaf043cf3710c5154fd7e8577590e3ce7d1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="recursive-procedures-visual-basic"></a>遞迴程序 (Visual Basic)
A*遞迴*程序會呼叫本身。 一般情況下，這不是最有效方式寫入[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式碼。  
  
 下列程序會使用遞迴，計算其原始的引數的階乘。  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>遞迴程序的考量  
 **限制條件**。 您必須設計遞迴程序以測試可以終止遞迴的至少一個條件，而且您也必須處理在合理的遞迴呼叫數內滿足任何這類狀況，其中的情況。 至少一個可以失敗不符合的條件，您的程序會執行在無限迴圈中執行的高風險。  
  
 **記憶體使用量**。 您的應用程式具有有限的本機變數的空間。 每次程序呼叫本身，它會使用更多空間其區域變數的額外複本。 如果會無限期繼續此程序，它最終會導致<xref:System.StackOverflowException>錯誤。  
  
 **效率**。 您幾乎可以取代遞迴迴圈。 迴圈沒有傳遞引數，初始化其他存放裝置，並傳回值的額外負荷。 您的效能可能會比較好沒有遞迴呼叫。  
  
 **相互遞迴**。 您可能發現很差的效能或甚至無限迴圈，如果兩個程序彼此呼叫。 此種設計顯示與單一遞迴程序的相同問題，但可能更難偵測及偵錯。  
  
 **以括號呼叫**。 當`Function`程序呼叫本身以遞迴方式，您必須請依照下列程序名稱，加上括弧，即使沒有引數清單。 否則，函式名稱會以表示函式的傳回值。  
  
 **測試**。 如果您撰寫的遞迴程序時，應該先確定它永遠符合某些限制狀況非常仔細地測試它。 您也應該確定您有太多的遞迴呼叫，因為記憶體不足無法執行。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.StackOverflowException>  
 [程序](./index.md)  
 [Sub 程序](./sub-procedures.md)  
 [函式程序](./function-procedures.md)  
 [屬性程序](./property-procedures.md)  
 [運算子程序](./operator-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [程序多載化](./procedure-overloading.md)  
 [程序的疑難排解](./troubleshooting-procedures.md)  
 [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [疑難排解例外狀況：System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
