---
title: HOW TO：將值放在屬性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: e6aee5ea36c0315d5b01ae2734d17c9e7dab8e93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863892"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>HOW TO：將值放在屬性 (Visual Basic)
您將屬性名稱放在指派陳述式左邊值儲存在屬性中。  
  
 屬性的`Set`程序會將儲存的值，但您未明確呼叫它的名稱。 就像您使用變數，您可以使用屬性。 Visual Basic 呼叫屬性程序。  
  
### <a name="to-store-a-value-in-a-property"></a>若要儲存在屬性中的值  
  
1. 使用指派陳述式左邊的屬性名稱。  
  
     下列範例會設定值的 Visual Basic`TimeOfDay`屬性到中午，隱含地呼叫其`Set`程序。  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. 如果此屬性會接受引數，請遵循使用括號來括住的引數清單的屬性名稱。 如果不有任何引數，您可以選擇性地省略括號。  
  
3. 以括弧括住，並以逗號分隔的引數清單括住的引數。 請確定您提供的引數的屬性會定義的對應參數的順序相同。  
  
4. 指派陳述式右側所產生的值會儲存在屬性中。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [在 Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：宣告，並在 Visual Basic 中呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
