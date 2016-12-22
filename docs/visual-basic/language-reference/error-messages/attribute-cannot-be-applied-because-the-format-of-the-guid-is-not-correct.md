---
title: "&#39;&lt;attribute&gt;&#39; cannot be applied because the format of the GUID &#39;&lt;number&gt;&#39; is not correct | Microsoft Docs"
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
  - "vbc32500"
  - "bc32500"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32500"
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;attribute&gt;&#39; cannot be applied because the format of the GUID &#39;&lt;number&gt;&#39; is not correct
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`COMClassAttribute` 屬性區塊指定的全域唯一識別碼 \(GUID\) 並不符合正確的 GUID 格式。  `COMClassAttribute` 會使用 GUID 做為類別、介面和建立事件的唯一識別。  
  
 GUID 包含 16 個位元組，前面 8 個為數值，後面 8 個為二進位值。  它是由 Microsoft 公用程式 \(例如 uuidgen.exe\) 所產生，並確保隨時隨地都是唯一的。  
  
 **錯誤 ID**：BC32500  
  
### 若要更正這個錯誤  
  
1.  請判斷識別 COM 物件所需要之一個或多個正確的 GUID。  
  
2.  請確定提供給 `COMClassAttribute` 屬性 \(Attribute\) 區塊的 GUID 字串複製正確。  
  
## 請參閱  
 <xref:System.Guid>   
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)