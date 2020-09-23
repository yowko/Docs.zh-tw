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
ms.openlocfilehash: 7d85066d4678ee2a53b8339bee2db20374482579
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071400"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>如何：將值置入屬性 (Visual Basic)

您可以將屬性名稱放在指派語句的左邊，以將值儲存在屬性中。  
  
 屬性的程式會 `Set` 儲存一個值，但您不會依名稱明確地呼叫它。 您可以使用屬性，就像使用變數一樣。 Visual Basic 會對屬性的程式進行呼叫。  
  
### <a name="to-store-a-value-in-a-property"></a>若要在屬性中儲存值  
  
1. 使用指派語句左邊的屬性名稱。  
  
     下列範例會將 Visual Basic 屬性的值設定 `TimeOfDay` 為中午，並隱含地呼叫其程式 `Set` 。  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. 如果屬性採用引數，請在屬性名稱後面加上括弧，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。  
  
3. 將引數清單中的引數放在括弧內，並以逗號分隔。 請務必以屬性定義對應參數的相同順序提供引數。  
  
4. 在指派語句的右邊產生的值會儲存在屬性中。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Visual Basic 中屬性和變數的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
