---
title: HOW TO：呼叫屬性程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 7b85239f80b4bfa87d1dbb1e3207e63d0cef7eeb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827207"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>HOW TO：呼叫屬性程序 (Visual Basic)
您可以在屬性中儲存值，或擷取其值呼叫屬性程序。 存取屬性相同的方式存取的變數。  
  
 屬性的`Set`程序儲存的值，並將其`Get`程序擷取的值。 不過，您無法明確呼叫這些程序的名稱。 就像您會儲存或擷取變數的值，您可以使用指派陳述式或運算式中的屬性。 Visual Basic 呼叫屬性程序。  
  
### <a name="to-call-a-propertys-get-procedure"></a>若要呼叫的屬性 Get 的程序  
  
1.  使用屬性名稱的運算式中您會使用變數名稱的方式相同。 您可以使用屬性，您可以使用變數或常數的任何位置。  
  
     -或-  
  
     使用下列相等的屬性名稱 (`=`) 登入在指派陳述式。  
  
     下列範例會讀取的值<xref:Microsoft.VisualBasic.DateAndTime.Now%2A>屬性，會隱含地呼叫其`Get`程序。  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2.  如果此屬性會接受引數，請遵循使用括號來括住的引數清單的屬性名稱。 如果不有任何引數，您可以選擇性地省略括號。  
  
3.  以括弧括住，並以逗號分隔的引數清單括住的引數。 請確定您提供的引數的屬性會定義的對應參數的順序相同。  
  
 如同變數運算式在參與的屬性的值或常數會或儲存在變數或指派陳述式左邊的屬性。  
  
### <a name="to-call-a-propertys-set-procedure"></a>若要呼叫屬性的設定程序  
  
1.  使用指派陳述式左邊的屬性名稱。  
  
     下列範例會設定的值<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>屬性，以隱含方式呼叫`Set`程序。  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2.  如果此屬性會接受引數，請遵循使用括號來括住的引數清單的屬性名稱。 如果不有任何引數，您可以選擇性地省略括號。  
  
3.  以括弧括住，並以逗號分隔的引數清單括住的引數。 請確定您提供的引數的屬性會定義的對應參數的順序相同。  
  
 指派陳述式右側所產生的值會儲存在屬性中。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [在 Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：宣告，並在 Visual Basic 中呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值放在屬性中](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
- [Get 陳述式](../../../../visual-basic/language-reference/statements/get-statement.md)
- [Set 陳述式](../../../../visual-basic/language-reference/statements/set-statement.md)
