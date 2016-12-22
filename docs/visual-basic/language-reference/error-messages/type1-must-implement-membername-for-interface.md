---
title: "&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30154"
  - "bc30154"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30154"
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

'\<typename\>' 須針對介面 '\<interfacename\>' 實作 '\<membername\>'實作屬性必須擁有相對應的 'ReadOnly'\/'WriteOnly' 規範。  
  
 類別或結構要求實作一個介面，但是未實作介面所定義的程序、屬性 \(Property\) 或事件。  必須實作介面的每個成員。  
  
 **錯誤 ID**︰BC30154  
  
### 若要更正這個錯誤  
  
1.  使用和介面中所定義相同的名稱和簽章來宣告成員。  確定至少包含 `End Function`、`End Sub` 或 `End Property` 陳述式。  
  
2.  在 `Function`、`Sub`、`Property` 或 `Event` 陳述式的結尾加入 `Implements` 子句。  例如：  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  實作屬性 \(Property\) 時，確定 `ReadOnly` 或 `WriteOnly` 的使用方式和介面定義相同。  
  
4.  實作屬性時，宣告適當的 `Get` 和 `Set` 程序。  
  
## 請參閱  
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)