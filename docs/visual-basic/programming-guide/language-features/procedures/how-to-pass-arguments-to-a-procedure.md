---
title: "如何：將引數傳遞至程序 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3debb4fa6e7b15f9c321ef207d0cc04181a98da2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>如何：將引數傳遞至程序 (Visual Basic)
當您呼叫程序時，您會遵循括號括住的引數清單的程序名稱。 您會提供引數對應至每個必要參數的程序所定義，而您可以選擇性地提供的引數`Optional`參數。 如果您未提供`Optional`呼叫中的參數，您必須包含逗號來標示它的引數清單中的位置，如果您提供的任何後續的引數。  
  
 如果您想要傳遞的資料型別引數不同於其對應的參數，例如`Byte`至`String`，您可以設定類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 至`Off`。 如果`Option Strict`是`On`，您必須使用擴展轉換或明確轉換關鍵字。 如需詳細資訊，請參閱[擴大和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和[類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
  
 如需詳細資訊，請參閱[程序參數和引數](./procedure-parameters-and-arguments.md)。  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>若要將一個或多個引數傳遞至程序  
  
1.  在呼叫的陳述式，請依照下列程序名稱，加上括弧。  
  
2.  放在括弧內的引數清單。 包含一個引數的每個必要參數的程序所定義，並以逗號分隔的引數。  
  
3.  請確定每個引數是有效的運算式評估為資料類型轉換為型別程序定義的對應參數。  
  
4.  如果參數定義成[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)，您可以將它包含引數清單中，或加以省略。 如果您省略它，程序會使用該參數所定義的預設值。  
  
5.  如果您省略的引數`Optional`參數且沒有其他參數之後參數清單中，您可以標記多餘的逗號引數清單中省略的引數的位置。  
  
     下列範例會呼叫[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式。  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     上述範例中提供必要的第一個引數，這是要顯示的訊息字串。 它會省略選擇性的第二個參數，指定要顯示在訊息方塊上的按鈕的引數。 呼叫未提供值，因為`MsgBox`會使用預設值， `MsgBoxStyle.OKOnly`，這只會顯示**確定** 按鈕。  
  
     第二個引數清單中的逗號標示省略第二個引數的位置和最後一個的字串傳遞給選擇性第三個參數`MsgBox`，這是要顯示的標題列中的文字。  
  
## <a name="see-also"></a>另請參閱  
 [Sub 程序](./sub-procedures.md)  
 [函式程序](./function-procedures.md)  
 [屬性程序](./property-procedures.md)  
 [運算子程序](./operator-procedures.md)  
 [如何：定義程序的參數](./how-to-define-a-parameter-for-a-procedure.md)  
 [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)  
 [遞迴程序](./recursive-procedures.md)  
 [程序多載化](./procedure-overloading.md)  
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [物件導向程式設計](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
