---
title: 如何：呼叫屬性程序
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 0b35751136937d4cee5b3ca9669b43d3fbdf71a1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071947"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>如何：呼叫屬性程序 (Visual Basic)

您可以藉由將值儲存在屬性中或抓取其值，來呼叫屬性程式。 您可以使用存取變數的相同方式來存取屬性。  
  
 屬性的程式會 `Set` 儲存值，而且其程式會抓取 `Get` 值。 不過，您不會依名稱明確地呼叫這些程式。 您可以使用指派語句或運算式中的屬性，就如同您儲存或取出變數值一樣。 Visual Basic 會對屬性的程式進行呼叫。  
  
### <a name="to-call-a-propertys-get-procedure"></a>若要呼叫屬性的 Get 程式  
  
1. 使用運算式中的屬性名稱，方式與使用變數名稱的方式相同。 您可以在任何可使用變數或常數的地方使用屬性。  
  
     -或-  
  
     在指派語句中) 登入之後，使用屬性名稱，並在等號 (`=` 。  
  
     下列範例會讀取屬性的值 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> ，並隱含地呼叫其程式 `Get` 。  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. 如果屬性採用引數，請在屬性名稱後面加上括弧，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。  
  
3. 將引數清單中的引數放在括弧內，並以逗號分隔。 請務必以屬性定義對應參數的相同順序提供引數。  
  
 屬性的值就像變數或常數一樣參與運算式，或是儲存在指派語句左邊的變數或屬性中。  
  
### <a name="to-call-a-propertys-set-procedure"></a>若要呼叫屬性的 Set 程式  
  
1. 使用指派語句左邊的屬性名稱。  
  
     下列範例會設定屬性的值 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> ，並隱含地呼叫程式 `Set` 。  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. 如果屬性採用引數，請在屬性名稱後面加上括弧，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。  
  
3. 將引數清單中的引數放在括弧內，並以逗號分隔。 請務必以屬性定義對應參數的相同順序提供引數。  
  
 在指派語句的右邊產生的值會儲存在屬性中。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Visual Basic 中屬性和變數的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
- [Get 陳述式](../../../language-reference/statements/get-statement.md)
- [Set 語句](../../../language-reference/statements/set-statement.md)
