---
title: "Object Variables in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object variables, about object variables"
  - "variables [Visual Basic], object"
  - "objects [Visual Basic], accessing"
  - "object variables"
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Object Variables in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

除了直接儲存值以外，變數可參考物件。  您將物件指派給變數的原因與將任何值指派給變數的原因相同：  
  
-   變數的名稱通常比存取物件本身所需的方法和屬性 \(Property\) 之完整路徑短。  
  
-   使用參考物件的變數比透過必要的方法或屬性重複地存取物件本身更有效率。  
  
-   您可以在程式碼執行時將變數變改為參考其他物件。  
  
## 縮短程式碼  
 您可以用物件變數縮短必須輸入的程式碼。  下列範例使用方法和屬性的完整路徑，以存取 <xref:System.Windows.Forms.Control> 物件。  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 如果您用物件變數來控制，就可以縮短這個程式碼和加快執行速度。  您應該用您嘗試要指派給它的特定類別 \(本例中的 `Control`\) 來宣告物件變數。  一旦您將物件指派給變數，您可以完全將它視為它所參考的物件。  您可以設定或擷取物件的屬性，或使用任何物件的方法。  下列範例使用物件變數，簡化前述範例中的程式碼。  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## 請參閱  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [How to: Speed Up Access to an Object with a Long Qualification Path](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)