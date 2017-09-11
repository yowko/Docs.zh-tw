---
title: "如何︰ 資料流處理 XML 片段，從 XmlReader (Visual Basic) |Microsoft 文件"
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
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c9c60bb4730ef6569390f76f63c40a2cbd1c9524
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="00d01-102">如何︰ 資料流處理 XML 片段，從 XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00d01-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="00d01-103">當您必須處理大型 XML 檔案時，可能無法將整個 XML 樹狀載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="00d01-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="00d01-104">本主題示範如何串流片段使用<xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="00d01-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="00d01-105">其中一種最有效的方式使用<xref:System.Xml.XmlReader>讀取<xref:System.Xml.Linq.XElement>物件為撰寫您自己的自訂座標軸方法。</xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="00d01-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="00d01-106">座標軸方法通常會傳回集合例如<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>，如本主題中範例所示。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="00d01-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="00d01-107">在自訂座標軸方法呼叫來建立 XML 片段後<xref:System.Xml.Linq.XNode.ReadFrom%2A>方法，傳回集合使用`yield return`。</xref:System.Xml.Linq.XNode.ReadFrom%2A></span><span class="sxs-lookup"><span data-stu-id="00d01-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="00d01-108">這會將延後執行語意 (Semantics) 提供給您自訂的座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="00d01-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="00d01-109">當您建立 XML 樹狀結構從<xref:System.Xml.XmlReader>物件，<xref:System.Xml.XmlReader>必須置於項目。</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="00d01-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="00d01-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A>方法不會傳回讀取項目的關閉標記前。</xref:System.Xml.Linq.XNode.ReadFrom%2A></span><span class="sxs-lookup"><span data-stu-id="00d01-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="00d01-111">如果您想要建立部分樹狀結構，您可以執行個體化<xref:System.Xml.XmlReader>，將讀取器定位在您想要轉換成節點<xref:System.Xml.Linq.XElement>樹狀結構，然後再建立<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="00d01-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="00d01-112">本主題[How to︰ 資料流 XML 片段並存取標頭資訊 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)包含資訊和範例如何串流更複雜的文件。</span><span class="sxs-lookup"><span data-stu-id="00d01-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="00d01-113">本主題[How to︰ 執行串流轉換的大型 XML 文件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md)包含使用 LINQ to XML 轉換非常大的 XML 文件，同時維護小的記憶體使用量的範例。</span><span class="sxs-lookup"><span data-stu-id="00d01-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00d01-114">範例</span><span class="sxs-lookup"><span data-stu-id="00d01-114">Example</span></span>  
 <span data-ttu-id="00d01-115">這個範例會建立自訂座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="00d01-115">This example creates a custom axis method.</span></span> <span data-ttu-id="00d01-116">您可以使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢進行查詢。</span><span class="sxs-lookup"><span data-stu-id="00d01-116">You can query it by using a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query.</span></span> <span data-ttu-id="00d01-117">自訂座標軸方法  `StreamRootChildDoc` 是一種方法，特別針對讀取具有重複 `Child` 項目的文件而設計。</span><span class="sxs-lookup"><span data-stu-id="00d01-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
<span data-ttu-id="00d01-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="00d01-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="00d01-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="00d01-119">This example produces the following output:</span></span>  
  
<span data-ttu-id="00d01-120"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="00d01-120"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="00d01-121">在此範例中，來源文件很小。</span><span class="sxs-lookup"><span data-stu-id="00d01-121">In this example, the source document is very small.</span></span> <span data-ttu-id="00d01-122">但是，即使有數百萬的 `Child` 元素，此範例的記憶體使用量還是很小。</span><span class="sxs-lookup"><span data-stu-id="00d01-122">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d01-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00d01-123">See Also</span></span>  
 <span data-ttu-id="00d01-124">[逐步解說︰ 在 Visual Basic 中實作 IEnumerable(Of T)](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md) </span><span class="sxs-lookup"><span data-stu-id="00d01-124">[Walkthrough: Implementing IEnumerable(Of T) in Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md) </span></span>  
<span data-ttu-id="00d01-125"> [剖析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)</span><span class="sxs-lookup"><span data-stu-id="00d01-125"> [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)</span></span>
