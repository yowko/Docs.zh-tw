---
title: System.Xml 使用方式
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: KrzysztofCwalina
ms.openlocfilehash: fc94ac62d1f2413c5f51446a8f6d0a52d9151557
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650124"
---
# <a name="systemxml-usage"></a>System.Xml 使用方式
本節說明中的數種類型的使用方式<xref:System.Xml?displayProperty=nameWithType>可用來代表 XML 資料的命名空間。  
  
 **X DO NOT** 使用 <xref:System.Xml.XmlNode> 或 <xref:System.Xml.XmlDocument> 來表示 XML 資料。 使用的執行個體優先<xref:System.Xml.XPath.IXPathNavigable>， <xref:System.Xml.XmlReader>， <xref:System.Xml.XmlWriter>，或是子類型的<xref:System.Xml.Linq.XNode>改。 `XmlNode` 和`XmlDocument`並未設計成在公用 Api 中公開。  
  
 **✓ DO** 使用 `XmlReader`， `IXPathNavigable`，或是子類型的 `XNode` 做為輸入或輸出的接受或傳回 XML 的成員。  
  
 使用而不是這些抽象概`XmlDocument`， `XmlNode`，或<xref:System.Xml.XPath.XPathDocument>，因為這以減少記憶體中 XML 文件的特定實作的方法，並讓他們使用的虛擬公開 （expose） 的 XML 資料來源`XNode``XmlReader`，或<xref:System.Xml.XPath.XPathNavigator>。  
  
 **X DO NOT** 子類別 `XmlDocument` 如果您想要建立代表基礎物件模型或資料來源的 XML 檢視表的型別。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
