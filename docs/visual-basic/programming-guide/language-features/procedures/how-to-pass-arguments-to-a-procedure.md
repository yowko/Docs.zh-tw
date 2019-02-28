---
title: HOW TO：將引數傳遞至程序 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 0bc7c9d09922b7fbef534e6b58389ca343cc1e13
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974389"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>HOW TO：將引數傳遞至程序 (Visual Basic)
當您呼叫程序時，您會遵循括號括住的引數清單的程序名稱。 您提供的程序定義，對應至每個必要參數的引數，您可以選擇性地提供的引數`Optional`參數。 如果您未提供`Optional`呼叫中的參數，您必須包含逗號來標示其引數清單中的位置，如果您提供的任何後續的引數。  
  
 如果您想要傳遞的資料型別引數不同於其對應的參數，例如`Byte`要`String`，您可以設定的類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 以`Off`。 如果`Option Strict`是`On`，您必須使用擴展轉換或明確轉換的關鍵字。 如需詳細資訊，請參閱 < [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)並[型別轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
  
 如需詳細資訊，請參閱 <<c0> [ 程序參數和引數](./procedure-parameters-and-arguments.md)。  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>若要將一或多個引數傳遞至程序  
  
1.  在呼叫的陳述式，請依照下列程序名稱，加上括弧。  
  
2.  放在括號內的引數清單。 包含程序會定義，每個必要參數的引數，並以逗號分隔的引數。  
  
3.  請確定每個引數是有效的運算式評估為型別程序的資料類型轉換為定義的對應參數。  
  
4.  如果參數定義成[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)，您可以將它包含引數清單中，或加以省略。 如果您省略它，則程序會使用定義為該參數的預設值。  
  
5.  如果您省略的引數`Optional`參數且沒有另一個參數後的參數清單中，您可以將省略的引數取代標記透過額外的逗號，引數清單中。  
  
     下列範例會呼叫 Visual Basic<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式。  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     上述範例中提供必要的第一個引數，這是要顯示的訊息字串。 它會省略選擇性的第二個參數，指定要顯示在訊息方塊上的按鈕的引數。 呼叫未提供值，因為`MsgBox`會使用預設值`MsgBoxStyle.OKOnly`，這只會顯示**確定** 按鈕。  
  
     第二個引數清單中的逗號會將標示省略第二個引數的位置和最後一個字串傳遞給選擇性第三個參數`MsgBox`，這是要顯示的標題列中的文字。  
  
## <a name="see-also"></a>另請參閱

- [Sub 程序](./sub-procedures.md)
- [函式程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [如何：如需程序來定義參數](./how-to-define-a-parameter-for-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [遞迴程序](./recursive-procedures.md)
- [程序多載化](./procedure-overloading.md)
- [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [物件導向程式設計 (Visual Basic)](../../concepts/object-oriented-programming.md)
