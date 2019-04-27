---
title: HOW TO：取得值，屬性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863632"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>HOW TO：取得值，屬性 (Visual Basic)
您可以在運算式中包含屬性名稱，以擷取屬性的值。  
  
 屬性的`Get`程序會擷取值，但您未明確呼叫它的名稱。 就像您使用變數，您可以使用屬性。 Visual Basic 呼叫屬性程序。  
  
### <a name="to-retrieve-a-value-from-a-property"></a>若要擷取屬性的值  
  
1. 使用屬性名稱的運算式中您會使用變數名稱的方式相同。 您可以使用屬性，您可以使用變數或常數的任何位置。  
  
     -或-  
  
     使用下列相等的屬性名稱 (`=`) 登入在指派陳述式。  
  
     下列範例會讀取值的 Visual Basic`Now`屬性，會隱含地呼叫其`Get`程序。  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. 如果此屬性會接受引數，請遵循使用括號來括住的引數清單的屬性名稱。 如果不有任何引數，您可以選擇性地省略括號。  
  
3. 以括弧括住，並以逗號分隔的引數清單括住的引數。 請確定您提供的引數的屬性會定義的對應參數的順序相同。  
  
 如同變數運算式在參與的屬性的值或常數會或儲存在變數或指派陳述式左邊的屬性。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [在 Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：宣告，並在 Visual Basic 中呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值放在屬性中](./how-to-put-a-value-in-a-property.md)
