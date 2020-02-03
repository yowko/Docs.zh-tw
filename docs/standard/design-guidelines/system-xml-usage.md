---
title: System.Xml 使用方式
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 2ecb709684834a8280c841eb8eef4f024481f7a4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743578"
---
# <a name="systemxml-usage"></a>System.Xml 使用方式
本節將討論如何在可用來代表 XML 資料的 <xref:System.Xml?displayProperty=nameWithType> 命名空間中使用數種類型。

 ❌ 不使用 <xref:System.Xml.XmlNode> 或 <xref:System.Xml.XmlDocument> 來代表 XML 資料。 請改用 <xref:System.Xml.Linq.XNode> 的 <xref:System.Xml.XPath.IXPathNavigable>、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>或子類型的實例。 `XmlNode` 和 `XmlDocument` 不是為了公開公用 Api 而設計的。

 ✔️確實會使用 `XNode` 的 `XmlReader`、`IXPathNavigable`或子類型，做為接受或傳回 XML 之成員的輸入或輸出。

 使用這些抽象概念，而不是 `XmlDocument`、`XmlNode`或 <xref:System.Xml.XPath.XPathDocument>，因為這會將方法與記憶體中 XML 檔的特定執行分離，讓它們能夠使用公開 `XNode`、`XmlReader`或 <xref:System.Xml.XPath.XPathNavigator>的虛擬 XML 資料來源。

 如果您想要建立代表基礎物件模型或資料來源之 XML 視圖的類型，❌ 不會將 `XmlDocument` 子類別化。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*

## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
