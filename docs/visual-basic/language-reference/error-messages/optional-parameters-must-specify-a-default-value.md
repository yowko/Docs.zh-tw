---
title: "Optional parameters must specify a default value | Microsoft Docs"
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
  - "vbc30812"
  - "bc30812"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30812"
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Optional parameters must specify a default value
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

選擇性參數必須提供預設值，當呼叫程序沒有提供參數時可以使用。  
  
 **錯誤 ID**︰BC30812  
  
### 若要更正這個錯誤  
  
-   請指定選擇性參數的預設值，例如：  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## 請參閱  
 [Optional](../../../visual-basic/language-reference/modifiers/optional.md)