---
title: "System.Xml 使用方式 | Microsoft Docs"
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
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# System.Xml 使用方式
本節中的數種類型的使用方式說明 <xref:System.Xml?displayProperty=fullName> 命名空間，可以用來表示 XML 資料。  
  
 **X 不** 使用 <xref:System.Xml.XmlNode> 或 <xref:System.Xml.XmlDocument> 來代表 XML 資料。 使用的執行個體非 <xref:System.Xml.XPath.IXPathNavigable>, ，<xref:System.Xml.XmlReader>, ，<xref:System.Xml.XmlWriter>, ，或是子類型的 <xref:System.Xml.Linq.XNode> 改。`XmlNode` 和 `XmlDocument` 並未設計成在公用 Api 公開。  
  
 **✓ 執行** 使用 `XmlReader`, ，`IXPathNavigable`, ，或是子類型的 `XNode` 做為輸入或輸出的接受或傳回 XML 的成員。  
  
 使用這些抽象概念，而不是 `XmlDocument`, ，`XmlNode`, ，或 <xref:System.Xml.XPath.XPathDocument>, ，因為這樣以減少從記憶體中 XML 文件的特定實作的方法，並讓它們使用虛擬公開 （expose） 的 XML 資料來源 `XNode`, ，`XmlReader`, ，或 <xref:System.Xml.XPath.XPathNavigator>。  
  
 **X 不** 子類別 `XmlDocument` 如果您想要建立型別，表示基礎物件模型或資料來源的 XML 檢視。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)