---
title: "XML entity references are not supported | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31180"
  - "bc31180"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31180"
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# XML entity references are not supported
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

未在 XML 1.0 規格中定義的實體參考 \(例如，`©`\) 都會當做 XML 常值的值而加入。  XML 常值中僅支援 `&`、`"`、`<`、`>` 和 `'` XML 實體參考。  
  
 **錯誤 ID**：BC31180  
  
### 若要更正這個錯誤  
  
-   移除不支援的實體參考。  
  
## 請參閱  
 [XML Literals and the XML 1.0 Specification](../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)