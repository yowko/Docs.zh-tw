---
title: "&lt;permission&gt; (Visual Basic) | Microsoft Docs"
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
  - "<permission> XML tag"
  - "permission XML tag"
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &lt;permission&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定成員的必要使用權限。  
  
## 語法  
  
```  
<permission cref="member">description</permission>  
```  
  
#### 參數  
 `member`  
 對可以從目前編譯環境呼叫的成員或欄位的參考。  編譯器會檢查特定的程式碼項目是否存在，並在輸出的 XML 中將 `member` 轉譯為正式的項目名稱。  以雙引號 \(" "\) 括住 `member`。  
  
 `description`  
 成員存取的描述。  
  
## 備註  
 使用 `<permission>` 標記來說明成員的存取。  使用 <xref:System.Security.PermissionSet> 類別來指定成員的存取。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例會使用 `<permission>` 標記，來說明 `ReadFile` 方法需要 <xref:System.Security.Permissions.FileIOPermission>。  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/permission_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)