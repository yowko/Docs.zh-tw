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
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349689"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>如何：宣告混合存取層級的屬性 (Visual Basic)
如果您想要讓屬性上的 `Get` 和 `Set` 程式擁有不同的存取層級，您可以在 `Property` 語句中使用更寬鬆的等級，並在 `Get` 或 `Set` 語句中使用更嚴格的層級。 當您希望程式碼的某些部分能夠取得屬性的值，而且程式碼的某些其他部分能夠變更值時，您可以在屬性上使用混合存取層級。  
  
 如需存取層級的詳細資訊，請參閱[Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>若要宣告具有混合存取層級的屬性  
  
1. 以一般方式宣告屬性，並在 `Property` 語句中指定較不嚴格的存取層級（例如 `Public`）。  
  
2. 請宣告 `Get` 或 `Set` 程式，以指定更嚴格的存取層級（例如 `Friend`）。  
  
3. 請不要在另一個屬性程式上指定存取層級。 它會假設在 `Property` 語句中宣告的存取層級。 您可以限制只有其中一個屬性程式的存取權。  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     在上述範例中，`Get` 程式與屬性本身具有相同的 `Protected` 存取權，而 `Set` 程式則具有 `Private` 存取權。 衍生自 `employee` 的類別可以讀取 `salary` 值，但只有 `employee` 類別可以設定它。  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic 中的屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
