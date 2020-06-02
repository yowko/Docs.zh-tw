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
# <a name="systemxml-usage"></a><span data-ttu-id="a7b67-102">System.Xml 使用方式</span><span class="sxs-lookup"><span data-stu-id="a7b67-102">System.Xml Usage</span></span>
<span data-ttu-id="a7b67-103">本節將討論如何使用命名空間中的數種類型 <xref:System.Xml?displayProperty=nameWithType> ，這些型別可以用來代表 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="a7b67-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="a7b67-104">❌請勿使用 <xref:System.Xml.XmlNode> 或 <xref:System.Xml.XmlDocument> 來表示 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="a7b67-104">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="a7b67-105">請 <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlReader> 改用、、 <xref:System.Xml.XmlWriter> 或之子類型的實例 <xref:System.Xml.Linq.XNode> 。</span><span class="sxs-lookup"><span data-stu-id="a7b67-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="a7b67-106">`XmlNode`和 `XmlDocument` 並非設計來公開公用 api。</span><span class="sxs-lookup"><span data-stu-id="a7b67-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="a7b67-107">✔️請使用 `XmlReader` 、 `IXPathNavigable` 或的子類型，做 `XNode` 為接受或傳回 XML 之成員的輸入或輸出。</span><span class="sxs-lookup"><span data-stu-id="a7b67-107">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="a7b67-108">請使用這些抽象，而不是 `XmlDocument` 、 `XmlNode` 或 <xref:System.Xml.XPath.XPathDocument> ，因為這會將方法與記憶體中 XML 檔的特定執行分離，並允許它們使用公開、或的虛擬 XML 資料來源 `XNode` `XmlReader` <xref:System.Xml.XPath.XPathNavigator> 。</span><span class="sxs-lookup"><span data-stu-id="a7b67-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="a7b67-109">❌`XmlDocument`如果您想要建立代表基礎物件模型或資料來源之 XML 視圖的類型，請勿將子類別化。</span><span class="sxs-lookup"><span data-stu-id="a7b67-109">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="a7b67-110">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="a7b67-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a7b67-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="a7b67-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a7b67-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7b67-112">See also</span></span>

- [<span data-ttu-id="a7b67-113">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="a7b67-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="a7b67-114">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="a7b67-114">Usage Guidelines</span></span>](usage-guidelines.md)
