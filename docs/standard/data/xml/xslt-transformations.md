---
title: "XSLT 轉換 | Microsoft Docs"
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
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 4
---
# XSLT 轉換
可延伸樣式表語言轉換 \(XSLT\) 可讓您將來源 XML 文件的內容轉換成另一種不同格式或結構的文件。  例如，您可以使用 XSLT 將 XML 轉換成網站上使用的 HTML，或將它轉換成只包含應用程式所需欄位的文件。  這個轉換程序是由 [W3C XSL 轉換 \(XSLT\) 1.0 版建議事項](http://go.microsoft.com/fwlink/?LinkID=49919)所指定。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> 類別是 .NET Framework 中的 XSLT 處理器。  <xref:System.Xml.Xsl.XslCompiledTransform> 類別支援 W3C XSLT 1.0 建議事項。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，<xref:System.Xml.Xsl.XslTransform> 類別已過時。  <xref:System.Xml.Xsl.XslCompiledTransform> 類別是 XSLT 引擎的新實作。  其中包含效能增進與新的安全性功能。  建議的作法是使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別建立 XSLT 應用程式。  
  
## 在本節中  
 [使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 提供有關使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的資訊。  
  
 [從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 討論如何從 <xref:System.Xml.Xsl.XslTransform> 類別移轉程式碼。  
  
 [XSLT 編譯器 \(xsltc.exe\)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 提供有關使用 XSLT 編譯器的資訊。  
  
 [使用 XslTransform 類別進行 XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 提供有關使用 <xref:System.Xml.Xsl.XslTransform> 類別的資訊。  
  
 **注意**：在 .NET Framework 2.0 版中，<xref:System.Xml.Xsl.XslTransform> 類別已過時。  
  
## 參考  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## 相關章節  
 [XML 文件和資料](../../../../docs/standard/data/xml/index.md)