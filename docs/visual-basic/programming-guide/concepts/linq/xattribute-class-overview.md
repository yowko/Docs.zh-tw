---
title: XAttribute 類別概觀 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 6b24f429a69067f6af1a61efe4102a5638db3031
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836112"
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="9ac75-102">XAttribute 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ac75-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="9ac75-103">屬性是與項目相關聯的成對名稱/值。</span><span class="sxs-lookup"><span data-stu-id="9ac75-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="9ac75-104"><xref:System.Xml.Linq.XAttribute> 類別表示 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="9ac75-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="9ac75-105">總覽</span><span class="sxs-lookup"><span data-stu-id="9ac75-105">Overview</span></span>  
 <span data-ttu-id="9ac75-106">在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中使用屬性的方式類似於使用項目。</span><span class="sxs-lookup"><span data-stu-id="9ac75-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="9ac75-107">其建構函式類似。</span><span class="sxs-lookup"><span data-stu-id="9ac75-107">Their constructors are similar.</span></span> <span data-ttu-id="9ac75-108">您用來擷取其集合的方法也類似。</span><span class="sxs-lookup"><span data-stu-id="9ac75-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="9ac75-109">屬性集合的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式看起來非常類似項目集合的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="9ac75-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="9ac75-110">系統會保留將屬性加入到項目的順序。</span><span class="sxs-lookup"><span data-stu-id="9ac75-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="9ac75-111">也就是說，當您逐一查看屬性時，您會看到加入這些屬性的相同順序。</span><span class="sxs-lookup"><span data-stu-id="9ac75-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="9ac75-112">XAttribute 建構函式</span><span class="sxs-lookup"><span data-stu-id="9ac75-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="9ac75-113">下列 <xref:System.Xml.Linq.XAttribute> 類別的建構函式就是您常用的建構函式：</span><span class="sxs-lookup"><span data-stu-id="9ac75-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="9ac75-114">建構函式</span><span class="sxs-lookup"><span data-stu-id="9ac75-114">Constructor</span></span>|<span data-ttu-id="9ac75-115">描述</span><span class="sxs-lookup"><span data-stu-id="9ac75-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="9ac75-116">建立 <xref:System.Xml.Linq.XAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="9ac75-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="9ac75-117">`name` 引數會指定屬性的名稱；`content` 會指定屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="9ac75-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="9ac75-118">建立具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="9ac75-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="9ac75-119">下列程式碼會顯示此項目包含在 Visual Basic 中使用 XML 常值的屬性：</span><span class="sxs-lookup"><span data-stu-id="9ac75-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="9ac75-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9ac75-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="9ac75-121">屬性的功能結構</span><span class="sxs-lookup"><span data-stu-id="9ac75-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="9ac75-122">您無法建構內嵌 <xref:System.Xml.Linq.XAttribute> 物件之結構的 <xref:System.Xml.Linq.XElement> 物件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9ac75-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 <span data-ttu-id="9ac75-123">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9ac75-123">This example produces the following output:</span></span>  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="9ac75-124">屬性不是節點</span><span class="sxs-lookup"><span data-stu-id="9ac75-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="9ac75-125">屬性和項目有一些差異。</span><span class="sxs-lookup"><span data-stu-id="9ac75-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="9ac75-126"><xref:System.Xml.Linq.XAttribute> 物件在 XML 樹狀結構中不是節點。</span><span class="sxs-lookup"><span data-stu-id="9ac75-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="9ac75-127">它們是與 XML 項目相關聯的成對名稱/值。</span><span class="sxs-lookup"><span data-stu-id="9ac75-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="9ac75-128">相較於文件物件模型 (DOM)，這在反映 XML 的結構時，更為接近。</span><span class="sxs-lookup"><span data-stu-id="9ac75-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="9ac75-129">雖然 <xref:System.Xml.Linq.XAttribute> 物件實際上在 XML 樹狀結構中不是節點，但是使用 <xref:System.Xml.Linq.XAttribute> 物件的方式與使用 <xref:System.Xml.Linq.XElement> 物件的方式非常類似。</span><span class="sxs-lookup"><span data-stu-id="9ac75-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="9ac75-130">這個區別只有對於撰寫可在節點層級使用 XML 樹狀結構之程式碼的開發人員特別重要。</span><span class="sxs-lookup"><span data-stu-id="9ac75-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="9ac75-131">這個區別與許多開發人員都無關。</span><span class="sxs-lookup"><span data-stu-id="9ac75-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac75-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ac75-132">See also</span></span>

- [<span data-ttu-id="9ac75-133">LINQ to XML 程式設計概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ac75-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
