---
title: 序列化為 files、Textwriter 和 Xmlwriter-LINQ to XML
description: 您可以將 XML 樹狀結構序列化至檔案、無型別的或 XmlWriter，也可以使用 ToString 方法將任何 XML 元件（包括 XDocument 和 System.xml.linq.xelement>）序列化為字串。
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20651c06a759d83934c4b035a42eac7c2700eb9f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552809"
---
# <a name="serialize-to-files-textwriters-and-xmlwriters-linq-to-xml"></a><span data-ttu-id="0232c-103">序列化為 files、Textwriter 和 Xmlwriter (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="0232c-103">Serialize to files, TextWriters, and XmlWriters (LINQ to XML)</span></span>

<span data-ttu-id="0232c-104">您可以將 XML 樹狀序列化至 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="0232c-104">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="0232c-105">您可以使用 <xref:System.Xml.Linq.XDocument> 方法，將任何 XML 元件 (包括 <xref:System.Xml.Linq.XElement> 和 `ToString`) 序列化至字串。</span><span class="sxs-lookup"><span data-stu-id="0232c-105">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="0232c-106">如果您要在序列化至字串時隱藏格式，您可以使用 <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="0232c-106">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0232c-107">序列化至檔案時的預設行為是格式化 (縮排) 所產生的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="0232c-107">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="0232c-108">當您縮排時，不會保留 XML 樹狀結構中的無意義空白字元。</span><span class="sxs-lookup"><span data-stu-id="0232c-108">When you indent, the insignificant white space in the XML tree isn't preserved.</span></span> <span data-ttu-id="0232c-109">若要使用格式進行序列化，請使用下列其中一個不是引數的方法多載 <xref:System.Xml.Linq.SaveOptions> ：</span><span class="sxs-lookup"><span data-stu-id="0232c-109">To serialize with formatting, use one of the overloads of the following methods that don't take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="0232c-110">如果您想要選擇不縮排和不保留 XML 樹狀結構中的無效空白字元，請使用下列採用 <xref:System.Xml.Linq.SaveOptions> 當做引數之方法的其中一個多載：</span><span class="sxs-lookup"><span data-stu-id="0232c-110">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="0232c-111">如需範例，請參閱適當的參考文章。</span><span class="sxs-lookup"><span data-stu-id="0232c-111">For examples, see the appropriate reference article.</span></span>
