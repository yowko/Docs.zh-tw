---
title: System.Xml 使用方式
ms.date: 10/22/2008
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: a01799bd130de0222d4d66dee4955375c1a1911f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828591"
---
# <a name="systemxml-usage"></a><span data-ttu-id="ed3fa-102">System.Xml 使用方式</span><span class="sxs-lookup"><span data-stu-id="ed3fa-102">System.Xml Usage</span></span>
<span data-ttu-id="ed3fa-103">本節說明如何使用多個型別，這些型別位於 <xref:System.Xml?displayProperty=nameWithType> 可用於表示 XML 資料的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="ed3fa-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="ed3fa-104">❌ 請勿使用 <xref:System.Xml.XmlNode> 或 <xref:System.Xml.XmlDocument> 來表示 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="ed3fa-104">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="ed3fa-105">改為使用 <xref:System.Xml.XPath.IXPathNavigable> 、 <xref:System.Xml.XmlReader> 、 <xref:System.Xml.XmlWriter> 或的子類型實例 <xref:System.Xml.Linq.XNode> 。</span><span class="sxs-lookup"><span data-stu-id="ed3fa-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="ed3fa-106">`XmlNode` 和 `XmlDocument` 不是設計來公開公用 api。</span><span class="sxs-lookup"><span data-stu-id="ed3fa-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="ed3fa-107">✔️將 `XmlReader` 、 `IXPathNavigable` 或子類型 `XNode` 作為接受或傳回 XML 之成員的輸入或輸出。</span><span class="sxs-lookup"><span data-stu-id="ed3fa-107">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="ed3fa-108">請使用這些抽象概念，而不是 `XmlDocument` 、 `XmlNode` 或 <xref:System.Xml.XPath.XPathDocument> ，因為這會將方法與記憶體中 XML 檔的特定執行分離，讓它們能夠使用公開、或的虛擬 XML 資料來源 `XNode` `XmlReader` <xref:System.Xml.XPath.XPathNavigator> 。</span><span class="sxs-lookup"><span data-stu-id="ed3fa-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="ed3fa-109">❌`XmlDocument`如果您想要建立代表基礎物件模型或資料來源之 XML 視圖的型別，請不要子類別。</span><span class="sxs-lookup"><span data-stu-id="ed3fa-109">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="ed3fa-110">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="ed3fa-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ed3fa-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="ed3fa-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ed3fa-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed3fa-112">See also</span></span>

- [<span data-ttu-id="ed3fa-113">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="ed3fa-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="ed3fa-114">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="ed3fa-114">Usage Guidelines</span></span>](usage-guidelines.md)
