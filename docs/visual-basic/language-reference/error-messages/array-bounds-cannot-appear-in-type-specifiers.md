---
title: "Array bounds cannot appear in type specifiers | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30638"
  - "bc30638"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30638"
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Array bounds cannot appear in type specifiers
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

陣列大小不可以宣告為資料型別規範的一部分。  
  
 **錯誤 ID**：BC30638  
  
### 若要更正這個錯誤  
  
-   請緊接在變數名稱之後指定陣列的大小，而不是將陣列大小放在型別之後，如以下範例中所示。  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   請定義陣列並以想要的元素數目將它初始化，如以下範例中所示。  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## 請參閱  
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)