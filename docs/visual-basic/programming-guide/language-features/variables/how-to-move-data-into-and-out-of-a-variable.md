---
title: "How to: Move Data Into and Out of a Variable (Visual Basic) | Microsoft Docs"
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
  - "variables [Visual Basic], retrieving values"
  - "variables [Visual Basic], storing data"
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Move Data Into and Out of a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

藉由在指派陳述式 \(Assignment Statement\) 的左邊放置變數名稱，即可將值存入變數。  
  
## 在變數中放置資料  
  
#### 若要將值存入變數  
  
-   請在指派陳述式的左邊使用變數名稱。  
  
     下列範例會設定變數 `alpha` 的值。  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     指派陳述式右邊所產生的值便會存入變數中。  
  
## 取得變數的資料  
 將變數名稱納入運算式中，即可擷取變數的值。  
  
#### 若要擷取變數的值  
  
-   請在運算式中使用變數名稱。  只要是可以使用常數或常值的任何地方，都可以使用變數，除了定義常數值的運算式之外。  
  
     \-或\-  
  
-   請在指派陳述式的等號 \(`=`\) 後使用變數名稱。  
  
     下列範例會讀取變數 `startValue` 的值，然後在運算式中使用變數 `counter` 的值。  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     運算式中的變數值就會如同常數一般使用，接著結果會儲存在指派陳述式左邊的變數或屬性 \(Property\) 中。  
  
## 請參閱  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)