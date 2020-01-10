---
title: System.Xml 使用方式
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: c57f5451526094d58066d7d391f41795f17732de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709032"
---
# <a name="systemxml-usage"></a><span data-ttu-id="b1a7c-102">System.Xml 使用方式</span><span class="sxs-lookup"><span data-stu-id="b1a7c-102">System.Xml Usage</span></span>
<span data-ttu-id="b1a7c-103">本節將討論如何在可用來代表 XML 資料的 <xref:System.Xml?displayProperty=nameWithType> 命名空間中使用數種類型。</span><span class="sxs-lookup"><span data-stu-id="b1a7c-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="b1a7c-104">**X 不會**使用 <xref:System.Xml.XmlNode> 或 <xref:System.Xml.XmlDocument> 來代表 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="b1a7c-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="b1a7c-105">請改用 <xref:System.Xml.Linq.XNode> 的 <xref:System.Xml.XPath.IXPathNavigable>、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>或子類型的實例。</span><span class="sxs-lookup"><span data-stu-id="b1a7c-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="b1a7c-106">`XmlNode` 和 `XmlDocument` 不是為了公開公用 Api 而設計的。</span><span class="sxs-lookup"><span data-stu-id="b1a7c-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="b1a7c-107">**✓**會使用 `XNode` 的 `XmlReader`、`IXPathNavigable`或子類型，做為接受或傳回 XML 之成員的輸入或輸出。</span><span class="sxs-lookup"><span data-stu-id="b1a7c-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="b1a7c-108">使用這些抽象概念，而不是 `XmlDocument`、`XmlNode`或 <xref:System.Xml.XPath.XPathDocument>，因為這會將方法與記憶體中 XML 檔的特定執行分離，讓它們能夠使用公開 `XNode`、`XmlReader`或 <xref:System.Xml.XPath.XPathNavigator>的虛擬 XML 資料來源。</span><span class="sxs-lookup"><span data-stu-id="b1a7c-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="b1a7c-109">如果您想要建立代表基礎物件模型或資料來源之 XML 視圖的類型， **X 不會**將 `XmlDocument` 子類別化。</span><span class="sxs-lookup"><span data-stu-id="b1a7c-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="b1a7c-110">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="b1a7c-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b1a7c-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="b1a7c-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a7c-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1a7c-112">See also</span></span>

- [<span data-ttu-id="b1a7c-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="b1a7c-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="b1a7c-114">用法方針</span><span class="sxs-lookup"><span data-stu-id="b1a7c-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
