---
title: "&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly | Microsoft Docs"
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
  - "vbc30910"
  - "bc30910"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30910"
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

類別或介面繼承自基底類別 \(Base Class\) 或介面，但具有較不受限的存取層級。  
  
 例如，`Public` 介面會繼承自 `Friend` 介面，或者 `Protected` 類別會繼承自 `Private` 類別。  這樣會公開 \(Expose\) 基底類別或介面，在超過想要的層級中存取。  
  
 **錯誤 ID：**BC30910  
  
### 若要更正這個錯誤  
  
-   將衍生類別 \(Derived Class\) 或介面的存取層級變更為至少與基底類別或介面一樣受限的層級。  
  
     \-或\-  
  
-   如果您需要較不受限的存取層級，請移除 `Inherits` 陳述式 \(Statement\)。  您無法繼承更具限制的基底類別或介面。  
  
## 請參閱  
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)