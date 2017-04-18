---
title: "處理記憶體中的 XML 資料 | Microsoft Docs"
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
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# 處理記憶體中的 XML 資料
Microsoft .NET Framework 包含三種處理 XML 資料的模型：<xref:System.Xml.XmlDocument> 類別、<xref:System.Xml.XPath.XPathDocument> 類別及 [LINQ to XML](../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md)。  
  
 <xref:System.Xml.XmlDocument> 類別會實作 W3C 文件物件模型 \(DOM\) 層級 1 核心及核心 DOM 層級 2 建議事項。  DOM 是 XML 文件的記憶體中 \(快取\) 樹狀結構表示。  透過 <xref:System.Xml.XmlDocument> 及其相關類別，您可以建構 XML 文件、載入並存取資料、修改資料，以及儲存變更。  
  
 <xref:System.Xml.XPath.XPathDocument> 類別是唯讀的記憶體中資料存放區，以 XPath 資料模型為基礎。  <xref:System.Xml.XPath.XPathNavigator> 類別提供了數種可在唯讀 <xref:System.Xml.XPath.XPathDocument> 類別及 <xref:System.Xml.XmlDocument> 類別包含的 XML 文件中使用游標模型的編輯選項與巡覽功能。  
  
 [LINQ to XML](../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md) 是 .NET Framework 3.5 版中用來處理 XML 資料的新模型。  它是利用 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) 的記憶體中模型。  LINQ 會擴充 C\# 和 Visual Basic 的語言語法，以提供新的查詢功能。  
  
## 在本節中  
 [使用 DOM 模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 討論如何使用 <xref:System.Xml.XmlDocument> 及其相關類別來處理 XML 資料。  
  
 [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 討論如何使用 <xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDocument> 及 <xref:System.Xml.XPath.XPathNavigator> 類別來處理 XML 資料。  
  
 [使用 LINQ to XML 處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 提供 LINQ to XML 的簡短概觀，並提供 LINQ to XML 文件的連結。  
  
## 相關章節  
 [XML 文件和資料](../../../../docs/standard/data/xml/index.md)