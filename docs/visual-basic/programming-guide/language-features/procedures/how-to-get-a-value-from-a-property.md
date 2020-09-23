---
title: 如何：取得屬性值
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 983e2fd22badf4296004404d885df0a07ab2dc74
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071556"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>如何：取得屬性值 (Visual Basic)

您可以藉由將屬性名稱包含在運算式中，來取得屬性的值。  
  
 屬性的程式 `Get` 會抓取值，但您不會依名稱明確地呼叫它。 您可以使用屬性，就像使用變數一樣。 Visual Basic 會對屬性的程式進行呼叫。  
  
### <a name="to-retrieve-a-value-from-a-property"></a>從屬性取出值  
  
1. 使用運算式中的屬性名稱，方式與使用變數名稱的方式相同。 您可以在任何可使用變數或常數的地方使用屬性。  
  
     -或-  
  
     在指派語句中) 登入之後，使用屬性名稱，並在等號 (`=` 。  
  
     下列範例會讀取 Visual Basic 屬性的值 `Now` ，並隱含地呼叫其程式 `Get` 。  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. 如果屬性採用引數，請在屬性名稱後面加上括弧，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。  
  
3. 將引數清單中的引數放在括弧內，並以逗號分隔。 請務必以屬性定義對應參數的相同順序提供引數。  
  
 屬性的值就像變數或常數一樣參與運算式，或是儲存在指派語句左邊的變數或屬性中。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Visual Basic 中屬性和變數的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
