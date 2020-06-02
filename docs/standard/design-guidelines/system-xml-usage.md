---
title: System.Xml 使用方式
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 07828219f2e17be925d060fa3bb33a9209ecb62b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291665"
---
# <a name="systemxml-usage"></a>System.Xml 使用方式
本節將討論如何使用命名空間中的數種類型 <xref:System.Xml?displayProperty=nameWithType> ，這些型別可以用來代表 XML 資料。

 ❌請勿使用 <xref:System.Xml.XmlNode> 或 <xref:System.Xml.XmlDocument> 來表示 XML 資料。 請 <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlReader> 改用、、 <xref:System.Xml.XmlWriter> 或之子類型的實例 <xref:System.Xml.Linq.XNode> 。 `XmlNode`和 `XmlDocument` 並非設計來公開公用 api。

 ✔️請使用 `XmlReader` 、 `IXPathNavigable` 或的子類型，做 `XNode` 為接受或傳回 XML 之成員的輸入或輸出。

 請使用這些抽象，而不是 `XmlDocument` 、 `XmlNode` 或 <xref:System.Xml.XPath.XPathDocument> ，因為這會將方法與記憶體中 XML 檔的特定執行分離，並允許它們使用公開、或的虛擬 XML 資料來源 `XNode` `XmlReader` <xref:System.Xml.XPath.XPathNavigator> 。

 ❌`XmlDocument`如果您想要建立代表基礎物件模型或資料來源之 XML 視圖的類型，請勿將子類別化。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [使用指導方針](usage-guidelines.md)
