---
title: "How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic) | Microsoft Docs"
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
  - "variables [Visual Basic], accessing"
  - "variables [Visual Basic], object"
  - "With statement"
  - "With block"
  - "object variables, accessing"
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

如果經常存取的物件需要數個方法和屬性的限定性條件路徑，則只要不重複限定性條件路徑，即可加快程式碼。  
  
 有兩種方法可避免重複限定性條件路徑。  可將物件指定給變數，或將它用於 `With`...`End With` 區塊中。  
  
### 若要將高度限定物件指定給變數，以加速高度限定物件的存取  
  
1.  宣告經常存取之物件型別的變數。  在宣告的初始設定部分中指定限定性條件路徑。  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  使用變數來存取物件的成員。  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### 若要使用 With...End With 區塊來加速高度限定物件的存取  
  
1.  在 `With` 陳述式 \(Statement\) 中放入限定性條件路徑。  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  存取 `With` 區塊 \(`End With` 陳述式的前面\) 內部的物件成員。  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## 請參閱  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)