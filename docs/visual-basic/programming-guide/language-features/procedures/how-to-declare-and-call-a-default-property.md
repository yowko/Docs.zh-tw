---
title: HOW TO：宣告，並在 Visual Basic 中呼叫預設屬性
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: ca282acbe6831f2189d83faa2f83d32d420d9b53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640962"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>HOW TO：宣告，並在 Visual Basic 中呼叫預設屬性
A*屬性預設*是類別或結構的屬性，不需要指定它可以存取您的程式碼。 在呼叫程式碼命名類別或結構，但不是屬性，與內容允許存取屬性時，Visual Basic 會解析成該類別或結構的預設屬性存取若有的話。  
  
 類別或結構最多可以有一個預設屬性。 不過，您可以多載預設屬性，並讓它的多個版本。  
  
 如需詳細資訊，請參閱 <<c0> [ 預設](../../../../visual-basic/language-reference/modifiers/default.md)。  
  
### <a name="to-declare-a-default-property"></a>若要宣告預設屬性  
  
1.  以一般方式宣告的屬性。 未指定`Shared`或`Private`關鍵字。  
  
2.  包含`Default`屬性宣告中的關鍵字。  
  
3.  指定至少一個參數的屬性。 您無法定義預設屬性未採用至少一個引數。  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a>若要呼叫預設屬性  
  
1.  宣告包含的類別或結構類型的變數。  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  使用單獨在運算式中的變數名稱，您通常會包含屬性名稱。  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  變數名稱後面加括號括住的引數清單。 預設屬性必須採用至少一個引數。  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  若要擷取預設屬性值，請使用變數的名稱，引數清單中，在運算式中，或等於下列 (`=`) 登入在指派陳述式。  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  若要設定預設屬性值，使用指派陳述式左邊的引數清單中的變數名稱。  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  就像您一樣存取任何其他屬性，您一律可以指定變數的名稱，連同預設屬性名稱。  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a>範例  
 下列範例會宣告預設屬性類別上。  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範如何呼叫預設屬性`myProperty`類別上`class1`。 三個的指派陳述式存放區中的值`myProperty`，而<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>呼叫讀取值。  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 預設屬性的最常見的用法是<xref:Microsoft.VisualBasic.Collection.Item%2A>上各種不同的集合類別的屬性。  
  
## <a name="robust-programming"></a>穩固程式設計  
 預設屬性可能會導致小型減少原始程式碼字元，但它們可以讓您的程式碼更難讀取。 如果類別或結構名稱的參考時呼叫的程式碼不熟悉如何使用您自己的類別或結構，它無法確定該參考是存取類別或結構本身或預設屬性。 這可能會導致編譯器錯誤或難以察覺的執行階段邏輯錯誤。  
  
 您可以一律使用，以稍微降低預設屬性錯誤的機會[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定檢查的編譯器型別`On`。  
  
 如果您打算使用預先定義的類別或結構中您的程式碼中，您必須判斷是否有預設屬性，而如果是的話，它的名稱為何。  
  
 由於這些缺點，您應該考慮不要定義預設屬性。 程式碼的可讀性，您應該也要考慮一律明確地參考的所有屬性，甚至是預設屬性。  
  
## <a name="see-also"></a>另請參閱
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Default](../../../../visual-basic/language-reference/modifiers/default.md)
- [在 Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：將值放在屬性中](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
