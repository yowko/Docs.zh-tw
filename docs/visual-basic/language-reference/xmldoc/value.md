---
title: "&lt;value&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "<value> XML tag"
  - "value XML tag"
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &lt;value&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定屬性的說明。  
  
## 語法  
  
```  
<value>property-description</value>  
```  
  
#### 參數  
 `property-description`  
 屬性的描述。  
  
## 備註  
 使用 `<value>` 標記來說明屬性。  請注意，當您透過 Visual Studio 開發環境的程式碼精靈加入屬性時，該精靈會為新屬性加上 [\<summary\>](../../../visual-basic/language-reference/xmldoc/summary.md) 標記。  接著，您必須手動加入 `<value>` 標記，來說明該屬性所表示的值。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例會使用 `<value>` 標記，來說明 `Counter` 屬性要保存哪個值。  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)