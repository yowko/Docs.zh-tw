---
title: "序列化至 File、TextWriter 和 XmlWriter1 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f61324395e81509e5800e99b654a8c669d4397f0
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="cadd9-102">序列化至 File、TextWriter 和 XmlWriter</span><span class="sxs-lookup"><span data-stu-id="cadd9-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="cadd9-103">您可以將 XML 樹狀結構序列化到 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="cadd9-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="cadd9-104">您可以使用 `ToString` 方法，將任何 XML 元件 (包括 <xref:System.Xml.Linq.XDocument> 和 <xref:System.Xml.Linq.XElement>) 序列化到字串。</span><span class="sxs-lookup"><span data-stu-id="cadd9-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="cadd9-105">如果您要在序列化到字串時隱藏格式，則可以使用 <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> 方法。</span><span class="sxs-lookup"><span data-stu-id="cadd9-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="cadd9-106">序列化至檔案時的預設行為是格式化 (縮排) 所產生的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="cadd9-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="cadd9-107">當您縮排時，不會保留 XML 樹狀中的無效空白字元。</span><span class="sxs-lookup"><span data-stu-id="cadd9-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="cadd9-108">若要使用格式進行序列化，請使用下列未接受 <xref:System.Xml.Linq.SaveOptions> 作為引數之方法的其中一個多載：</span><span class="sxs-lookup"><span data-stu-id="cadd9-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <span data-ttu-id="cadd9-109"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cadd9-109"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="cadd9-110"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cadd9-110"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="cadd9-111">如果您想要選擇不縮排和不保留 XML 樹狀結構中的無效空間，請使用下列接受 <xref:System.Xml.Linq.SaveOptions> 作為引數之方法的其中一個多載：</span><span class="sxs-lookup"><span data-stu-id="cadd9-111">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <span data-ttu-id="cadd9-112"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cadd9-112"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="cadd9-113"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cadd9-113"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="cadd9-114">如需範例，請參閱適當的參考主題。</span><span class="sxs-lookup"><span data-stu-id="cadd9-114">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadd9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cadd9-115">See Also</span></span>  
 [<span data-ttu-id="cadd9-116">序列化 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="cadd9-116">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
