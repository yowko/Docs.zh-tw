---
title: "XML Literals and the XML 1.0 Specification (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML literals [Visual Basic], XML 1.0 specification"
ms.assetid: 46f046e5-293c-41a3-b893-4e5f6e32e78a
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# XML Literals and the XML 1.0 Specification (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的 XML 常值語法支援大部分的可延伸標記語言 \(XML\) 1.0 規格。  如需 XML 1.0 規格的詳細資訊，請參閱 W3C 網站上的[可延伸標記語言 \(XML\) 1.0](http://go.microsoft.com/fwlink/?LinkId=73927) \(英文\)。  
  
## Visual Basic 不支援的項目  
  
-   XML 常值 \(Literal\) 不能包含文件類型定義 \(DTD\)。  
  
-   XML 文件常值必須以 XML 文件宣告開頭。  
  
-   XML 常值一行不能包含超過 65,535 個字元。  
  
-   XML 命名空間前置字元、項目名稱及屬性名稱不能包含超過 1,024 個字元。  
  
## Visual Basic 支援的額外功能  
  
-   文件和項目常值中允許的內嵌運算式語法不是有效的 XML。  
  
## 請參閱  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)