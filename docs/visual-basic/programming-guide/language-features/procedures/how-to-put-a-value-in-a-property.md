---
title: 如何：將值置入屬性
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: ad0d0e81f94dd3dead50f21c3bd6ff580c004dd6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346047"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>如何：將值置入屬性 (Visual Basic)
您可以藉由將屬性名稱放在指派語句的左邊，將值儲存在屬性中。  
  
 屬性的 `Set` 程式會儲存一個值，但您不會依名稱明確地呼叫它。 您可以使用屬性，就像使用變數一樣。 Visual Basic 會呼叫屬性的程式。  
  
### <a name="to-store-a-value-in-a-property"></a>若要在屬性中儲存值  
  
1. 使用指派語句左側的屬性名稱。  
  
     下列範例會將 Visual Basic `TimeOfDay` 屬性的值設定為 [中午]，並隱含地呼叫其 `Set` 程式。  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. 如果屬性接受引數，請在屬性名稱後面加上括弧，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。  
  
3. 將引數放在括弧內的引數清單中，並以逗號分隔。 請務必以屬性定義對應參數的相同順序來提供引數。  
  
4. 在指派語句的右邊產生的值會儲存在屬性中。  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic 中的屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
