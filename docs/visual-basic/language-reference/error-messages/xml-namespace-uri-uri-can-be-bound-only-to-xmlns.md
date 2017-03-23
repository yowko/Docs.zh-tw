---
title: "XML namespace URI &#39;http://www.w3.org/XML/1998/namespace&#39; can be bound only to &#39;xmlns&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc31183"
  - "vbc31183"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31183"
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# XML namespace URI &#39;http://www.w3.org/XML/1998/namespace&#39; can be bound only to &#39;xmlns&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在 XML 命名空間宣告中使用了 http:\/\/www.w3.org\/XML\/1998\/namespace 這個 URI。  這個 URI 是保留的命名空間，而且不可包含在 XML 命名空間宣告中。  
  
 **錯誤 ID**：BC31183  
  
### 若要更正這個錯誤  
  
-   移除 XML 命名空間宣告，或以有效的命名空間 URI 取代 http:\/\/www.w3.org\/XML\/1998\/namespace 這個 URI。  
  
## 請參閱  
 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)