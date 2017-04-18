---
title: "XSLT 擴充物件 | Microsoft Docs"
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
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# XSLT 擴充物件
擴充物件可用來擴充樣式表的功能。  <xref:System.Xml.Xsl.XsltArgumentList> 類別會維護擴充物件。  
  
 以下是使用擴充物件而不使用內嵌指令碼的優點：  
  
-   提供較佳的類別封裝和重複使用。  
  
-   允許樣式表更簡潔且更易於維護。  
  
 使用 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法，將 XSLT 擴充物件加入至 <xref:System.Xml.Xsl.XsltArgumentList> 物件。  限定名稱和命名空間 URI 於當時與擴充物件產生關聯。  
  
> [!NOTE]
>  呼叫 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法，需要 FullTrust 使用權限集合。  如需詳細資訊，請參閱[Code Access Security](http://msdn.microsoft.com/zh-tw/23a20143-241d-4fe5-9d9f-3933fd594c03)與[NIB: Named Permission Sets](http://msdn.microsoft.com/zh-tw/08250d67-c99d-4ab0-8d2b-b0e12019f6e3)。  
  
 從擴充物件傳回的資料型別，是 `number`、`string`、`Boolean` 及 `node set` 這四種基本 XPath 資料型別之一。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> 類別目前不支援任何允許傳遞未指定的參數數目，並以 `params` 關鍵字定義的方法。  使用以 `params` 關鍵字定義之任何方法的 XSLT 樣式表將無法正常運作。  如需詳細資訊，請參閱 [params](../Topic/params%20\(C%23%20Reference\).md)。  
  
### 使用 XSLT 擴充物件  
  
1.  使用 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法，建立 <xref:System.Xml.Xsl.XsltArgumentList> 物件並加入擴充物件。  
  
2.  從樣式表呼叫擴充物件。  
  
3.  將 <xref:System.Xml.Xsl.XsltArgumentList> 物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。  
  
## 請參閱  
 [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)   
 [XSLT 安全性考量](../../../../docs/standard/data/xml/xslt-security-considerations.md)