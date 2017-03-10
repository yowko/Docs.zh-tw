---
title: "Initializer expected | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30996"
  - "bc30996"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30996"
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Initializer expected
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

您嘗試使用物件初始設定式來宣告類別的執行個體，但初始設定式的初始設定清單是空的，如下列範例所示。  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 在初始設定式清單中，必須至少初始化一個欄位或屬性，如下列範例所示。  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **錯誤 ID**：BC30996  
  
### 若要更正這個錯誤  
  
1.  在初始設定式中至少初始化一個欄位或屬性，或者不要使用物件初始設定式。  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)