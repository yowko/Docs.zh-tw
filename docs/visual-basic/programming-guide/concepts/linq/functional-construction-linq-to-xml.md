---
title: 函數式建構 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: f677c0d0e204b5d12718701ab70b8a3c1bd3530c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977466"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="2ccab-102">函數式建構 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ccab-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="2ccab-103">提供一種強大的方式來建立 XML 元素，稱為「函數式建構」。</span><span class="sxs-lookup"><span data-stu-id="2ccab-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="2ccab-104">功能結構是在單一陳述式中建立 XML 樹狀結構的能力。</span><span class="sxs-lookup"><span data-stu-id="2ccab-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="2ccab-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 程式介面有數種主要功能可以使用功能結構：</span><span class="sxs-lookup"><span data-stu-id="2ccab-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="2ccab-106"><xref:System.Xml.Linq.XElement> 建構函式會針對內容採用各種引數類型。</span><span class="sxs-lookup"><span data-stu-id="2ccab-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="2ccab-107">例如，您可以傳遞變成子項目的其他 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="2ccab-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="2ccab-108">您可以傳遞變成項目屬性的 <xref:System.Xml.Linq.XAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="2ccab-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="2ccab-109">或者，您可以傳遞轉換成字串的其他類物件型，然後變成項目的文字內容。</span><span class="sxs-lookup"><span data-stu-id="2ccab-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="2ccab-110"><xref:System.Xml.Linq.XElement> 建構函式會採用 `params` 類型的 <xref:System.Object> 陣列，讓您可以將任何數目的物件傳遞到建構函式。</span><span class="sxs-lookup"><span data-stu-id="2ccab-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="2ccab-111">這可讓您建立包含複雜內容的項目。</span><span class="sxs-lookup"><span data-stu-id="2ccab-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="2ccab-112">如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="2ccab-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="2ccab-113">如果集合包含 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="2ccab-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="2ccab-114">這是非常重要的，因為這可讓您將 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢的結果傳遞到建構函式中。</span><span class="sxs-lookup"><span data-stu-id="2ccab-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="2ccab-115">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="2ccab-115">The following is an example:</span></span>  
  
 <span data-ttu-id="2ccab-116">這些功能可讓您撰寫程式碼使用 XML 常值，來建立 XML 樹狀結構，以及撰寫程式碼，會使用結果[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢當您建立 XML 樹狀結構：</span><span class="sxs-lookup"><span data-stu-id="2ccab-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="2ccab-117">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2ccab-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ccab-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ccab-118">See also</span></span>

- [<span data-ttu-id="2ccab-119">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ccab-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
