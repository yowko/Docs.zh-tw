---
title: "&#39;&lt;keyword&gt;&#39; is valid only within an instance method | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30043"
  - "vbc30043"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30043"
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &#39;&lt;keyword&gt;&#39; is valid only within an instance method
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`Me`、`MyClass` 和 `MyBase` 關鍵字參考特定的類別執行個體。  您不能在共用的 `Function` 或 `Sub` 程序中使用他們。  
  
 **錯誤 ID**：BC30043  
  
### 若要更正這個錯誤  
  
-   移除程序中的關鍵字，或移除程序宣告中的 `Shared` 關鍵字。  
  
## 請參閱  
 [Object Variable Assignment](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)