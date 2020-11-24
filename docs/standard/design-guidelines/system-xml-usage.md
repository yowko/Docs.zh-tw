---
title: System.Xml 使用方式
ms.date: 10/22/2008
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 46282afa6548c731b04c40d8de91a1fed997c57c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677566"
---
# <a name="systemxml-usage"></a>System.Xml 使用方式

本節說明如何使用多個型別，這些型別位於 <xref:System.Xml?displayProperty=nameWithType> 可用於表示 XML 資料的命名空間中。

 ❌ 請勿使用 <xref:System.Xml.XmlNode> 或 <xref:System.Xml.XmlDocument> 來表示 XML 資料。 改為使用 <xref:System.Xml.XPath.IXPathNavigable> 、 <xref:System.Xml.XmlReader> 、 <xref:System.Xml.XmlWriter> 或的子類型實例 <xref:System.Xml.Linq.XNode> 。 `XmlNode` 和 `XmlDocument` 不是設計來公開公用 api。

 ✔️將 `XmlReader` 、 `IXPathNavigable` 或子類型 `XNode` 作為接受或傳回 XML 之成員的輸入或輸出。

 請使用這些抽象概念，而不是 `XmlDocument` 、 `XmlNode` 或 <xref:System.Xml.XPath.XPathDocument> ，因為這會將方法與記憶體中 XML 檔的特定執行分離，讓它們能夠使用公開、或的虛擬 XML 資料來源 `XNode` `XmlReader` <xref:System.Xml.XPath.XPathNavigator> 。

 ❌`XmlDocument`如果您想要建立代表基礎物件模型或資料來源之 XML 視圖的型別，請不要子類別。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [使用指導方針](usage-guidelines.md)
