---
title: "序列化至檔案、 Textwriter 和 XmlWriters3 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f8f8672004b0704b00ff60e5b58256f664bcbd82
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="97556-102">序列化至 File、TextWriter 和 XmlWriter</span><span class="sxs-lookup"><span data-stu-id="97556-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="97556-103">您可以序列化到 XML 樹狀結構<xref:System.IO.File>、 <xref:System.IO.TextWriter>，或<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="97556-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="97556-104">您可以將序列化的任何 XML 元件，包括<xref:System.Xml.Linq.XDocument>和<xref:System.Xml.Linq.XElement>，使用字串`ToString`方法。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="97556-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="97556-105">如果您想要序列化為字串時隱藏格式，您可以使用<xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>方法。</xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="97556-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="97556-106">當序列化至檔案的 Thedefault 行為是格式化 （縮排） 所產生的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="97556-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="97556-107">當您縮排時，不會保留 XML 樹狀中的無效空白字元。</span><span class="sxs-lookup"><span data-stu-id="97556-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="97556-108">若要使用格式序列化，請使用未採用下列方法的多載<xref:System.Xml.Linq.SaveOptions>做為引數︰</xref:System.Xml.Linq.SaveOptions></span><span class="sxs-lookup"><span data-stu-id="97556-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <span data-ttu-id="97556-109"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="97556-109"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="97556-110"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="97556-110"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="97556-111">如果您想要選擇不縮排和不保留空白字元 XML 樹狀結構中，使用其中一個會採用下列方法的多載<xref:System.Xml.Linq.SaveOptions>做為引數︰</xref:System.Xml.Linq.SaveOptions></span><span class="sxs-lookup"><span data-stu-id="97556-111">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <span data-ttu-id="97556-112"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="97556-112"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="97556-113"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="97556-113"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="97556-114">如需範例，請參閱適當的參考主題。</span><span class="sxs-lookup"><span data-stu-id="97556-114">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97556-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97556-115">See Also</span></span>  
 [<span data-ttu-id="97556-116">序列化 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97556-116">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
