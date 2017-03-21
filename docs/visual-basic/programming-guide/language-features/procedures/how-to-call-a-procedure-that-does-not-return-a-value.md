---
title: "如何︰ 呼叫不傳回值 (Visual Basic) 的程序 |Microsoft 文件"
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
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
ms.openlocfilehash: 17b2b902f3ee6ab79b2614b7742aa08fefab2420
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>如何：呼叫不傳回值的程序 (Visual Basic)
A`Sub`程序不會傳回呼叫程式碼的值。 明確呼叫它，以獨立的呼叫陳述式。 您無法直接使用其名稱在運算式中的呼叫它。  
  
### <a name="to-call-a-sub-procedure"></a>若要呼叫子函數程序  
  
1.  指定的名稱`Sub`程序。  
  
2.  請依照下列程序名稱以括號括住的引數清單。 如果不有任何引數，您可以省略括號。 不過，使用括號會讓您的程式碼容易閱讀。  
  
3.  將引數放在括號，以逗號分隔的引數清單。 確定您提供的相同順序的引數，`Sub`程序定義對應的參數。  
  
     下列範例會呼叫[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>函式來啟動應用程式視窗。</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>使用視窗標題做為其唯一引數。</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 它不會傳回呼叫程式碼的值。 如果未執行 「 記事本 」 處理程序，則會擲回<xref:System.ArgumentException>.</xref:System.ArgumentException> `Shell`程序假設應用程式中指定的路徑。  
  
     [!code-vb[VbVbalrCatRef #&11;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A></xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:System.ArgumentException></xref:System.ArgumentException>   
 [程序](./index.md)   
 [Sub 程序](./sub-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [如何︰ 建立程序](./how-to-create-a-procedure.md)   
 [如何︰ 呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)   
 [如何︰ 在 Visual Basic 中呼叫事件處理常式](./how-to-call-an-event-handler.md)
