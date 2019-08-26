---
title: XslTransform 的 XmlDataDocument 輸入
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5c2fb203a1a6975d2b30e47528b15a9005a2583
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916014"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>XslTransform 的 XmlDataDocument 輸入
> [!NOTE]
> 在 .NET Framework 2.0 中，<xref:System.Xml.Xsl.XslTransform> 類別已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。 如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。  
  
 Microsoft .NET Framework 實作 XML 文件物件模型 (DOM)，以提供 XML 文件中資料的存取權，以及其他可用來在 XML 文件中讀取、寫入和巡覽的類別。 <xref:System.Xml.XmlDataDocument> 位於 <xref:System.Xml> 命名空間中，可透過與 <xref:System.Data.DataSet> 中之關聯式資料的同步處理，而提供資料的關聯式存取權。 您可以透過 <xref:System.Data.DataSet> 的關聯式表示法同時檢視及管理結構化 XML，或透過 <xref:System.Xml.XmlDataDocument> 的 DOM 表示法來管理半結構化的 XML。 <xref:System.Xml.XmlDataDocument> 因此能夠跨越 XML 與關聯式領域的界限。  
  
 若資料儲存在關聯式結構中，而您想將它輸入 XSLT 轉換中，您可以將關聯式資料載入 <xref:System.Data.DataSet> 中，並使其與 <xref:System.Xml.XmlDataDocument> 產生關聯。 對 <xref:System.Xml.XPath.XPathNavigator> 的輸入 <xref:System.Xml.Xsl.XslTransform> 會透過 <xref:System.Xml.XmlDataDocument> 介面在 <xref:System.Xml.XPath.IXPathNavigable> 上實作。 採用關聯式資料，並將它載入 <xref:System.Data.DataSet> 中，然後在 <xref:System.Xml.XmlDataDocument> 內進行同步處理，此時即可對關聯式資料執行 XSLT 轉換。  
  
 如需將轉換套用至關聯式資料的詳細資訊，請參閱[將 XSLT 轉換套用至 DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlDataDocument>
- [資料集和 XmlDataDocument 同步處理](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [使用 XslTransform 類別進行 XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform 類別實作 XSLT 處理器](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [轉換中的 XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [轉換中的 XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [XslTransform 的 XPathDocument 輸入](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [XslTransform 的 XmlDocument 輸入](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
