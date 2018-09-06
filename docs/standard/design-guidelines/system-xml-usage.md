---
title: System.Xml 使用方式
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c3eb01e1050bc78d2b31de19a8a728af92777e8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863383"
---
# <a name="systemxml-usage"></a>System.Xml 使用方式
本節說明中的數種類型的使用方式<xref:System.Xml?displayProperty=nameWithType>可用來代表 XML 資料的命名空間。  
  
 **X DO NOT** 使用 <xref:System.Xml.XmlNode> 或 <xref:System.Xml.XmlDocument> 來表示 XML 資料。 使用的執行個體優先<xref:System.Xml.XPath.IXPathNavigable>， <xref:System.Xml.XmlReader>， <xref:System.Xml.XmlWriter>，或是子類型的<xref:System.Xml.Linq.XNode>改。 `XmlNode` 和`XmlDocument`並未設計成在公用 Api 中公開。  
  
 **✓ DO** 使用 `XmlReader`， `IXPathNavigable`，或是子類型的 `XNode` 做為輸入或輸出的接受或傳回 XML 的成員。  
  
 使用而不是這些抽象概`XmlDocument`， `XmlNode`，或<xref:System.Xml.XPath.XPathDocument>，因為這以減少記憶體中 XML 文件的特定實作的方法，並讓他們使用的虛擬公開 （expose） 的 XML 資料來源`XNode``XmlReader`，或<xref:System.Xml.XPath.XPathNavigator>。  
  
 **X DO NOT** 子類別 `XmlDocument` 如果您想要建立代表基礎物件模型或資料來源的 XML 檢視表的型別。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
