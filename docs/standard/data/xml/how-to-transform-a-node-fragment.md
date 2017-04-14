---
title: "HOW TO：轉換節點片段 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# HOW TO：轉換節點片段
當您轉換包含於 <xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XPath.XPathDocument> 物件的資料時，XSLT 轉換會套用至整個文件。  換言之，如果您要傳入的節點不是文件的根節點，則不會阻止轉換程序取得已載入文件中的所有節點。  若要轉換節點片段，您必須建立僅含有該節點片段的單獨物件，再將該物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。  
  
## 程序  
  
#### 轉換節點片段  
  
1.  建立包含來源文件的物件。  
  
2.  尋找要轉換的節點片段。  
  
3.  建立僅具有該節點片段的單獨物件。  
  
4.  將該節點片段傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。  
  
## 範例  
 下列範例會轉換節點片段，並將結果輸出至主控台。  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### 輸入  
  
##### books.xml  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### single.xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### 輸出  
 書名為《The Confidence Man》。  
  
## 請參閱  
 [使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)