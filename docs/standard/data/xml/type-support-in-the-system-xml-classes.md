---
title: "System.Xml 類別中的型別支援"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 14821ef78f20d1ff303afacb42415e4017a92742
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="5c964-102">System.Xml 類別中的型別支援</span><span class="sxs-lookup"><span data-stu-id="5c964-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="5c964-103">在 .NET Framework 2.0 版中，核心 XML 類別已增強為包括類型支援功能。</span><span class="sxs-lookup"><span data-stu-id="5c964-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="5c964-104"><xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 及 <xref:System.Xml.XPath.XPathNavigator> 類別包含類型支援功能，包括在 XML 結構描述類型與 Common Language Runtime (CLR) 類型之間轉換的能力。</span><span class="sxs-lookup"><span data-stu-id="5c964-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="5c964-105">在 .NET Framework 2.0 版中，<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 及 <xref:System.Xml.XPath.XPathNavigator> 類別已增強為包括類型支援功能。</span><span class="sxs-lookup"><span data-stu-id="5c964-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
-   <span data-ttu-id="5c964-106"><xref:System.Xml.XmlReader>和<xref:System.Xml.XPath.XPathNavigator>類別都包含**SchemaInfo**傳回的結構描述資訊的節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="5c964-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
-   <span data-ttu-id="5c964-107">**ReadContentAs**和**ReadElementContentAs**和方法上的<xref:System.Xml.XmlReader>類別讀取文字值，並將它轉換成 CLR 值的單一方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="5c964-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
-   <span data-ttu-id="5c964-108"><xref:System.Xml.XmlWriter.WriteValue%2A> 類別上的 <xref:System.Xml.XmlWriter> 方法會在寫出 XML 時，將 CLR 類型轉換成 XML 結構描述類型。</span><span class="sxs-lookup"><span data-stu-id="5c964-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
-   <span data-ttu-id="5c964-109">**ValueAs**和<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>屬性<xref:System.Xml.XPath.XPathNavigator>類別傳回的節點值，並將它轉換成 CLR 值的單一方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="5c964-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c964-110">在 .NET Framework 1.0 版中，需要 <xref:System.Xml.XmlConvert> 類別以在 XML 結構描述與 CLR 類型之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="5c964-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c964-111">本章節內容</span><span class="sxs-lookup"><span data-stu-id="5c964-111">In This Section</span></span>  
 [<span data-ttu-id="5c964-112">XML 資料類型對應至 CLR 型別</span><span class="sxs-lookup"><span data-stu-id="5c964-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="5c964-113">說明 XML 資料類型與 CLR 類型的預設對應。</span><span class="sxs-lookup"><span data-stu-id="5c964-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="5c964-114">XML 型別支援實作注意事項</span><span class="sxs-lookup"><span data-stu-id="5c964-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="5c964-115">討論部分類型支援實作細節。</span><span class="sxs-lookup"><span data-stu-id="5c964-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="5c964-116">XML 資料型別轉換</span><span class="sxs-lookup"><span data-stu-id="5c964-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="5c964-117">說明如何使用 <xref:System.Xml.XmlConvert> 類別在 XML 結構描述與 CLR 類型之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="5c964-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5c964-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="5c964-118">Related Sections</span></span>  
 [<span data-ttu-id="5c964-119">存取強型別使用 XPathNavigator XML 資料</span><span class="sxs-lookup"><span data-stu-id="5c964-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
