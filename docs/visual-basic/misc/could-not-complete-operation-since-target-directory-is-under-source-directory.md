---
title: "無法完成作業，因為目標目錄在來源目錄底下 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrIO_CyclicOperation"
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# 無法完成作業，因為目標目錄在來源目錄底下
循環作業失敗。 循環作業會循環，因此無法完成。 例如，物件 A 可能會嘗試繼承自物件 B，而物件 B 又接著繼承自物件 A。  
  
### 更正這個錯誤  
  
-   繼承時，請確定沒有循環參考。  
  
## 請參閱  
 [Error Types](../../visual-basic/programming-guide/language-features/error-types.md)   
 [Debugging Basics: Breakpoints](http://msdn.microsoft.com/zh-tw/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)