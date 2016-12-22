---
title: "XML comment exception must have a &#39;cref&#39; attribute | Microsoft Docs"
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
  - "bc42319"
  - "vbc42319"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42319"
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML comment exception must have a &#39;cref&#39; attribute
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

\<exception\> 標記 \(Tag\) 提供方法來記下方法可能會擲回的例外狀況。  必要的 `cref` 屬性會指定成員的名稱，這是由文件產生器進行檢查。  如果該成員已存在，則會將它轉譯成文件檔案中的正式項目名稱。  
  
 **錯誤 ID：**BC42319  
  
### 若要更正這個錯誤  
  
-   如下將 `cref` 屬性加入至例外狀況：  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## 請參閱  
 [\<exception\>](../../../visual-basic/language-reference/xmldoc/exception.md)   
 [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)   
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)