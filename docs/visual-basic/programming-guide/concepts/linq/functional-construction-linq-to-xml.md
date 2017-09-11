---
title: "功能建構 (LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
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
ms.openlocfilehash: b88b67aca337b893f9f276c8e4a6589b6946069b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="b97ff-102">功能建構 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b97ff-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="b97ff-103">提供強大的方式，來建立 XML 項目稱為*功能結構*。</span><span class="sxs-lookup"><span data-stu-id="b97ff-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="b97ff-104">功能結構是在單一陳述式中建立 XML 樹狀結構的能力。</span><span class="sxs-lookup"><span data-stu-id="b97ff-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="b97ff-105">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 程式介面有數種主要功能可以使用功能結構：</span><span class="sxs-lookup"><span data-stu-id="b97ff-105">There are several key features of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="b97ff-106"><xref:System.Xml.Linq.XElement>建構函式會採用各種引數的內容類型。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b97ff-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="b97ff-107">例如，您可以將另一個<xref:System.Xml.Linq.XElement>物件，其成為子項目。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b97ff-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="b97ff-108">您可以傳遞<xref:System.Xml.Linq.XAttribute>物件，就會變成項目的屬性。</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="b97ff-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="b97ff-109">或者，您可以傳遞轉換成字串的其他類物件型，然後變成項目的文字內容。</span><span class="sxs-lookup"><span data-stu-id="b97ff-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="b97ff-110"><xref:System.Xml.Linq.XElement>建構函式接受`params`型別的陣列<xref:System.Object>，因此您可以將任何數目的物件傳遞給建構函式。</xref:System.Object> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b97ff-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="b97ff-111">這可讓您建立包含複雜內容的項目。</span><span class="sxs-lookup"><span data-stu-id="b97ff-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="b97ff-112">如果物件實作<xref:System.Collections.Generic.IEnumerable%601>會列舉中物件的集合，集合中的所有項目加入。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="b97ff-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="b97ff-113">如果集合包含<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>物件，會個別加入集合中的每個項目。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b97ff-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="b97ff-114">這很重要，因為它可讓您的結果傳遞[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]建構函式的查詢。</span><span class="sxs-lookup"><span data-stu-id="b97ff-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="b97ff-115">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="b97ff-115">The following is an example:</span></span>  
  
 <span data-ttu-id="b97ff-116">這些功能可讓您撰寫程式碼使用 XML 常值，建立 XML 樹狀結構，也可以撰寫程式碼會使用結果[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢當您建立 XML 樹狀結構︰</span><span class="sxs-lookup"><span data-stu-id="b97ff-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries when you create an XML tree:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="b97ff-117">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b97ff-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b97ff-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b97ff-118">See Also</span></span>  
 [<span data-ttu-id="b97ff-119">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b97ff-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
