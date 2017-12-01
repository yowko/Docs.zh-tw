---
title: "System.Xml 類別中的型別支援"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 14821ef78f20d1ff303afacb42415e4017a92742
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="type-support-in-the-systemxml-classes"></a>System.Xml 類別中的型別支援
在 .NET Framework 2.0 版中，核心 XML 類別已增強為包括類型支援功能。 <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 及 <xref:System.Xml.XPath.XPathNavigator> 類別包含類型支援功能，包括在 XML 結構描述類型與 Common Language Runtime (CLR) 類型之間轉換的能力。  
  
 在 .NET Framework 2.0 版中，<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 及 <xref:System.Xml.XPath.XPathNavigator> 類別已增強為包括類型支援功能。  
  
-   <xref:System.Xml.XmlReader>和<xref:System.Xml.XPath.XPathNavigator>類別都包含**SchemaInfo**傳回的結構描述資訊的節點的屬性。  
  
-   **ReadContentAs**和**ReadElementContentAs**和方法上的<xref:System.Xml.XmlReader>類別讀取文字值，並將它轉換成 CLR 值的單一方法呼叫。  
  
-   <xref:System.Xml.XmlWriter.WriteValue%2A> 類別上的 <xref:System.Xml.XmlWriter> 方法會在寫出 XML 時，將 CLR 類型轉換成 XML 結構描述類型。  
  
-   **ValueAs**和<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>屬性<xref:System.Xml.XPath.XPathNavigator>類別傳回的節點值，並將它轉換成 CLR 值的單一方法呼叫。  
  
> [!NOTE]
>  在 .NET Framework 1.0 版中，需要 <xref:System.Xml.XmlConvert> 類別以在 XML 結構描述與 CLR 類型之間進行轉換。  
  
## <a name="in-this-section"></a>本章節內容  
 [XML 資料類型對應至 CLR 型別](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 說明 XML 資料類型與 CLR 類型的預設對應。  
  
 [XML 型別支援實作注意事項](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 討論部分類型支援實作細節。  
  
 [XML 資料型別轉換](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 說明如何使用 <xref:System.Xml.XmlConvert> 類別在 XML 結構描述與 CLR 類型之間進行轉換。  
  
## <a name="related-sections"></a>相關章節  
 [存取強型別使用 XPathNavigator XML 資料](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
