---
title: "&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning) | Microsoft Docs"
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
  - "vbc40008"
  - "bc40008"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40008"
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

陳述式 \(Statement\) 會嘗試存取已利用 <xref:System.ObsoleteAttribute> 屬性 \(Attribute\) 和指示詞標示，將它視為警告的程式設計項目。  
  
 您可以套用 <xref:System.ObsoleteAttribute>，標記任何將來不會再使用的程式設計項目。  如果這麼做，可以將屬性 \(attribute\) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 \(property\) 設定為 `True` 或 `False`。  如果將它設定為 `True`，嘗試使用此項目時，編譯器會將其視為錯誤。  如果將它設定為 `False`，或讓它預設值為 `False`，嘗試使用此項目時，編譯器會發出警告。  
  
 根據預設，這個訊息是個警告，因為 <xref:System.ObsoleteAttribute> 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性為 `False`。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID**︰BC40008  
  
### 若要更正這個錯誤  
  
-   確定原始程式碼參考的項目名稱拼寫正確。  
  
## 請參閱  
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)