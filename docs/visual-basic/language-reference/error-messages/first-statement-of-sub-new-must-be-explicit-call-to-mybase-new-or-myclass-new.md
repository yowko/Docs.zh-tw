---
title: "First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30920"
  - "bc30920"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30920"
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

類別建構函式 \(Constructor\) 不會明確呼叫基底類別 \(Base Class\) 建構函式，並且將以 <xref:System.ObsoleteAttribute> 屬性和指示詞標記隱含基底類別建構函式，將它視為錯誤處理。  
  
 當衍生類別建構函式未呼叫基底類別建構函式時，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會嘗試產生對無參數基底類別建構函式的隱含呼叫。  如果基底類別中沒有不需引數即可呼叫存取的建構函式，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 不會產生隱含呼叫。  在這個案例中，必要的建構函式會標記著 <xref:System.ObsoleteAttribute> 屬性，這樣 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 便不會呼叫它。  
  
 您可以套用 <xref:System.ObsoleteAttribute>，標記任何將來不會再使用的程式設計項目。  如果這麼做，可以將屬性 \(attribute\) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 \(property\) 設定為 `True` 或 `False`。  如果將它設定為 `True`，嘗試使用此項目時，編譯器會將其視為錯誤。  如果將它設定為 `False`，或讓它預設值為 `False`，嘗試使用此項目時，編譯器會發出警告。  
  
 **錯誤 ID**：BC30920  
  
### 若要更正這個錯誤  
  
1.  檢查引號中的錯誤訊息，並進行必要的修正。  
  
2.  包含對 `MyBase.New()` 或 `MyClass.New()` 的呼叫，做為衍生類別中 `Sub New` 的第一個陳述式。  
  
## 請參閱  
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)