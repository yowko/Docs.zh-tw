---
title: XML 文件和資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5b8e9290231e884b8b78c1f20bc99f5bc4326db
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490905"
---
# <a name="xml-documents-and-data"></a>XML 文件和資料
.NET Framework 提供一組完整且整合的類別，好讓您輕鬆地建置可感知 XML 的應用程式。 下列命名空間中的類別支援 XML 的剖析與撰寫、記憶體中 XML 資料的編輯、資料驗證和 XSLT 轉換。  
  
- <xref:System.Xml>  
  
- <xref:System.Xml.XPath>  
  
- <xref:System.Xml.Xsl>  
  
- <xref:System.Xml.Schema>  
  
- <xref:System.Xml.Linq>  
  
 如需完整清單，請在 [.NET API 瀏覽器](https://docs.microsoft.com/dotnet/api/?term=system.xml)搜尋 "System.Xml"。  
  
 這些命名空間中的類別支援全球資訊網協會 (W3C) 的建議。 例如：  
  
- <xref:System.Xml.XmlDocument?displayProperty=nameWithType> 類別會實作 [W3C 文件物件模型 (DOM) 層級 1 核心](https://www.w3.org/TR/REC-DOM-Level-1/)和 [DOM 層級 2 核心](https://www.w3.org/TR/DOM-Level-2-Core/)的建議事項。  
  
- <xref:System.Xml.XmlReader?displayProperty=nameWithType> 和 <xref:System.Xml.XmlWriter?displayProperty=nameWithType> 類別支援 [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) 和 [XML 中的命名空間](https://www.w3.org/TR/REC-xml-names/)的建議事項。  
  
- <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> 類別中的結構描述支援 [W3C XML Schema Part 1:Structures](https://www.w3.org/TR/xmlschema-1/) (XML 結構描述第 1 部分：結構) 及 [XML Schema Part 2:Datatypes](https://www.w3.org/TR/xmlschema-2/) (資料類型) 建議。  
  
- <xref:System.Xml.Xsl?displayProperty=nameWithType> 命名空間中的類別支援符合 [W3C XSLT 1.0](https://www.w3.org/TR/xslt) 建議事項的 XSLT 轉換。  
  
 .NET Framework 中的 XML 類別提供以下優點：  
  
- **生產力。** [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) 和 [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) 可輕鬆地透過 XML 編寫程式，並提供類似於 SQL 的查詢體驗。  
  
- **擴充性。** .NET Framework 中的 XML 類別可利用抽象基底類別和虛擬方法進行擴充。 例如，您可以建立將快取資料流儲存在本機磁碟之 <xref:System.Xml.XmlUrlResolver> 類別的衍生類別。  
  
- **可外掛式架構。** .NET Framework 提供的架構可讓元件在其中彼此互相利用，而且資料也可以在不同的元件之間進行資料流處理。 例如，類似 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 的資料存放區可透過 <xref:System.Xml.Xsl.XslCompiledTransform> 類別進行轉換，接著輸出可以資料流方式傳輸至另一個存放區，或當做 Web 服務的資料流傳回。  
  
- **效能。** 為了提高應用程式效能，.NET Framework 中的某些 XML 類別可支援資料流形式的模型，並擁有下列特性：  
  
    - 順向的最小快取、提取模型剖析 (<xref:System.Xml.XmlReader>)。  
  
    - 順向驗證 (<xref:System.Xml.XmlReader>)。  
  
    - 資料指標樣式導覽，可將節點的建立最小化為單一虛擬節點，同時提供文件的隨機存取 (<xref:System.Xml.XPath.XPathNavigator>)。  
  
     為了要在每次需要 XSLT 處理時都提高效能，您可以使用 <xref:System.Xml.XPath.XPathDocument> 類別，它是最佳化的唯讀 XPath 查詢存放區，其設計目的是要與 <xref:System.Xml.Xsl.XslCompiledTransform> 類別有效率地一起運作。  
  
- **與 ADO.NET 整合。** XML 類別與 [ADO.NET](../../../../docs/framework/data/adonet/index.md) 緊密整合在一起，可讓關聯式資料和 XML 結合在一起。 <xref:System.Data.DataSet> 類別是一項擷取自資料庫的記憶體中資料快取。 <xref:System.Data.DataSet> 類別可使用 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 類別來讀取及寫入 XML，將其內部的關聯式結構描述結構保存為 XML 結構描述 (XSD)，還可以推斷 XML 文件的結構描述結構。  
  
## <a name="in-this-section"></a>本節內容  
 [XML 處理選項](../../../../docs/standard/data/xml/xml-processing-options.md)  
 討論用來處理 XML 資料的選項。  
  
 [處理記憶體中的 XML 資料](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 討論用來處理記憶體內 XML 資料的三個模型：[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) 和 [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)、<xref:System.Xml.XmlDocument> 類別 (根據 W3C 文件物件模型) 和 <xref:System.Xml.XPath.XPathDocument> 類別 (根據 XPath 資料模型)。  
  
 [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)  
 說明如何使用 XSLT 處理器。  
  
 [XML 結構描述物件模型 (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 說明藉由提供 <xref:System.Xml.Schema.XmlSchema> 類別來載入和編輯結構描述，用以建置及管理 XML 結構描述 (XSD) 的類別。  
  
 [XML 與關聯式資料和 ADO.NET 互相整合](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 說明 .NET Framework 如何透過 <xref:System.Data.DataSet> 物件和 <xref:System.Xml.XmlDataDocument> 物件，啟用即時、同步方式來存取關聯式及階層式表示的資料。  
  
 [管理 XML 文件中的命名空間](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 說明 <xref:System.Xml.XmlNamespaceManager> 類別如何用來儲存及維護命名空間資訊。  
  
 [System.Xml 類別中的類型支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 說明 XML 資料類型如何對應到 CLR 類型、如何轉換 XML 資料類型，以及 <xref:System.Xml> 類別中的其他類型支援功能。  
  
## <a name="related-sections"></a>相關章節  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 提供如何使用 ADO.NET 來存取資料的相關資訊。  
  
 [安全性](../../../../docs/standard/security/index.md)  
 提供 .NET Framework 安全性系統的概觀。  
