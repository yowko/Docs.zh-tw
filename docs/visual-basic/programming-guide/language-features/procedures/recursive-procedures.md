---
title: "遞迴程序 (Visual Basic) |Microsoft 文件"
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
- Visual Basic code, procedures
- procedures, that call themselves
- procedures, recursive
- procedures, calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
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
ms.openlocfilehash: 9fc95cd5f7cfd5637f6282c6ef571eb81bac1816
ms.lasthandoff: 03/13/2017

---
# <a name="recursive-procedures-visual-basic"></a>遞迴程序 (Visual Basic)
A*遞迴*程序會呼叫本身。 一般而言，這不是最有效方式撰寫[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼。  
  
 下列程序會使用遞迴來計算其原始的引數的階乘。  
  
 [!code-vb[VbVbcnProcedures #&51;](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>遞迴程序的考量  
 **限制條件**。 您必須設計遞迴程序來測試可終止遞迴，至少一個條件，您也必須處理中沒有這類條件滿足，則在合理的遞迴呼叫數內的情況。 沒有至少一個可以失敗不符合的條件，您的程序會執行無限迴圈中執行的較高的風險。  
  
 **記憶體使用量**。 您的應用程式具有有限的空間供區域變數。 每次程序呼叫本身，它會使用更多空間其區域變數的額外複本。 如果此程序會無限期地繼續，則最後會導致<xref:System.StackOverflowException>錯誤。</xref:System.StackOverflowException>  
  
 **效率**。 您幾乎可以取代遞迴迴圈。 迴圈並沒有傳遞引數，初始化其他儲存體，並傳回值的額外負荷。 您的效能可能沒有遞迴呼叫大幅提升。  
  
 **相互遞迴**。 您可能發現，效能非常低落或甚至無限迴圈，如果兩個程序彼此呼叫。 此種設計顯示單一遞迴程序中，相同的問題，但可以就很難偵測及偵錯。  
  
 **以括號呼叫**。 當`Function`程序會呼叫自己，以遞迴方式，您必須遵循的程序名稱，加上括弧，即使沒有任何引數清單。 否則，函式名稱會視為函式的傳回值。  
  
 **測試**。 如果您撰寫遞迴程序，應該先確認它永遠符合部分的限制條件非常仔細地測試它。 您也應該確定您無法執行因為有太多遞迴呼叫的記憶體不足。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.StackOverflowException></xref:System.StackOverflowException>   
 [程序](./index.md)   
 [Sub 程序](./sub-procedures.md)   
 [Function 程序](./function-procedures.md)   
 [Property 程序](./property-procedures.md)   
 [運算子程序](./operator-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [多載化程序](./procedure-overloading.md)   
 [疑難排解程序](./troubleshooting-procedures.md)   
 [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [疑難排解例外狀況：System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
