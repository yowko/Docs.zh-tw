---
title: "如何︰ 將值置入屬性 (Visual Basic) |Microsoft 文件"
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
- property values
- Visual Basic code, procedures
- values, properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: e3b2336589b525756a92cb3e26ab6c1950118b01
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>如何：將值置入屬性 (Visual Basic)
您放在指派陳述式左邊的屬性名稱的值儲存在屬性中。  
  
 屬性的`Set`程序儲存值，但您沒有明確呼叫它的名稱。 就像您會使用變數，您可以使用屬性。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會呼叫屬性程序。  
  
### <a name="to-store-a-value-in-a-property"></a>若要儲存的屬性值  
  
1.  指派陳述式的左邊使用屬性名稱。  
  
     下列範例會設定的值[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]`TimeOfDay`屬性到中午，隱含地呼叫其`Set`程序。  
  
     [!code-vb[VbVbcnProcedures #&11;](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  如果屬性有引數，請遵循有括號括住的引數清單的屬性名稱。 如果不有任何引數，您可以省略括號。  
  
3.  將引數放在括號，以逗號分隔的引數清單。 請確定您提供的引數的屬性會定義對應參數的順序相同。  
  
4.  指派陳述式右邊所產生的值儲存在屬性中。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>   
 [Property 程序](./property-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)   
 [如何︰ 建立屬性](./how-to-create-a-property.md)   
 [如何︰ 宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [如何︰ 呼叫屬性程序](./how-to-call-a-property-procedure.md)   
 [如何︰ 宣告及呼叫預設屬性，在 Visual Basic 中](./how-to-declare-and-call-a-default-property.md)   
 [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
