---
title: "&#39;AddressOf&#39; operand must be the name of a method (without parentheses) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30577"
  - "bc30577"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30577"
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &#39;AddressOf&#39; operand must be the name of a method (without parentheses)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`AddressOf` 運算子會建立參考特定程序的程序委派執行個體。  語法如下。  
  
 `AddressOf` `procedurename`  
  
 您在 `AddressOf` 之後的引數加上括號，而這是不需要的。  
  
 **錯誤 ID**：BC30577  
  
### 若要更正這個錯誤  
  
1.  移除 `AddressOf` 之後引數的括號。  
  
2.  確定引數是方法名稱。  
  
## 請參閱  
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)