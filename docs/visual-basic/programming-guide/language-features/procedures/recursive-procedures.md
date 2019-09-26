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
ms.openlocfilehash: b08a06a07f134b7c95251848862d39339e59fe61
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274348"
---
# <a name="recursive-procedures-visual-basic"></a>遞迴程序 (Visual Basic)

*遞迴*程式是一種呼叫本身的程式。 一般來說，這不是撰寫 Visual Basic 程式碼最有效率的方式。  
  
 下列程式會使用遞迴來計算其原始引數的階乘。  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>遞迴程式的考慮

 **限制條件**。 您必須設計遞迴程式來測試至少一個可終止遞迴的條件，而且您也必須處理在合理數目的遞迴呼叫中不滿足這類條件的情況。 若沒有至少一個可以符合的條件而不會失敗，則您的程式會在無限迴圈中執行高風險。

 **記憶體使用量**。 您的應用程式對於本機變數的空間數量有限。 每次程式呼叫本身時，它會使用更多該空間來取得其區域變數的其他複本。 如果此程式會無限期地繼續，最後<xref:System.StackOverflowException>會造成錯誤。

 **效率**。 您幾乎可以將迴圈替換成遞迴。 迴圈不會有傳遞引數、初始化額外的儲存體和傳回值的額外負荷。 在沒有遞迴呼叫的情況下，您的效能可能更好。

 **相互遞迴**。 如果兩個程式彼此呼叫，您可能會發現效能不佳，甚至是無限迴圈。 這種設計會以單一遞迴程式的方式呈現相同的問題，但可能難以偵測和偵錯工具。

 **使用括弧呼叫**。 `Function`當程式以遞迴方式呼叫本身時，即使沒有引數清單，您也必須在程式名稱後面加上括弧。 否則，會採用函式名稱來表示函數的傳回值。

 **測試**。 如果您撰寫遞迴程式，您應該小心進行測試，確定它一定符合某些限制條件。 您也應該確保因為有太多遞迴呼叫而無法用盡記憶體。

## <a name="see-also"></a>另請參閱

- <xref:System.StackOverflowException>
- [程序](index.md)
- [Sub 程序](sub-procedures.md)
- [函式程序](function-procedures.md)
- [屬性程序](property-procedures.md)
- [運算子程序](operator-procedures.md)
- [程序參數和引數](procedure-parameters-and-arguments.md)
- [程序多載化](procedure-overloading.md)
- [程序的疑難排解](troubleshooting-procedures.md)
- [迴圈結構](../control-flow/loop-structures.md)
