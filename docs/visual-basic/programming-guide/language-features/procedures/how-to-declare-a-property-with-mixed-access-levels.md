---
title: HOW TO：宣告混合的存取層級 (Visual Basic) 的屬性
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
ms.openlocfilehash: d2b1a80863fe29901554b4912acbbfbdfdab4122
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972578"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>HOW TO：宣告混合的存取層級 (Visual Basic) 的屬性
如果您想`Get`並`Set`有不同的存取層級屬性的程序，您可以使用中的更寬鬆的層級`Property`陳述式並在更嚴格的層級`Get`或`Set`陳述式。 當您想要能夠取得屬性的值，程式碼的特定組件和其他部分的程式碼能夠將值變更時，您可以使用在屬性上的混合的存取層級。  
  
 如需有關存取層級的詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>若要宣告混合的存取層級的屬性  
  
1.  宣告屬性，以一般方式，並指定較不嚴格的存取層級 (例如`Public`) 中`Property`陳述式。  
  
2.  宣告其中`Get`或`Set`程序並指定更嚴格的存取層級 (例如`Friend`)。  
  
3.  未指定存取層級上的其他屬性程序。 它會假設中宣告的存取層級`Property`陳述式。 您可以限制只有其中一個屬性程序的存取。  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     在上述範例中，`Get`程序中的相同`Protected`屬性本身的存取權時`Set`程序中的`Private`存取。 類別衍生自`employee`可以讀取`salary`值，但僅限`employee`類別也可以設定它。  
  
## <a name="see-also"></a>另請參閱
- [程序](./index.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [在 Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：宣告，並在 Visual Basic 中呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值放在屬性中](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
