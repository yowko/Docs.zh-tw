---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: a7b81b8c1856c11cb0c5e777f31986a330cf115f
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332918"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="03a1d-102">LINQ to XML 註釋</span><span class="sxs-lookup"><span data-stu-id="03a1d-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="03a1d-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的註釋可讓您將任意型別的任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="03a1d-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="03a1d-104">若要將附註加入到 XML 元件 (例如，<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>) 中，您可以呼叫 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="03a1d-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="03a1d-105">您可以按照型別擷取附註。</span><span class="sxs-lookup"><span data-stu-id="03a1d-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="03a1d-106">請注意，這些附註不是 XML 資訊集的一部分；它們無法進行序列化或還原序列化。</span><span class="sxs-lookup"><span data-stu-id="03a1d-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03a1d-107">方法</span><span class="sxs-lookup"><span data-stu-id="03a1d-107">Methods</span></span>  
 <span data-ttu-id="03a1d-108">使用附註時，您可以使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="03a1d-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="03a1d-109">方法</span><span class="sxs-lookup"><span data-stu-id="03a1d-109">Method</span></span>|<span data-ttu-id="03a1d-110">描述</span><span class="sxs-lookup"><span data-stu-id="03a1d-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="03a1d-111">將物件加入到 <xref:System.Xml.Linq.XObject> 的附註清單。</span><span class="sxs-lookup"><span data-stu-id="03a1d-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="03a1d-112">從 <xref:System.Xml.Linq.XObject> 取得指定之型別的第一個附註物件。</span><span class="sxs-lookup"><span data-stu-id="03a1d-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="03a1d-113">針對 <xref:System.Xml.Linq.XObject> 取得指定之型別的附註集合。</span><span class="sxs-lookup"><span data-stu-id="03a1d-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="03a1d-114">從 <xref:System.Xml.Linq.XObject> 移除指定之型別的附註。</span><span class="sxs-lookup"><span data-stu-id="03a1d-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03a1d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03a1d-115">See Also</span></span>  
 [<span data-ttu-id="03a1d-116">進階的 LINQ to XML 程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03a1d-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
