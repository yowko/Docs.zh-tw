---
title: 如何：宣告混合存取層級的屬性
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: 78363f7b2fb5b251f7409e53b2802baf83b05810
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072700"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>如何：宣告混合存取層級的屬性 (Visual Basic)

如果您想要 `Get` `Set` 屬性上的和程式具有不同的存取層級，您可以在語句中使用較寬鬆的層級， `Property` 並在或語句中使用更嚴格的層級 `Get` `Set` 。 當您想要讓程式碼的某些部分能夠取得屬性的值，以及程式碼的某些其他部分能夠變更值時，您可以在屬性上使用混合存取層級。  
  
 如需存取層級的詳細資訊，請參閱 [Visual Basic 中的存取層級](../declared-elements/access-levels.md)。  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>宣告混合存取層級的屬性  
  
1. 以一般方式宣告屬性，並指定較不嚴格的存取層級 (例如 `Public` 語句中的) `Property` 。  
  
2. 宣告 `Get` 或 `Set` 指定更嚴格的存取層級 (例如) 的程式 `Friend` 。  
  
3. 請勿在其他屬性程式上指定存取層級。 它會假設在語句中宣告的存取層級 `Property` 。 您可以限制只能存取其中一個屬性程式。  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     在上述範例中，程式 `Get` 具有與 `Protected` 屬性本身相同的存取權，但程式 `Set` 具有 `Private` 存取權。 衍生自的類別 `employee` 可以讀取 `salary` 值，但只有 `employee` 類別可以設定它。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Visual Basic 中屬性和變數的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
