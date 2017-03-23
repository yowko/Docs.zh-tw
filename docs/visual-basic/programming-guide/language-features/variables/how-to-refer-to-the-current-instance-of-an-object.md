---
title: "How to: Refer to the Current Instance of an Object (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], object"
  - "objects [Visual Basic], referring to current instance"
  - "instances, referring to current"
  - "current instance"
  - "object variables"
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Refer to the Current Instance of an Object (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

物件的「*目前執行個體*」\(Current Instance\) 是目前用來執行程式碼的執行個體。  
  
 使用 `Me` 關鍵字即可參考目前執行個體。  
  
### 參考目前執行個體  
  
-   在您通常會使用物件變數名稱的地方，使用 `Me` 關鍵字。  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     雖然 `Me` 的行為方式類似於物件變數，但是您無法宣告它或將任何項目指派給它。  `Me` 一定是參考目前執行個體。  
  
## 請參閱  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)