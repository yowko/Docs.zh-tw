---
title: 如何：呼叫不傳回值的程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: cf136f1486645d6e8e4b5856c0b1baf9e99f6c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649044"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>如何：呼叫不傳回值的程序 (Visual Basic)
A`Sub`程序不會傳回呼叫程式碼的值。 明確呼叫它，以獨立的呼叫陳述式。 您無法只使用其名稱，在運算式中的呼叫它。  
  
### <a name="to-call-a-sub-procedure"></a>若要呼叫 Sub 程序  
  
1.  指定的名稱`Sub`程序。  
  
2.  請依照下列程序名稱與括號來括住的引數清單。 如果有任何引數，您可以選擇性地省略括號。 不過，使用括號可讓您的程式碼更方便閱讀。  
  
3.  將引數放在括號，並以逗號分隔的引數清單。 確定您提供的相同順序的引數，`Sub`程序所定義的對應參數。  
  
     下列範例會呼叫 Visual Basic<xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>函式可啟動應用程式視窗。 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 使用視窗標題做為其唯一的引數。 呼叫程式碼不會傳回值。 如果未執行 「 記事本 」 處理程序，此範例會擲回<xref:System.ArgumentException>。 `Shell`程序會假設應用程式是在指定的路徑。  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [程序](./index.md)  
 [Sub 程序](./sub-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [如何：建立程序](./how-to-create-a-procedure.md)  
 [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)  
 [如何： 在 Visual Basic 中呼叫事件處理常式](./how-to-call-an-event-handler.md)
