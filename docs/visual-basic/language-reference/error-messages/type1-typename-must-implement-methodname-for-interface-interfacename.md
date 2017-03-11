---
title: "&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30149"
  - "bc30149"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30149"
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

類別或結構要求實作一個介面，但是未實作該介面定義的程序。  必須實作介面的每個成員。  
  
 **錯誤 ID**︰BC30149  
  
### 若要更正這個錯誤  
  
1.  使用和介面中所定義相同的名稱和簽章來宣告程序。  確定至少要包含 `End Function` 或 `End Sub` 陳述式。  
  
2.  在 `Function` 或 `Sub` 陳述式的尾端加入 `Implements` 子句。  例如：  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## 請參閱  
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)