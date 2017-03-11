---
title: "Determining Object Type (Visual Basic) | Microsoft Docs"
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
  - "classes [Visual Basic], discovering which an object belongs to"
  - "types [Visual Basic], determining Visual Basic object types"
  - "object variables, testing values"
  - "TypeOf...Is expression, object type at run time"
  - "TypeName function"
  - "objects [Visual Basic], type determining"
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Determining Object Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

泛型物件變數 \(也就是您宣告為 `Object` 的變數\) 可存放任何類別的物件。  當使用 `Object` 型別的變數時，您可能需要根據物件的類別而採取不同的動作。例如，一些物件可能不支援特定的屬性或方法。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 提供兩種方式判斷儲存在物件變數中的是何種型別的物件：`TypeName` 函式和 `TypeOf...Is` 運算子。  
  
## TypeName 和 TypeOf…Is  
 `TypeName` 函式傳回的是字串，在您需要儲存或顯示物件類別名稱時，這是最佳選擇，如下列程式碼片段所示：  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#92)]  
  
 `TypeOf...Is` 運算子是測試物件型別的最佳選擇，因為它比使用 `TypeName` 所做的對等字串比較快很多。  下列程式碼片段將 `TypeOf...Is` 套用在 `If...Then...Else` 陳述式 \(Statement\) 中。  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#93)]  
  
 這裡必須特別注意。  `TypeOf...Is` 運算子會傳回 `True`，前提為物件是特定的型別，或是衍生自特定的型別。  您在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中所做的事情幾乎都會牽涉到物件，包括一些通常不視為物件的項目，例如字串及整數。  這些物件洐生自且繼承自 <xref:System.Object>。  當傳遞 `Integer` 並以 `Object` 進行評估時，`TypeOf...Is` 運算子會傳回 `True`。  下列範例會回報參數 `InParam` 同時為 `Object` 和 `Integer`︰  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#94)]  
  
 下列範例同時使用 `TypeOf...Is` 和 `TypeName`，來決定以 `Ctrl` 引數傳遞的物件型別。  `TestObject` 程序以三種不同的控制項呼叫 `ShowType`。  
  
#### 若要執行範例  
  
1.  建立新的 Windows 應用程式專案，並在表單中加入 <xref:System.Windows.Forms.Button> 控制項、<xref:System.Windows.Forms.CheckBox> 控制項及 <xref:System.Windows.Forms.RadioButton> 控制項。  
  
2.  從表單上的按鈕呼叫 `TestObject` 程序。  
  
3.  將下列程式碼加入表單。  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#95)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>   
 [Calling a Property or Method Using a String Name](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md)