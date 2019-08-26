---
title: System.Xml 類別中的型別支援
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 954ff12ae1ac8b4d601c35fcd76ea35b2bb3acbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939443"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="06cb5-102">System.Xml 類別中的型別支援</span><span class="sxs-lookup"><span data-stu-id="06cb5-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="06cb5-103">在 .NET Framework 2.0 版中，核心 XML 類別已增強為包括類型支援功能。</span><span class="sxs-lookup"><span data-stu-id="06cb5-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="06cb5-104"><xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 及 <xref:System.Xml.XPath.XPathNavigator> 類別包含類型支援功能，包括在 XML 結構描述類型與 Common Language Runtime (CLR) 類型之間轉換的能力。</span><span class="sxs-lookup"><span data-stu-id="06cb5-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="06cb5-105">在 .NET Framework 2.0 版中，<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 及 <xref:System.Xml.XPath.XPathNavigator> 類別已增強為包括類型支援功能。</span><span class="sxs-lookup"><span data-stu-id="06cb5-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="06cb5-106">每個 <xref:System.Xml.XmlReader> 及 <xref:System.Xml.XPath.XPathNavigator> 類別都包含 **SchemaInfo** 屬性，可傳回節點的結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="06cb5-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="06cb5-107">**ReadContentAs**、**ReadElementContentAs** 及 <xref:System.Xml.XmlReader> 類別上的方法，會在單一方法呼叫中讀取文字值，並將其轉換成 CLR 值。</span><span class="sxs-lookup"><span data-stu-id="06cb5-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="06cb5-108"><xref:System.Xml.XmlWriter.WriteValue%2A> 類別上的 <xref:System.Xml.XmlWriter> 方法會在寫出 XML 時，將 CLR 類型轉換成 XML 結構描述類型。</span><span class="sxs-lookup"><span data-stu-id="06cb5-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="06cb5-109"><xref:System.Xml.XPath.XPathNavigator> 類別上的 **ValueAs** 及 <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> 屬性會在單一方法呼叫中傳回節點值，並將其轉換成 CLR 值。</span><span class="sxs-lookup"><span data-stu-id="06cb5-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06cb5-110">在 .NET Framework 1.0 版中，需要 <xref:System.Xml.XmlConvert> 類別以在 XML 結構描述與 CLR 類型之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="06cb5-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06cb5-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="06cb5-111">In This Section</span></span>  
 [<span data-ttu-id="06cb5-112">將 XML 資料類型對應至 CLR 類型</span><span class="sxs-lookup"><span data-stu-id="06cb5-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="06cb5-113">說明 XML 資料類型與 CLR 類型的預設對應。</span><span class="sxs-lookup"><span data-stu-id="06cb5-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="06cb5-114">XML 類型支援實作注意事項</span><span class="sxs-lookup"><span data-stu-id="06cb5-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="06cb5-115">討論部分類型支援實作細節。</span><span class="sxs-lookup"><span data-stu-id="06cb5-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="06cb5-116">XML 資料類型轉換</span><span class="sxs-lookup"><span data-stu-id="06cb5-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="06cb5-117">說明如何使用 <xref:System.Xml.XmlConvert> 類別在 XML 結構描述與 CLR 類型之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="06cb5-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="06cb5-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="06cb5-118">Related Sections</span></span>  
 [<span data-ttu-id="06cb5-119">使用 XPathNavigator 存取強型別 XML 資料</span><span class="sxs-lookup"><span data-stu-id="06cb5-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
