---
title: "XML 處理選項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 18f8f9c76a1842517340eaa3f74b4778f869403e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xml-processing-options"></a>XML 處理選項
請參閱下表，以取得您可以用來處理 XML 資料的 Microsoft 技術清單。  
  
## <a name="net-framework-options"></a>.NET Framework 選項  
  
|**選項**|**處理類型**|**說明**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(<xref:System.Xml.Linq> 命名空間)|記憶體中|-以.net framework language-integrated Query (LINQ) 技術為基礎。<br />-提供類似於 SQL 物件、 關聯式資料、 與 XML 資料的查詢體驗。<br />-提供直覺式文件建立和轉換功能。<br />-如果您要撰寫新程式碼，請使用此選項。|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|資料流形式|-提供快速、 非快取、 順向的方式來存取 XML 資料。<br />-您可以使用來建立物件<xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType>方法，並指定要啟用物件上使用的功能組<xref:System.Xml.XmlReaderSettings>類別。|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|資料流形式|-提供快速、 非快取、 順向的方式，以產生 XML 資料。<br />-您可以使用來建立物件<xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType>方法，並指定要啟用物件上使用的功能組<xref:System.Xml.XmlWriterSettings>類別。|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|記憶體中|-實作[W3C 文件物件模型 (DOM) 層級 1 核心](http://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html)和[DOM 層級 2 核心](http://www.w3.org/TR/DOM-Level-2-Core/)建議。<br />-您可以建立、 插入、 移除及修改節點使用的方法和常用 DOM 模型為基礎的屬性。<br />-使用此選項，如果您要修改現有的程式碼來利用 W3C DOM|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|記憶體中|-提供數個編輯選項和使用資料指標模型的瀏覽功能。<br />XML 文件中可包含<xref:System.Xml.XPath.XPathDocument>或<xref:System.Xml.XmlDocument>物件。<br />-提供了絕佳的唯讀處理 XML 的效能。<br />-如果您要修改包含 XPath 查詢或 XSLT 轉換的現有程式碼，請使用此選項。|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|記憶體中|-提供來轉換使用 XSL 轉換 XML 資料的選項。<br />- [XSLT 編譯器 (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)可讓您參考預先編譯您的應用程式中的轉換。|  
  
## <a name="win32-and-com-based-options"></a>Win32 和 COM 架構的選項  
  
|**選項**|**說明**|  
|----------------|---------------------|  
|[XmlLite](http://go.microsoft.com/fwlink/?LinkId=93723)|的順向的 XML 剖析器，可協助您建置高效能快速、 安全、 非快取，XML 應用程式。<br />-適用於任何語言都可以使用動態連結程式庫 (Dll)。我們建議使用 c + +。|  
|[MSXML](http://go.microsoft.com/fwlink/?LinkId=93722)|-COM 為基礎的技術處理隨附於 Windows 作業系統的 XML。<br />-提供 DOM 的原始實作 XPath 和 XSLT 的支援。<br />-包含 SAX2 事件架構剖析器。|  
  
## <a name="see-also"></a>另請參閱  
 [使用 DOM 模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XSLT 編譯器 (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
