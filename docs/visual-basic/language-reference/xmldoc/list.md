---
title: "&lt;list&gt; (Visual Basic) | Microsoft Docs"
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
  - "listheader XML tag"
  - "<item> XML tag"
  - "<list> XML tag"
  - "<listheader> XML tag"
  - "term XML tag"
  - "list XML tag"
  - "<description> XML tag"
  - "description XML tag"
  - "item XML tag"
  - "<term> XML tag"
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# &lt;list&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

定義清單或表格。  
  
## 語法  
  
```  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### 參數  
 `type`  
 清單的型別。  必須是項目符號清單的 "bullet"，編號清單的 "number"，或雙欄式資料表的 "table"。  
  
 `term`  
 只適用於 `type` 是 "table" 時。 要定義的術語，其定義在說明標記中。  
  
 `description`  
 當 `type` 是 "bullet" 或 "number"，`description` 是清單中的項目。當 `type` 是 "table"，`description` 是 `term` 的定義。  
  
## 備註  
 `<listheader>` 區塊會定義表格或定義清單的標題。  在定義表格時，您只需提供一個 `term` 項目做為標題。  
  
 清單中的每個項目都以 `<item>` 區塊來指定。  建立定義清單時，您必須指定 `term` 和 `description`。  但是對於表格、項目符號清單或編號清單，您只需提供 `description` 的項目。  
  
 在清單或表格中可以有全部需要的 `<item>` 區塊。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例會使用 `<list>` 標記 \(Tag\)，在註解區段中定義項目符號清單。  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/list_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)