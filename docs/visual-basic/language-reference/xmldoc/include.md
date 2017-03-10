---
title: "&lt;include&gt; (Visual Basic) | Microsoft Docs"
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
  - "include XML tag"
  - "<include> XML tag"
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &lt;include&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

請參閱另一個檔案中原始程式碼之型別和成員的說明。  
  
## 語法  
  
```  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### 參數  
 `filename`  
 必要項。  為含有文件的檔案名稱。  可將檔案名稱加上路徑。  以雙引號 \(" "\) 將 `filename` 括起來。  
  
 `tagpath`  
 必要項。  `filename` 中導向標記 \(Tag\) `name` 的標記路徑。  以雙引號 \(" "\) 將路徑括起來。  
  
 `name`  
 必要項。  註解前之標記內的名稱規範。  `Name` 會有 `id`。  
  
 `id`  
 必要項。  註解前面之標記的 ID。  以單引號 \(' '\) 將 ID 括起來。  
  
## 備註  
 使用 `<include>` 標記來參考其他檔案內的註解，這些檔案描述了您原始程式碼中的型別及成員。  除了將文件註解直接放置在您原始程式碼檔案中，您也可以使用這種方法。  
  
 `<include>` 標記會使用＜W3C XML Path Language \(XPath\) Version 1.0 Recommendation＞。  如需如何自訂 `<include>` 用途的詳細資訊，請造訪 http:\/\/www.w3.org\/TR\/xpath。  
  
## 範例  
 這個範例會使用 `<include>` 標記，從 `commentFile.xml` 檔案匯入成員文件註解。  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/include_1.vb)]  
  
 `commentFile.xml` 的格式如下。  
  
```  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)