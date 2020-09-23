---
title: 如何：呼叫不傳回值的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 2686a4d9dc10cde209f558771feeb5ba4f4ccb21
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075001"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>如何：呼叫不傳回值的程序 (Visual Basic)

程式不 `Sub` 會傳回呼叫程式碼的值。 您可以使用獨立的呼叫語句來明確呼叫它。 您無法直接在運算式中使用其名稱來呼叫它。  
  
### <a name="to-call-a-sub-procedure"></a>若要呼叫 Sub 程式  
  
1. 指定程式的名稱 `Sub` 。  
  
2. 請以括弧括住程式名稱，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。 不過，使用括弧可讓您的程式碼更容易閱讀。  
  
3. 將引數清單中的引數放在括弧內，並以逗號分隔。 請務必以程式定義對應參數的相同順序提供引數 `Sub` 。  
  
     下列範例會呼叫 Visual Basic 函 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 式來啟用應用程式視窗。 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 將視窗標題作為其唯一引數。 它不會傳回值給呼叫程式碼。 如果「記事本」處理常式未執行，此範例會擲回 <xref:System.ArgumentException> 。 此 `Shell` 程式假設應用程式位於指定的路徑中。  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Sub 陳述式](../../../language-reference/statements/sub-statement.md)
- [如何：建立程序](./how-to-create-a-procedure.md)
- [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)
- [如何：在 Visual Basic 中呼叫事件處理常式](./how-to-call-an-event-handler.md)
