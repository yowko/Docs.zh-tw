---
title: "How to: Access XML Descendant Elements (Visual Basic) | Microsoft Docs"
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
  - "XML descendent axis property [Visual Basic]"
  - "XML axis [Visual Basic], descendent"
  - "descendent axis property [Visual Basic]"
  - "XML [Visual Basic], accessing"
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Access XML Descendant Elements (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

這個範例顯示如何使用子代 \(Descendant\) 軸屬性存取具有指定名稱以及在 XML 項目下包含的所有 XML 項目。  具體而言，它會使用 `Value` 屬性來取得集合 \(由 `name` 子代軸屬性傳回\) 中第一個項目的值。  `name` 子代軸屬性會取得所有名為 `name`，且包含在 `contacts` 物件中的項目。  這個範例也會使用 `phone` 子代軸屬性存取 `contacts` 物件中所有名為 `phone` 的子代。  
  
## 範例  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-access-xml-descen_1.vb)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   對 <xref:System.Xml.Linq> 命名空間的參考。  
  
## 請參閱  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName>   
 [XML Descendant Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [XML Value Property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)   
 [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)