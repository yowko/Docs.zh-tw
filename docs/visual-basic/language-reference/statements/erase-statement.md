---
title: "Erase Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Erase"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Erase keyword"
  - "Erase statement"
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Erase Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

可用於釋放陣列變數和解除配置其元素的記憶體。  
  
## 語法  
  
```  
Erase arraylist  
```  
  
## 組件  
 `arraylist`  
 必要項。  可消除的陣列變數清單。  變數之間以逗號 \( , \) 來分隔。  
  
## 備註  
 `Erase` 陳述式只可以出現在程序層次。  這表示您可以在程序內釋放陣列，但是不可以在類別或模組層次釋放陣列。  
  
 `Erase` 陳述式的效用和指派 `Nothing` 給每個陣列變數相同。  
  
## 範例  
 下列範例會使用 `Erase` 陳述式清除兩個陣列，並釋放它們的記憶體 \(分別有 1000 和 100 個儲存項目\)。  然後，`ReDim` 陳述式會將新的陣列執行個體指派給三維陣列。  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## 請參閱  
 [Nothing](../../../visual-basic/language-reference/nothing.md)   
 [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md)