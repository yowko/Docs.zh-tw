---
title: XAttribute 類別概觀 (C#)
description: '屬性是與專案相關聯的名稱/值配對。 System.xml.linq.xattribute> 代表 XML 屬性。 瞭解如何在 c # 中使用 LINQ to XML 中的屬性。'
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 8a19de601041bbb20241c959e909483b97bcf797
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302226"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="bd7a8-105">XAttribute 類別概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="bd7a8-105">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="bd7a8-106">屬性是與項目相關聯的成對名稱/值。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-106">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="bd7a8-107"><xref:System.Xml.Linq.XAttribute> 類別表示 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-107">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="bd7a8-108">概觀</span><span class="sxs-lookup"><span data-stu-id="bd7a8-108">Overview</span></span>  
 <span data-ttu-id="bd7a8-109">在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中使用屬性的方式類似於使用項目。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-109">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="bd7a8-110">其建構函式類似。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-110">Their constructors are similar.</span></span> <span data-ttu-id="bd7a8-111">您用來擷取其集合的方法也類似。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-111">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="bd7a8-112">屬性集合的 LINQ 查詢運算式看起來非常類似于元素集合的 LINQ 查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-112">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="bd7a8-113">系統會保留將屬性加入到項目的順序。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-113">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="bd7a8-114">也就是說，當您逐一查看屬性時，您會看到加入這些屬性的相同順序。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-114">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="bd7a8-115">XAttribute 建構函式</span><span class="sxs-lookup"><span data-stu-id="bd7a8-115">The XAttribute Constructor</span></span>  
 <span data-ttu-id="bd7a8-116">下列 <xref:System.Xml.Linq.XAttribute> 類別的建構函式就是您常用的建構函式：</span><span class="sxs-lookup"><span data-stu-id="bd7a8-116">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="bd7a8-117">建構函式</span><span class="sxs-lookup"><span data-stu-id="bd7a8-117">Constructor</span></span>|<span data-ttu-id="bd7a8-118">描述</span><span class="sxs-lookup"><span data-stu-id="bd7a8-118">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="bd7a8-119">建立 <xref:System.Xml.Linq.XAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-119">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="bd7a8-120">`name` 引數會指定屬性的名稱；`content` 會指定屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-120">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="bd7a8-121">建立具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="bd7a8-121">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="bd7a8-122">下列程式碼顯示建立包含屬性之項目的一般工作：</span><span class="sxs-lookup"><span data-stu-id="bd7a8-122">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="bd7a8-123">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bd7a8-123">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="bd7a8-124">屬性的功能結構</span><span class="sxs-lookup"><span data-stu-id="bd7a8-124">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="bd7a8-125">您無法建構內嵌 <xref:System.Xml.Linq.XAttribute> 物件之結構的 <xref:System.Xml.Linq.XElement> 物件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bd7a8-125">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 <span data-ttu-id="bd7a8-126">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bd7a8-126">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="bd7a8-127">屬性不是節點</span><span class="sxs-lookup"><span data-stu-id="bd7a8-127">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="bd7a8-128">屬性和項目有一些差異。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-128">There are some differences between attributes and elements.</span></span> <span data-ttu-id="bd7a8-129"><xref:System.Xml.Linq.XAttribute> 物件在 XML 樹狀結構中不是節點。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-129"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="bd7a8-130">它們是與 XML 項目相關聯的成對名稱/值。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-130">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="bd7a8-131">相較於文件物件模型 (DOM)，這在反映 XML 的結構時，更為接近。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-131">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="bd7a8-132">雖然 <xref:System.Xml.Linq.XAttribute> 物件實際上在 XML 樹狀結構中不是節點，但是使用 <xref:System.Xml.Linq.XAttribute> 物件的方式與使用 <xref:System.Xml.Linq.XElement> 物件的方式非常類似。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-132">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="bd7a8-133">這個區別只有對於撰寫可在節點層級使用 XML 樹狀結構之程式碼的開發人員特別重要。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-133">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="bd7a8-134">這個區別與許多開發人員都無關。</span><span class="sxs-lookup"><span data-stu-id="bd7a8-134">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd7a8-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd7a8-135">See also</span></span>

- [<span data-ttu-id="bd7a8-136">LINQ to XML 程式設計概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="bd7a8-136">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
