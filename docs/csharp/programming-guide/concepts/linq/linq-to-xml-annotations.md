---
title: "LINQ to XML 註釋"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eadbc55ac6188fa3634745bf8bb222f07675a308
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="3f94b-102">LINQ to XML 註釋</span><span class="sxs-lookup"><span data-stu-id="3f94b-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="3f94b-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的註釋可讓您將任意型別的任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="3f94b-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="3f94b-104">若要將附註加入到 XML 元件 (例如，<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>) 中，您可以呼叫 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3f94b-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="3f94b-105">您可以按照型別擷取附註。</span><span class="sxs-lookup"><span data-stu-id="3f94b-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="3f94b-106">請注意，這些附註不是 XML 資訊集的一部分；它們無法進行序列化或還原序列化。</span><span class="sxs-lookup"><span data-stu-id="3f94b-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f94b-107">方法</span><span class="sxs-lookup"><span data-stu-id="3f94b-107">Methods</span></span>  
 <span data-ttu-id="3f94b-108">使用附註時，您可以使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="3f94b-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="3f94b-109">方法</span><span class="sxs-lookup"><span data-stu-id="3f94b-109">Method</span></span>|<span data-ttu-id="3f94b-110">描述</span><span class="sxs-lookup"><span data-stu-id="3f94b-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="3f94b-111">將物件加入到 <xref:System.Xml.Linq.XObject> 的附註清單。</span><span class="sxs-lookup"><span data-stu-id="3f94b-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="3f94b-112">從 <xref:System.Xml.Linq.XObject> 取得指定之型別的第一個附註物件。</span><span class="sxs-lookup"><span data-stu-id="3f94b-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="3f94b-113">針對 <xref:System.Xml.Linq.XObject> 取得指定之型別的附註集合。</span><span class="sxs-lookup"><span data-stu-id="3f94b-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="3f94b-114">從 <xref:System.Xml.Linq.XObject> 移除指定之型別的附註。</span><span class="sxs-lookup"><span data-stu-id="3f94b-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f94b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f94b-115">See Also</span></span>  
 [<span data-ttu-id="3f94b-116">進階 LINQ to XML 程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="3f94b-116">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
