---
title: 序列化至 Files、TextWriters 和 XmlWriters1
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 903e6f5b6a8cd88c140e6759136301a6305cee2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="cf5e8-102">序列化至 File、TextWriter 和 XmlWriter</span><span class="sxs-lookup"><span data-stu-id="cf5e8-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="cf5e8-103">您可以將 XML 樹狀結構序列化至 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="cf5e8-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="cf5e8-104">您可以使用 <xref:System.Xml.Linq.XDocument> 方法，將任何 XML 元件 (包括 <xref:System.Xml.Linq.XElement> 和 `ToString`) 序列化至字串。</span><span class="sxs-lookup"><span data-stu-id="cf5e8-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="cf5e8-105">如果您要在序列化至字串時隱藏格式，您可以使用 <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="cf5e8-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="cf5e8-106">序列化至檔案時的預設行為是格式化 (縮排) 所產生的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="cf5e8-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="cf5e8-107">當您縮排時，不會保留 XML 樹狀中的無效空白字元。</span><span class="sxs-lookup"><span data-stu-id="cf5e8-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="cf5e8-108">若要使用格式序列化，請使用下列沒有採用 <xref:System.Xml.Linq.SaveOptions> 當做引數之方法的其中一個多載：</span><span class="sxs-lookup"><span data-stu-id="cf5e8-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="cf5e8-109">如果您想要選擇不縮排和不保留 XML 樹狀結構中的無效空白字元，請使用下列採用 <xref:System.Xml.Linq.SaveOptions> 當做引數之方法的其中一個多載：</span><span class="sxs-lookup"><span data-stu-id="cf5e8-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="cf5e8-110">如需範例，請參閱適當的參考主題。</span><span class="sxs-lookup"><span data-stu-id="cf5e8-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf5e8-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf5e8-111">See Also</span></span>  
 [<span data-ttu-id="cf5e8-112">序列化 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="cf5e8-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
