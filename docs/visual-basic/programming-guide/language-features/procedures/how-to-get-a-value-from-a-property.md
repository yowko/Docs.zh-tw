---
title: "如何︰ 取得屬性 (Visual Basic) 的值 |Microsoft 文件"
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
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: 11
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
ms.openlocfilehash: 7487e4cde724c46a193639f2ad116d25e4ff834c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>如何：取得屬性值 (Visual Basic)
您可以在運算式中包含的屬性名稱擷取屬性的值。  
  
 屬性的`Get`程序會擷取值，但您沒有明確呼叫它的名稱。 就像您會使用變數，您可以使用屬性。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會呼叫屬性程序。  
  
### <a name="to-retrieve-a-value-from-a-property"></a>若要擷取屬性值  
  
1.  使用屬性名稱的運算式中使用變數名稱的方式相同。 您可以使用屬性您可以在任何地方使用的變數或常數。  
  
     -或-  
  
     使用下列等的屬性名稱 (`=`) 登入在指派陳述式。  
  
     下列範例會讀取的值[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]`Now`屬性，以隱含方式呼叫其`Get`程序。  
  
     [!code-vb[VbVbalrDateProperties #&4;](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  如果屬性有引數，請遵循有括號括住的引數清單的屬性名稱。 如果不有任何引數，您可以省略括號。  
  
3.  將引數放在括號，以逗號分隔的引數清單。 請確定您提供的引數的屬性會定義對應參數的順序相同。  
  
 屬性的值加入運算式如同變數或常數一般使用，或會儲存在變數或屬性指派陳述式的左邊。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [Property 程序](./property-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)   
 [如何︰ 建立屬性](./how-to-create-a-property.md)   
 [如何︰ 宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [如何︰ 呼叫屬性程序](./how-to-call-a-property-procedure.md)   
 [如何︰ 宣告及呼叫預設屬性，在 Visual Basic 中](./how-to-declare-and-call-a-default-property.md)   
 [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
