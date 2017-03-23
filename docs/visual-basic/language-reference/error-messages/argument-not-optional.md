---
title: "Argument not optional (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID449"
dev_langs: 
  - "VB"
ms.assetid: 76e7bcf3-24ed-4cd5-945b-b98f1c76944b
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Argument not optional (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

引數的數目和型別必須符合所預期的。  不是引數的數目錯誤，就是省略了某個非選擇性的引數。  引數只有在程序定義中宣告為 `Optional` 的情況下，才可以從使用者定義程序的呼叫中省略。  
  
### 若要更正這個錯誤  
  
1.  請提供所有必要的引數。  
  
2.  請確定省略的引數是選擇性的。  如果不是選擇性的，則在呼叫中提供該引數，或者在定義中宣告參數為 `Optional`。  
  
## 請參閱  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)