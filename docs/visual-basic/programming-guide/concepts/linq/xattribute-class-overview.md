---
title: XAttribute 類別概觀
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 5b165044b4bea83e1a0789e3dd00367ed27b43e8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413202"
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="34e42-102">System.xml.linq.xattribute> 類別總覽（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="34e42-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="34e42-103">屬性是與項目相關聯的成對名稱/值。</span><span class="sxs-lookup"><span data-stu-id="34e42-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="34e42-104"><xref:System.Xml.Linq.XAttribute> 類別表示 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="34e42-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="34e42-105">概觀</span><span class="sxs-lookup"><span data-stu-id="34e42-105">Overview</span></span>  
 <span data-ttu-id="34e42-106">在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中使用屬性的方式類似於使用項目。</span><span class="sxs-lookup"><span data-stu-id="34e42-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="34e42-107">其建構函式類似。</span><span class="sxs-lookup"><span data-stu-id="34e42-107">Their constructors are similar.</span></span> <span data-ttu-id="34e42-108">您用來擷取其集合的方法也類似。</span><span class="sxs-lookup"><span data-stu-id="34e42-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="34e42-109">屬性集合的 LINQ 查詢運算式看起來非常類似于元素集合的 LINQ 查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="34e42-109">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="34e42-110">系統會保留將屬性加入到項目的順序。</span><span class="sxs-lookup"><span data-stu-id="34e42-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="34e42-111">也就是說，當您逐一查看屬性時，您會看到加入這些屬性的相同順序。</span><span class="sxs-lookup"><span data-stu-id="34e42-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="34e42-112">XAttribute 建構函式</span><span class="sxs-lookup"><span data-stu-id="34e42-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="34e42-113">下列 <xref:System.Xml.Linq.XAttribute> 類別的建構函式就是您常用的建構函式：</span><span class="sxs-lookup"><span data-stu-id="34e42-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="34e42-114">建構函式</span><span class="sxs-lookup"><span data-stu-id="34e42-114">Constructor</span></span>|<span data-ttu-id="34e42-115">描述</span><span class="sxs-lookup"><span data-stu-id="34e42-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="34e42-116">建立 <xref:System.Xml.Linq.XAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="34e42-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="34e42-117">`name` 引數會指定屬性的名稱；`content` 會指定屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="34e42-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="34e42-118">建立具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="34e42-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="34e42-119">下列程式碼顯示一個專案，其中包含在 Visual Basic 中使用 XML 常值的屬性：</span><span class="sxs-lookup"><span data-stu-id="34e42-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="34e42-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="34e42-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="34e42-121">屬性的功能結構</span><span class="sxs-lookup"><span data-stu-id="34e42-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="34e42-122">您無法建構內嵌 <xref:System.Xml.Linq.XAttribute> 物件之結構的 <xref:System.Xml.Linq.XElement> 物件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="34e42-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="34e42-123">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="34e42-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="34e42-124">屬性不是節點</span><span class="sxs-lookup"><span data-stu-id="34e42-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="34e42-125">屬性和項目有一些差異。</span><span class="sxs-lookup"><span data-stu-id="34e42-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="34e42-126"><xref:System.Xml.Linq.XAttribute> 物件在 XML 樹狀結構中不是節點。</span><span class="sxs-lookup"><span data-stu-id="34e42-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="34e42-127">它們是與 XML 項目相關聯的成對名稱/值。</span><span class="sxs-lookup"><span data-stu-id="34e42-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="34e42-128">相較於文件物件模型 (DOM)，這在反映 XML 的結構時，更為接近。</span><span class="sxs-lookup"><span data-stu-id="34e42-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="34e42-129">雖然 <xref:System.Xml.Linq.XAttribute> 物件實際上在 XML 樹狀結構中不是節點，但是使用 <xref:System.Xml.Linq.XAttribute> 物件的方式與使用 <xref:System.Xml.Linq.XElement> 物件的方式非常類似。</span><span class="sxs-lookup"><span data-stu-id="34e42-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="34e42-130">這個區別只有對於撰寫可在節點層級使用 XML 樹狀結構之程式碼的開發人員特別重要。</span><span class="sxs-lookup"><span data-stu-id="34e42-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="34e42-131">這個區別與許多開發人員都無關。</span><span class="sxs-lookup"><span data-stu-id="34e42-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e42-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34e42-132">See also</span></span>

- [<span data-ttu-id="34e42-133">LINQ to XML 程式設計總覽（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="34e42-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
