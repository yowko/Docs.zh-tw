---
title: "如何︰ 宣告及呼叫預設屬性，在 Visual Basic |Microsoft 文件"
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
- defaults, properties
- properties [Visual Basic], default
- procedures, defining
- default properties, in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
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
ms.openlocfilehash: ce98e7fe72a395f6c4cde481feaa60be28c6fcc3
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>如何：在 Visual Basic 中宣告及呼叫預設屬性
A*預設屬性*是類別或結構的屬性，可以存取您的程式碼，而不指定它。 當呼叫程式碼的類別或結構，但不是屬性名稱和內容都可存取屬性，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]解析成該類別或結構的預設屬性的存取權，如果有的話。  
  
 類別或結構最多可以有一個預設屬性。 不過，您可以多載的預設屬性，並讓它的多個版本。  
  
 如需詳細資訊，請參閱[預設](../../../../visual-basic/language-reference/modifiers/default.md)。  
  
### <a name="to-declare-a-default-property"></a>若要宣告預設屬性  
  
1.  以一般方式宣告屬性。 未指定`Shared`或`Private`關鍵字。  
  
2.  包含`Default`屬性宣告中的關鍵字。  
  
3.  指定至少一個參數的屬性。 您無法定義預設屬性不需要使用至少一個引數。  
  
     [!code-vb[VbVbcnProcedures #&17;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a>若要呼叫預設屬性  
  
1.  宣告為包含的類別或結構類型的變數。  
  
     [!code-vb[VbVbcnProcedures #&16;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  使用變數名稱只在運算式中，您通常會包含屬性名稱。  
  
     [!code-vb[VbVbcnProcedures #&21;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  在變數名稱後面的括號括住的引數清單。 預設屬性必須接受至少一個引數。  
  
     [!code-vb[VbVbcnProcedures #&20;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  若要擷取預設屬性值，使用變數名稱，在運算式中，或等號之後的引數清單 (`=`) 登入在指派陳述式。  
  
     [!code-vb[VbVbcnProcedures #&15;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  若要設定預設屬性值，使用的引數清單，在指派陳述式左邊的變數名稱。  
  
     [!code-vb[VbVbcnProcedures #&14;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  您永遠可以指定預設屬性名稱與變數名稱，就像您一樣存取任何其他屬性。  
  
     [!code-vb[VbVbcnProcedures #&19;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a>範例  
 下列範例會宣告預設屬性類別上。  
  
 [!code-vb[VbVbcnProcedures #&12;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範如何呼叫預設屬性`myProperty`類別上`class1`。 三個指派陳述式存放區中的值`myProperty`，而<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>呼叫讀取值。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
 [!code-vb[VbVbcnProcedures #&13;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 預設屬性的最常見的用法是<xref:Microsoft.VisualBasic.Collection.Item%2A>上各種不同的集合類別的屬性。</xref:Microsoft.VisualBasic.Collection.Item%2A>  
  
## <a name="robust-programming"></a>穩固程式設計  
 預設屬性可能會導致小減少原始程式碼字元，但會讓您的程式碼更難閱讀。 如果類別或結構名稱的參考時呼叫的程式碼不熟悉您的類別或結構，它無法確定該參考存取類別或結構本身或預設屬性。 這可能會導致編譯器錯誤或微妙的執行階段邏輯錯誤。  
  
 您可以稍微降低預設屬性錯誤的機會都使用[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定編譯器型別檢查`On`。  
  
 如果您打算使用預先定義的類別或結構中程式碼，您必須決定是否具有預設屬性，而且如果是，其名稱為何。  
  
 由於這些缺點，您應該考慮不要定義預設屬性。 程式碼的可讀性，您應該也考慮一律明確參考所有屬性，甚至是預設屬性。  
  
## <a name="see-also"></a>另請參閱  
 [Property 程序](./property-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [預設值](../../../../visual-basic/language-reference/modifiers/default.md)   
 [Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)   
 [如何︰ 建立屬性](./how-to-create-a-property.md)   
 [如何︰ 宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [如何︰ 呼叫屬性程序](./how-to-call-a-property-procedure.md)   
 [如何︰ 將值置入屬性](./how-to-put-a-value-in-a-property.md)   
 [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
