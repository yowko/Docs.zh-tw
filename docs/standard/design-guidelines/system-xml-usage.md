---
title: "System.Xml 使用方式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 956cc0ba37c06b39ed32500209e1af47d4035c84
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="systemxml-usage"></a><span data-ttu-id="714f3-102">System.Xml 使用方式</span><span class="sxs-lookup"><span data-stu-id="714f3-102">System.Xml Usage</span></span>
<span data-ttu-id="714f3-103">本節討論中的幾種類型的使用方式的相關<xref:System.Xml?displayProperty=nameWithType>無法用來代表 XML 資料的命名空間。</span><span class="sxs-lookup"><span data-stu-id="714f3-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="714f3-104">**X 不**使用<xref:System.Xml.XmlNode>或<xref:System.Xml.XmlDocument>來表示 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="714f3-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="714f3-105">使用的執行個體非<xref:System.Xml.XPath.IXPathNavigable>， <xref:System.Xml.XmlReader>， <xref:System.Xml.XmlWriter>，或是子類型的<xref:System.Xml.Linq.XNode>改為。</span><span class="sxs-lookup"><span data-stu-id="714f3-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="714f3-106">`XmlNode`和`XmlDocument`不專為公開在公用 Api。</span><span class="sxs-lookup"><span data-stu-id="714f3-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="714f3-107">**✓ 不要**使用`XmlReader`， `IXPathNavigable`，或是子類型的`XNode`做為輸入或輸出的接受或傳回 XML 的成員。</span><span class="sxs-lookup"><span data-stu-id="714f3-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="714f3-108">使用這些抽象概念，而不是`XmlDocument`， `XmlNode`，或<xref:System.Xml.XPath.XPathDocument>，因為這可分隔從記憶體中 XML 文件的特定實作的方法，並讓他們使用的虛擬公開 （expose） 的 XML 資料來源`XNode``XmlReader`，或<xref:System.Xml.XPath.XPathNavigator>。</span><span class="sxs-lookup"><span data-stu-id="714f3-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="714f3-109">**X 不**子類別`XmlDocument`如果您想要建立代表基礎物件模型或資料來源的 XML 檢視表的型別。</span><span class="sxs-lookup"><span data-stu-id="714f3-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="714f3-110">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="714f3-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="714f3-111">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="714f3-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714f3-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="714f3-112">See Also</span></span>  
 [<span data-ttu-id="714f3-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="714f3-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="714f3-114">用法方針</span><span class="sxs-lookup"><span data-stu-id="714f3-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
