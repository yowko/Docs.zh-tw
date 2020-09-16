---
title: 處理記憶體中的 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 0f64b53588e08520d38c05ec6060f9aef58bd7d6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556482"
---
# <a name="processing-xml-data-in-memory"></a>處理記憶體中的 XML 資料
Microsoft .NET Framework 包含三種處理 XML 資料的模型：<xref:System.Xml.XmlDocument> 類別、<xref:System.Xml.XPath.XPathDocument> 類別，以及 [LINQ to XML (C#)](../../linq/linq-xml-overview.md) 和 [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md)。  
  
 <xref:System.Xml.XmlDocument> 類別會實作 W3C 文件物件模型 (DOM) 層級 1 核心及核心 DOM 層級 2 建議事項。 DOM 是 XML 文件的記憶體中 (快取) 樹狀結構表示。 透過 <xref:System.Xml.XmlDocument> 及其相關類別，您可以建構 XML 文件、載入並存取資料、修改資料，以及儲存變更。  
  
 <xref:System.Xml.XPath.XPathDocument> 類別是唯讀的記憶體中資料存放區，以 XPath 資料模型為基礎。 <xref:System.Xml.XPath.XPathNavigator> 類別提供了數種可在唯讀 <xref:System.Xml.XPath.XPathDocument> 類別及 <xref:System.Xml.XmlDocument> 類別包含的 XML 文件中使用游標模型的編輯選項與巡覽功能。  
  
 [LINQ to XML](../../linq/linq-xml-overview.md) 是 .NET Framework 3.5 版中推出的模型，用來處理 XML 資料。 它是利用 [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md) 的記憶體內部模型。 LINQ 會擴充 C# 和 Visual Basic 的語言語法，以提供新的查詢功能。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 DOM 模型處理 XML 資料](process-xml-data-using-the-dom-model.md)  
 討論如何使用 <xref:System.Xml.XmlDocument> 及其相關類別來處理 XML 資料。  
  
 [使用 XPath 資料模型處理 XML 資料](process-xml-data-using-the-xpath-data-model.md)  
 討論如何使用 <xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDocument> 及 <xref:System.Xml.XPath.XPathNavigator> 類別來處理 XML 資料。  
  
 [使用 LINQ to XML 處理 XML 資料](process-xml-data-using-linq-to-xml.md)  
 提供 LINQ to XML 的簡短概觀，並提供 LINQ to XML 文件的連結。  
  
## <a name="related-sections"></a>相關章節  
 [XML 檔和資料](index.md)
