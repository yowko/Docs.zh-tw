---
title: "Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30663"
  - "vbc30663"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30663"
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

屬性 \(Attribute\) 只可以套用一次。  `AttributeUsage` 屬性會決定是否可以多次套用屬性。  
  
 **錯誤 ID**︰BC30663  
  
### 若要更正這個錯誤  
  
1.  請確定屬性 \(Attribute\) 只套用了一次。  
  
2.  如果您使用自行開發的自訂屬性，請考慮變更其 `AttributeUsage` 屬性，讓這些屬性可以多次使用，如下列範例所示。  
  
    ```  
    <AttributeUsage(AllowMultiple := True)>  
    ```  
  
## 請參閱  
 <xref:System.AttributeUsageAttribute>   
 [建立自訂屬性](../Topic/Creating%20Custom%20Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [AttributeUsage](../Topic/AttributeUsage%20\(C%23%20and%20Visual%20Basic\).md)