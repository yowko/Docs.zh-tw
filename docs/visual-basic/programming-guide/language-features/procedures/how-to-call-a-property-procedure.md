---
title: "如何︰ 呼叫屬性程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], property procedures
- procedure calls, property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7dd3d53f602886f65c951de34b915b2672b1a817
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>如何：呼叫屬性程序 (Visual Basic)
您可以將值儲存在屬性中，或擷取其值呼叫屬性程序。 存取屬性相同的方式存取的變數。  
  
 屬性的`Set`程序儲存值，並將其`Get`程序擷取的值。 不過，您沒有明確呼叫這些程序的名稱。 就像您儲存或擷取變數的值，您可以使用在指派陳述式或運算式中的屬性。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會呼叫屬性程序。  
  
### <a name="to-call-a-propertys-get-procedure"></a>呼叫屬性的 Get 的程序  
  
1.  使用屬性名稱的運算式中使用變數名稱的方式相同。 您可以使用屬性您可以在任何地方使用的變數或常數。  
  
     -或-  
  
     使用下列等的屬性名稱 (`=`) 登入在指派陳述式。  
  
     下列範例會讀取的值<xref:Microsoft.VisualBasic.DateAndTime.Now%2A>屬性，以隱含方式呼叫其`Get`程序。</xref:Microsoft.VisualBasic.DateAndTime.Now%2A>  
  
     [!code-vb[VbVbalrDateProperties #&4;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  如果屬性有引數，請遵循有括號括住的引數清單的屬性名稱。 如果不有任何引數，您可以省略括號。  
  
3.  將引數放在括號，以逗號分隔的引數清單。 請確定您提供的引數的屬性會定義對應參數的順序相同。  
  
 屬性的值加入運算式如同變數或常數一般使用，或會儲存在變數或屬性指派陳述式的左邊。  
  
### <a name="to-call-a-propertys-set-procedure"></a>若要呼叫屬性的設定程序  
  
1.  指派陳述式的左邊使用屬性名稱。  
  
     下列範例會設定的值<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>屬性，以隱含方式呼叫`Set`程序。</xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
  
     [!code-vb[VbVbcnProcedures #&11;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  如果屬性有引數，請遵循有括號括住的引數清單的屬性名稱。 如果不有任何引數，您可以省略括號。  
  
3.  將引數放在括號，以逗號分隔的引數清單。 請確定您提供的引數的屬性會定義對應參數的順序相同。  
  
 指派陳述式右邊所產生的值儲存在屬性中。  
  
## <a name="see-also"></a>另請參閱  
 [Property 程序](./property-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)   
 [如何︰ 建立屬性](./how-to-create-a-property.md)   
 [如何︰ 宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [如何︰ 宣告及呼叫預設屬性，在 Visual Basic 中](./how-to-declare-and-call-a-default-property.md)   
 [如何︰ 將值置入屬性](./how-to-put-a-value-in-a-property.md)   
 [如何︰ 取得屬性值](./how-to-get-a-value-from-a-property.md)   
 [Get 陳述式](../../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set 陳述式](../../../../visual-basic/language-reference/statements/set-statement.md)
