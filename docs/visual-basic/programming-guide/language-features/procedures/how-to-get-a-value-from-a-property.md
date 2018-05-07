---
title: 如何：取得屬性值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 9f97669e8d18e7fc633cb0e691d973a611a8cea0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>如何：取得屬性值 (Visual Basic)
您可以在運算式中包含的屬性名稱擷取屬性的值。  
  
 屬性的`Get`程序會擷取值，但您沒有明確呼叫它的名稱。 就像您會使用變數，您可以使用屬性。 Visual Basic 會將屬性的程序呼叫。  
  
### <a name="to-retrieve-a-value-from-a-property"></a>若要擷取屬性的值  
  
1.  使用屬性名稱的運算式中使用變數名稱的方式相同。 您可以使用屬性您可以在任何地方使用的變數或常數。  
  
     -或-  
  
     使用下列相等的屬性名稱 (`=`) 登入指派陳述式。  
  
     下列範例會讀取值的 Visual Basic`Now`屬性，以隱含方式呼叫其`Get`程序。  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  如果屬性引數，請遵循以括號來括住的引數清單的屬性名稱。 如果有任何引數，您可以選擇性地省略括號。  
  
3.  將引數放在括號，並以逗號分隔的引數清單。 請確定您提供的引數的屬性會定義的對應參數的順序相同。  
  
 屬性的值加入運算式如同變數或常數會或儲存在變數或指派陳述式左邊的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [屬性程序](./property-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [在 Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)  
 [如何：建立屬性](./how-to-create-a-property.md)  
 [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)  
 [如何： 宣告及呼叫在 Visual Basic 中的預設屬性](./how-to-declare-and-call-a-default-property.md)  
 [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
