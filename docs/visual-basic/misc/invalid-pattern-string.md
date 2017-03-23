---
title: "無效的模式字串 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# 無效的模式字串
在搜尋的 `Like` 作業中指定的模式字串無效。  
  
### 更正這個錯誤  
  
1.  請檢閱清單運算式的有效字元。  
  
2.  在模式範圍中，確定起始範圍字元小於結束範圍字元，如同在 `[a-z]`。  
  
3.  在模式範圍中，確定沒有相鄰的多個連字號，如同在 `[a--z]`。  
  
4.  以右括弧結束模式範圍。  
  
## 請參閱  
 [Like Operator](../../visual-basic/language-reference/operators/like-operator.md)