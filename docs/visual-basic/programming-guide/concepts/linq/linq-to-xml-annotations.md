---
title: "LINQ to XML Annotations2 |Microsoft 文件"
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
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 97f5386630ba687e4401ee0cfb70f7170e273a53
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="df3d7-102">LINQ to XML 註釋</span><span class="sxs-lookup"><span data-stu-id="df3d7-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="df3d7-103">中的註解[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]可讓您將任何任意型別的任何任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="df3d7-103">Annotations in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="df3d7-104">若要將註解加入到 XML 元件，例如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>，您呼叫<xref:System.Xml.Linq.XObject.AddAnnotation%2A>方法。</xref:System.Xml.Linq.XObject.AddAnnotation%2A> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df3d7-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="df3d7-105">您可以按照型別擷取附註。</span><span class="sxs-lookup"><span data-stu-id="df3d7-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="df3d7-106">請注意，這些附註不是 XML 資訊集的一部分；它們無法進行序列化或還原序列化。</span><span class="sxs-lookup"><span data-stu-id="df3d7-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df3d7-107">方法</span><span class="sxs-lookup"><span data-stu-id="df3d7-107">Methods</span></span>  
 <span data-ttu-id="df3d7-108">使用附註時，您可以使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="df3d7-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="df3d7-109">方法</span><span class="sxs-lookup"><span data-stu-id="df3d7-109">Method</span></span>|<span data-ttu-id="df3d7-110">描述</span><span class="sxs-lookup"><span data-stu-id="df3d7-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="df3d7-111"><xref:System.Xml.Linq.XObject.AddAnnotation%2A></xref:System.Xml.Linq.XObject.AddAnnotation%2A></span><span class="sxs-lookup"><span data-stu-id="df3d7-111"><xref:System.Xml.Linq.XObject.AddAnnotation%2A></span></span>|<span data-ttu-id="df3d7-112">將物件加入至<xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>註解清單</span><span class="sxs-lookup"><span data-stu-id="df3d7-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="df3d7-113"><xref:System.Xml.Linq.XObject.Annotation%2A></xref:System.Xml.Linq.XObject.Annotation%2A></span><span class="sxs-lookup"><span data-stu-id="df3d7-113"><xref:System.Xml.Linq.XObject.Annotation%2A></span></span>|<span data-ttu-id="df3d7-114">取得指定之型別的第一個附註物件從<xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="df3d7-114">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="df3d7-115"><xref:System.Xml.Linq.XObject.Annotations%2A></xref:System.Xml.Linq.XObject.Annotations%2A></span><span class="sxs-lookup"><span data-stu-id="df3d7-115"><xref:System.Xml.Linq.XObject.Annotations%2A></span></span>|<span data-ttu-id="df3d7-116">取得指定之型別的附註集合<xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="df3d7-116">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="df3d7-117"><xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></span><span class="sxs-lookup"><span data-stu-id="df3d7-117"><xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></span></span>|<span data-ttu-id="df3d7-118">從<xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>移除指定之型別的附註</span><span class="sxs-lookup"><span data-stu-id="df3d7-118">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df3d7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df3d7-119">See Also</span></span>  
 [<span data-ttu-id="df3d7-120">進階的 LINQ to XML 程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df3d7-120">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
