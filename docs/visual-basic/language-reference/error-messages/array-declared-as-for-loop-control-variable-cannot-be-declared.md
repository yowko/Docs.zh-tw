---
title: "Array declared as for loop control variable cannot be declared with an initial size | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc32039"
  - "bc32039"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32039"
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Array declared as for loop control variable cannot be declared with an initial size
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`For Each` 迴圈使用陣列做為 *element* 反覆運算變數，但是又初始化該陣列。  
  
 下列陳述式 \(Statement\) 顯示這種錯誤是如何產生的：  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 第一個 `For Each` 陳述式是存取 `arrayList` 項目的正確方式。  第二個 `For Each` 陳述式則會產生此錯誤。  
  
 **錯誤 ID**：BC32039  
  
### 若要更正這個錯誤  
  
-   從 *element* 反覆運算變數的宣告中移除初始化設定。  
  
## 請參閱  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)