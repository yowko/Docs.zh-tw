---
title: "How to: Make an Object Variable Not Refer to Any Instance (Visual Basic) | Microsoft Docs"
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
  - "Nothing keyword, variable assignment"
  - "object variables, null reference"
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

您可以將物件變數設定為 [Nothing](../../../../visual-basic/language-reference/nothing.md)，以解除物件變數與任何物件執行個體 \(Instance\) 之間的關聯。  
  
### 解除物件變數與任何物件執行個體之間的關聯  
  
-   在指派陳述式 \(Assignment Statement\) 中將變數設定為 `Nothing`。  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## 穩固程式設計  
 如果您的程式碼嘗試存取某個物件變數的成員，而該物件變數已設定為 `Nothing`，就會發生 <xref:System.NullReferenceException>。  如果您需要經常將物件變數設定為 `Nothing`，或有可能不會初始化該變數，則將成員存取放在 `Try...Catch...Finally` 區塊之中是很好的作法。  
  
## .NET Framework 安全性  
 如果您需要爲含有機密或敏感資料的物件使用物件變數，則可以在不需要主動處理其中任何一個物件時，將變數設定為 `Nothing`。  這樣可以減少惡意程式碼存取資料的機會。  
  
## 請參閱  
 <xref:System.NullReferenceException>   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Nothing](../../../../visual-basic/language-reference/nothing.md)   
 [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [疑難排解例外狀況：System.NullReferenceException](../Topic/Troubleshooting%20Exceptions:%20System.NullReferenceException.md)