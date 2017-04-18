---
title: "如何︰ 將引數傳遞至程序 (Visual Basic) |Microsoft 文件"
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
- arguments [Visual Basic], passing to procedures
- procedures, arguments
- procedures, parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures, calling
- argument passing, procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: ddccd476b2347368d0435f637edf3882db306f45
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>如何：將引數傳遞至程序 (Visual Basic)
當您呼叫程序時，您可以依照括號括住的引數清單的程序名稱。 您會提供引數對應至每個必要參數的程序定義，而您可以選擇性地提供引數`Optional`參數。 如果您未提供`Optional`中呼叫的參數，您必須包含一個逗號，以標記引數清單中的位置，如果您提供的任何後續的引數。  
  
 如果您想要傳遞引數的資料型別不同於其對應的參數，例如`Byte`至`String`，您可以設定的型別檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 至`Off`。 如果`Option Strict`是`On`，您必須使用擴展轉換或明確轉換的關鍵字。 如需詳細資訊，請參閱[擴大和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和[類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
  
 如需詳細資訊，請參閱[程序參數和引數](./procedure-parameters-and-arguments.md)。  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>若要將一個或多個引數傳遞至程序  
  
1.  在呼叫的陳述式，請依照下列程序名稱，加上括弧。  
  
2.  放在括號內的引數清單。 包含引數，每個必要參數定義程序，並以逗號分隔的引數。  
  
3.  請確定每個引數是有效的運算式評估為資料類型轉換成程序的型別定義為對應參數。  
  
4.  如果參數定義成[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)，您可以將它包含引數清單中，或省略它。 如果您省略它，此程序會使用定義為該參數的預設值。  
  
5.  如果您省略引數`Optional`參數且沒有另一個參數之後的參數清單中，您可以省略引數的位置標記引數清單中額外的逗號。  
  
     下列範例會呼叫[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
     [!code-vb[VbVbcnProcedures #&34;](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     上述範例，提供必要的第一個引數，也就是要顯示的訊息字串。 它省略引數為選擇性的第二個參數，指定要顯示在訊息方塊上的按鈕。 呼叫不會提供一個值，因為`MsgBox`會使用預設值， `MsgBoxStyle.OKOnly`，這只會顯示**確定** 按鈕。  
  
     引數清單中的第二個逗號標示省略第二個引數的位置和最後一個字串傳遞給選擇性第三個參數`MsgBox`，這是顯示在標題列中的文字。  
  
## <a name="see-also"></a>另請參閱  
 [Sub 程序](./sub-procedures.md)   
 [Function 程序](./function-procedures.md)   
 [Property 程序](./property-procedures.md)   
 [運算子程序](./operator-procedures.md)   
 [如何︰ 定義程序參數](./how-to-define-a-parameter-for-a-procedure.md)   
 [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md)   
 [遞迴程序](./recursive-procedures.md)   
 [多載化程序](./procedure-overloading.md)   
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [物件導向程式設計](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
