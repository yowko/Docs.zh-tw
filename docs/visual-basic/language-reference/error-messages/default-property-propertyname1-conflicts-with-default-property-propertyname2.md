---
title: "Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc40007"
  - "bc40007"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40007"
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告的屬性 \(Property\) 名稱與在基底類別中定義的屬性 \(Property\) 名稱相同。  在此情況下，此類別中的屬性 \(Property\) 應該會遮蔽基底類別屬性 \(Property\)。  
  
 這是一個警告訊息。  預設會使用 `Shadows`。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID：**BC40007  
  
### 若要更正這個錯誤  
  
-   請將 `Shadows` 關鍵字加入至宣告中，或是變更正在宣告的屬性 \(Property\) 名稱。  
  
## 請參閱  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)