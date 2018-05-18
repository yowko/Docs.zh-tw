---
title: XML 處理選項
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b1295185bf0fa06884b1332762d01f86f138a0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xml-processing-options"></a>XML 處理選項
請參閱下表，以取得您可以用來處理 XML 資料的 Microsoft 技術清單。  
  
## <a name="net-framework-options"></a>.NET Framework 選項  
  
|**選項**|**處理型別**|**描述**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(<xref:System.Xml.Linq> 命名空間)|記憶體中|-   根據 .NET Framework Language-Integrated Query (LINQ) 技術。<br />-   提供類似於物件、關聯式資料和 XML 資料適用之 SQL 的查詢體驗。<br />-   提供直覺式文件建立和轉換功能。<br />-   如果您要撰寫新程式碼，請使用這個選項。|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|資料流形式|-   提供快速、非快取的順向方式來存取 XML 資料。<br />-   您可以使用 <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> 方法建立物件，並且使用 <xref:System.Xml.XmlReaderSettings> 類別來指定此物件上所要啟用的功能集合。|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|資料流形式|-   提供快速、非快取的順向方式來產生 XML 資料。<br />-   您可以使用 <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> 方法建立物件，並且使用 <xref:System.Xml.XmlWriterSettings> 類別來指定此物件上所要啟用的功能集合。|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|記憶體中|-   實作 [W3C 文件物件模型 (DOM) 層級 1 核心](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html)和 [DOM 層級 2 核心](https://www.w3.org/TR/DOM-Level-2-Core/)建議。<br />-   您可以使用以常用 DOM 模型為基礎的方法與屬性來建立、插入、移除及修改節點。<br />-   如果您要修改現有的程式碼來利用 W3C DOM，請使用這個選項。|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|記憶體中|-   使用資料指標模型提供幾個編輯選項和導覽功能。<br />-   XML 文件可包含在 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中。<br />-   針對 XML 的唯讀處理提供了絕佳的效能。<br />-   如果您要修改包含 XPath 查詢或 XSLT 轉換的現有程式碼，請使用這個選項。|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|記憶體中|-   提供使用 XSL 轉換來轉換 XML 資料的選項。<br />-    [XSLT 編譯器 (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) 可讓您在應用程式中參考先行編譯的轉換。|  
  
## <a name="win32-and-com-based-options"></a>Win32 和 COM 架構的選項  
  
|**選項**|**描述**|  
|----------------|---------------------|  
|[XmlLite](https://msdn.microsoft.com/library/ms752872.aspx)|-   一種快速、安全、非快取、順向的 XML 剖析器，可幫助您建置高效能的 XML 應用程式。<br />-   可搭配可使用動態連結程式庫 (DLL) 的任何語言一起使用；我們建議使用 C++。|  
|[MSXML](https://msdn.microsoft.com/library/ms763742.aspx)|-   COM 架構的技術，用於處理 Windows 作業系統隨附的 XML。<br />-   提供 DOM 的原始實作 (包含對於 XPath 和 XSLT 的支援)。<br />-   包含 SAX2 事件架構剖析器。|  
  
## <a name="see-also"></a>請參閱  
 [使用 DOM 模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XSLT 編譯器 (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
