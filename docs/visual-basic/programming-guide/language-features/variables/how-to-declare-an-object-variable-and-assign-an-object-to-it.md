---
title: "How to: Declare an Object Variable and Assign an Object to It in Visual Basic | Microsoft Docs"
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
  - "object variables, declaring"
  - "declaring object variables"
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Declare an Object Variable and Assign an Object to It in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以用 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 指定 `As Object`，宣告 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) 的變數。  將物件放在指派陳述式 \(Assignment Statement\) 或初始化子句中的等號 \(`=`\) 之後，可以將物件紙指派給這種變數。  
  
## 範例  
 下列範例會宣告 `Object` 變數，並且將目前的執行個體 \(Instance\) 指派給這個變數。  
  
```  
  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 您可以將變數初始化為宣告的一部分，來結合宣告與指派。  下列範例相當於前項範例。  
  
```  
Dim thisObject As Object = "This is an Object"  
```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   對 <xref:System> 命名空間的參考。  
  
-   放置 `Dim` 陳述式的類別、結構或模組。  
  
-   放置指派陳述式 \(Assignment Statement\) 的程序。  
  
## 請參閱  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)