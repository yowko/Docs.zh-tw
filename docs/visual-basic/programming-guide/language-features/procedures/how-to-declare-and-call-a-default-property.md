---
title: "How to: Declare and Call a Default Property in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "defaults, properties"
  - "properties [Visual Basic], default"
  - "procedures, defining"
  - "default properties, in Visual Basic"
  - "Visual Basic code, procedures"
  - "Visual Basic code, properties"
  - "default properties"
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# How to: Declare and Call a Default Property in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*預設屬性*」\(Default Property\) 是程式碼可存取但不需指定的類別或結構屬性。  在呼叫程式碼命名類別或結構 \(而非屬性\)，且內容允許存取屬性時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會解析該類別或結構預設屬性 \(如果有的話\) 的存取權。  
  
 類別或結構最多可有一個預設屬性。  不過，您可多載預設屬性，且擁有一個以上的屬性版本。  
  
 如需詳細資訊，請參閱[Default](../../../../visual-basic/language-reference/modifiers/default.md)。  
  
### 若要宣告預設屬性  
  
1.  以一般方式宣告屬性，  不要指定 `Shared` 或 `Private` 關鍵字。  
  
2.  在屬性宣告中包含 `Default` 關鍵字。  
  
3.  至少為屬性指定一個參數，  無法定義未包含任何引數的預設屬性。  
  
     [!code-vb[VbVbcnProcedures#17](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-declare-and-call-_1.vb)]  
  
### 若要呼叫預設屬性  
  
1.  宣告包含類別或結構型別 \(Structure Type\) 的變數。  
  
     [!code-vb[VbVbcnProcedures#16](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-declare-and-call-_2.vb)]  
  
2.  在您通常會包含屬性名稱的運算式中，單獨使用變數名稱。  
  
     [!code-vb[VbVbcnProcedures#21](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-declare-and-call-_3.vb)]  
  
3.  變數名稱後面緊跟著以括號括住的引數清單，  預設屬性至少必須取用一個引數。  
  
     [!code-vb[VbVbcnProcedures#20](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-declare-and-call-_4.vb)]  
  
4.  若要擷取預設屬性值，請在運算式中使用變數名稱 \(含引數清單\)，或在指派陳述式 \(Assignment Statement\) 的等號 \(`=`\) 後面使用變數名稱。  
  
     [!code-vb[VbVbcnProcedures#15](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-declare-and-call-_5.vb)]  
  
5.  若要設定預設屬性值，請在指派陳述式的左邊使用變數名稱 \(含引數清單\)。  
  
     [!code-vb[VbVbcnProcedures#14](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-declare-and-call-_6.vb)]  
  
6.  您永遠可同時指定預設屬性名稱與變數名稱，就像存取任何其他屬性一樣。  
  
     [!code-vb[VbVbcnProcedures#19](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-declare-and-call-_7.vb)]  
  
## 範例  
 以下範例會在類別上宣告預設屬性：  
  
 [!code-vb[VbVbcnProcedures#12](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-declare-and-call-_8.vb)]  
  
## 範例  
 下列範例會示範如何在類別 `class1` 上呼叫預設屬性 `myProperty`。  這三個指派陳述式會將值儲存在 `myProperty` 中，而 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 呼叫會讀取這些值。  
  
 [!code-vb[VbVbcnProcedures#13](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-declare-and-call-_9.vb)]  
  
 預設屬性的最常見用法是各種集合類別 \(Collection Class\) 上的 <xref:Microsoft.VisualBasic.Collection.Item%2A> 屬性。  
  
## 穩固程式設計  
 預設屬性可小幅度地減少原始程式碼字元，但會讓其他人更不容易看懂您的程式碼。  如果呼叫程式碼不熟悉您的類別或結構，則在它產生該類別或結構名稱的參考時，會無法確定該參考存取的是類別或結構本身或預設屬性。  這會造成編譯器錯誤，或微妙的執行階段邏輯錯誤。  
  
 您永遠可以使用 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)，將編譯器型別檢查 \(Type Checking\) 設為 `On`，以減少預設屬性錯誤的機會。  
  
 如果您預計在程式碼中使用預先定義的類別或結構，則必須判斷它是否具有預設屬性，如果有則其名稱為何。  
  
 因為這些缺點，所以您應考慮不要定義預設屬性。  為了增加程式碼可讀性，也應考慮一律明確參考所有屬性 \(甚至是預設屬性\)。  
  
## 請參閱  
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Default](../../../../visual-basic/language-reference/modifiers/default.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)