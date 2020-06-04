---
title: 如何：將引數傳遞至程序
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
ms.openlocfilehash: 903e05facccd1f2afdf4bb51b200531feb64aa79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387773"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>如何：將引數傳遞至程序 (Visual Basic)
當您呼叫程式時，您會在括弧中的程式名稱後面加上引數清單。 您提供的引數會對應至程式所定義的每個必要參數，而且您可以選擇性地提供引數給 `Optional` 參數。 如果您未 `Optional` 在呼叫中提供參數，當您提供任何後續的引數時，必須包含逗號來將其位置標記在引數清單中。  
  
 如果您想要傳遞的資料類型引數與其對應的參數（例如）不同， `Byte` `String` 您可以將類型檢查參數（[Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)）設定為 `Off` 。 如果 `Option Strict` 是 `On` ，您就必須使用擴輾轉換或明確轉換關鍵字。 如需詳細資訊，請參閱[擴展和縮小轉換](../data-types/widening-and-narrowing-conversions.md)和[類型轉換](../../../language-reference/functions/type-conversion-functions.md)函式。  
  
 如需詳細資訊，請參閱程式[參數和引數](./procedure-parameters-and-arguments.md)。  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>將一個或多個引數傳遞至程式  
  
1. 在呼叫語句中，在程式名稱後面加上括弧。  
  
2. 在括弧內，放入引數清單。 包含程式所定義之每個必要參數的引數，並以逗號分隔引數。  
  
3. 請確定每個引數都是有效的運算式，它會評估為可轉換成該程式針對對應參數所定義之類型的資料類型。  
  
4. 如果將參數定義為[選擇性](../../../language-reference/modifiers/optional.md)，您可以將它包含在引數清單中，或將其省略。 如果您省略它，程式會使用針對該參數定義的預設值。  
  
5. 如果您省略某個參數的引數， `Optional` 且參數清單中有另一個參數，您可以在引數清單中，將省略的引數的位置標記為額外的逗號。  
  
     下列範例會呼叫 Visual Basic 函式 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 。  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     上述範例會提供必要的第一個引數，也就是要顯示的訊息字串。 它會省略選擇性第二個參數的引數，這會指定要在訊息方塊上顯示的按鈕。 因為呼叫不提供值，所以會 `MsgBox` 使用預設值， `MsgBoxStyle.OKOnly` 這只會顯示 **[確定]** 按鈕。  
  
     引數清單中的第二個逗號會標記省略的第二個引數的位置，而最後一個字串會傳遞至的選擇性第三個參數 `MsgBox` ，也就是要在標題列中顯示的文字。  
  
## <a name="see-also"></a>另請參閱

- [Sub 程序](./sub-procedures.md)
- [Function 程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [如何：定義程序的參數](./how-to-define-a-parameter-for-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [遞迴程序](./recursive-procedures.md)
- [程序多載化](./procedure-overloading.md)
- [物件和類別](../objects-and-classes/index.md)
- [物件導向程式設計 (Visual Basic)](../../concepts/object-oriented-programming.md)
