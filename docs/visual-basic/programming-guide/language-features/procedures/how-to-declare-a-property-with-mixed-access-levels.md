---
title: "如何：宣告混合存取層級的屬性 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90fe20303f6f2ed692e54e44ee8cc65897531543
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>如何：宣告混合存取層級的屬性 (Visual Basic)
如果您想`Get`和`Set`屬性有不同的存取層級的程序，您可以使用中的更寬鬆的層級`Property`陳述式和更嚴格的層級，在`Get`或`Set`陳述式。 當您想要能夠取得屬性值的程式碼某些部分和其他部分的程式碼，將值變更時，您可以使用屬性上的混合的存取層級。  
  
 如需有關存取層級的詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>若要宣告混合的存取層級的屬性  
  
1.  宣告屬性以一般方式，並指定較不嚴格的存取層級 (例如`Public`) 中`Property`陳述式。  
  
2.  宣告其中`Get`或`Set`程序並指定更嚴格的存取層級 (例如`Friend`)。  
  
3.  未指定存取層級上的其他屬性程序。 它會假設中宣告的存取層級`Property`陳述式。 您可以限制存取其中一個屬性程序。  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     在上述範例中，`Get`程序中的相同`Protected`存取與屬性本身，而`Set`程序中的`Private`存取。 類別衍生自`employee`可以讀取`salary`值，但只`employee`類別可以將其設定。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [屬性程序](./property-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [在 Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)  
 [如何：建立屬性](./how-to-create-a-property.md)  
 [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)  
 [如何： 宣告及呼叫在 Visual Basic 中的預設屬性](./how-to-declare-and-call-a-default-property.md)  
 [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)  
 [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
