---
title: "LINQ to XML 註釋3 | Microsoft Docs"
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
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 13718f509eee46853020cfe1dd27ee85437d2e6d
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="665b5-102">LINQ to XML 註釋</span><span class="sxs-lookup"><span data-stu-id="665b5-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="665b5-103">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中的註釋可讓您將任意型別的任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="665b5-103">Annotations in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="665b5-104">若要將註釋新增至 XML 元件 (例如 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>)，您可以呼叫 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="665b5-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="665b5-105">您可以按照型別擷取附註。</span><span class="sxs-lookup"><span data-stu-id="665b5-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="665b5-106">請注意，這些附註不是 XML 資訊集的一部分；它們無法進行序列化或還原序列化。</span><span class="sxs-lookup"><span data-stu-id="665b5-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="665b5-107">方法</span><span class="sxs-lookup"><span data-stu-id="665b5-107">Methods</span></span>  
 <span data-ttu-id="665b5-108">使用附註時，您可以使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="665b5-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="665b5-109">方法</span><span class="sxs-lookup"><span data-stu-id="665b5-109">Method</span></span>|<span data-ttu-id="665b5-110">描述</span><span class="sxs-lookup"><span data-stu-id="665b5-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="665b5-111"><xref:System.Xml.Linq.XObject.AddAnnotation%2A></span><span class="sxs-lookup"><span data-stu-id="665b5-111"><xref:System.Xml.Linq.XObject.AddAnnotation%2A></span></span>|<span data-ttu-id="665b5-112">將物件新增至 <xref:System.Xml.Linq.XObject> 註釋清單。</span><span class="sxs-lookup"><span data-stu-id="665b5-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="665b5-113"><xref:System.Xml.Linq.XObject.Annotation%2A></span><span class="sxs-lookup"><span data-stu-id="665b5-113"><xref:System.Xml.Linq.XObject.Annotation%2A></span></span>|<span data-ttu-id="665b5-114">從 <xref:System.Xml.Linq.XObject> 取得指定型別的第一個註釋物件。</span><span class="sxs-lookup"><span data-stu-id="665b5-114">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="665b5-115"><xref:System.Xml.Linq.XObject.Annotations%2A></span><span class="sxs-lookup"><span data-stu-id="665b5-115"><xref:System.Xml.Linq.XObject.Annotations%2A></span></span>|<span data-ttu-id="665b5-116">為 <xref:System.Xml.Linq.XObject> 取得指定型別的註釋集合。</span><span class="sxs-lookup"><span data-stu-id="665b5-116">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="665b5-117"><xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></span><span class="sxs-lookup"><span data-stu-id="665b5-117"><xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></span></span>|<span data-ttu-id="665b5-118">從 <xref:System.Xml.Linq.XObject> 移除指定型別的註釋。</span><span class="sxs-lookup"><span data-stu-id="665b5-118">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="665b5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="665b5-119">See Also</span></span>  
 [<span data-ttu-id="665b5-120">進階 LINQ to XML 程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="665b5-120">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
