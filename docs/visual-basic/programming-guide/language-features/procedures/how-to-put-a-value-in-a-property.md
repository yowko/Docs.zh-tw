---
title: 如何：將值置入屬性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 29e68ca2b9436921c81346eb1def2417157aae9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650367"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>如何：將值置入屬性 (Visual Basic)
您儲存值，您可以在屬性中的屬性名稱放在指派陳述式的左半部。  
  
 屬性的`Set`程序可儲存值，但您沒有明確呼叫它的名稱。 就像您會使用變數，您可以使用屬性。 Visual Basic 會將屬性的程序呼叫。  
  
### <a name="to-store-a-value-in-a-property"></a>若要在屬性中儲存的值  
  
1.  指派陳述式的左邊使用屬性名稱。  
  
     下列範例會設定的值的 Visual Basic`TimeOfDay`屬性中午，隱含地呼叫其`Set`程序。  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  如果屬性引數，請遵循以括號來括住的引數清單的屬性名稱。 如果有任何引數，您可以選擇性地省略括號。  
  
3.  將引數放在括號，並以逗號分隔的引數清單。 請確定您提供的引數的屬性會定義的對應參數的順序相同。  
  
4.  產生的指派陳述式右邊的值會儲存在屬性中。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [屬性程序](./property-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [在 Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)  
 [如何：建立屬性](./how-to-create-a-property.md)  
 [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)  
 [如何： 宣告及呼叫在 Visual Basic 中的預設屬性](./how-to-declare-and-call-a-default-property.md)  
 [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
