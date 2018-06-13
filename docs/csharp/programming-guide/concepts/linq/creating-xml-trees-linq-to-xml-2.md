---
title: 在 C# 中建立 XML 樹狀 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 4fcd0c14970dd4aabe4d51335f9a0a0a991ef019
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335456"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="8bdb2-102">在 C# 中建立 XML 樹狀 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8bdb2-102">Creating XML Trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="8bdb2-103">本節提供在 C# 中建立 XML 樹狀的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="8bdb2-104">如需使用 LINQ 查詢的結果作為 <xref:System.Xml.Linq.XElement> 內容的資訊，請參閱[函數式建構 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="8bdb2-105">建構項目</span><span class="sxs-lookup"><span data-stu-id="8bdb2-105">Constructing Elements</span></span>  
 <span data-ttu-id="8bdb2-106"><xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XAttribute> 建構函式的簽章可讓您傳遞項目或屬性的內容，當做建構函式的引數。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="8bdb2-107">由於其中一個建構函式採用多個引數，因此，您可以傳遞任何數目的子項目。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="8bdb2-108">當然，這些子項目中的每個子項目都可以包含其自己的子項目。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="8bdb2-109">對於任何項目，您可以加入任何數目的屬性。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="8bdb2-110">加入 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement>) 或 <xref:System.Xml.Linq.XAttribute> 物件時，如果新內容沒有父代，這些物件只會附加到 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="8bdb2-111">如果新內容已經成為父代，或是其他 XML 樹狀的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="8bdb2-112">本主題中的最後一個範例會示範這個情況。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="8bdb2-113">若要建立 `contacts`<xref:System.Xml.Linq.XElement>，您可以使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="8bdb2-114">如果縮排正確，建構 <xref:System.Xml.Linq.XElement> 物件的程式碼會非常接近基礎 XML 的結構。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="8bdb2-115">XElement 建構函式</span><span class="sxs-lookup"><span data-stu-id="8bdb2-115">XElement Constructors</span></span>  
 <span data-ttu-id="8bdb2-116"><xref:System.Xml.Linq.XElement> 類別會將下列建構函式用於功能結構。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="8bdb2-117">請注意，<xref:System.Xml.Linq.XElement> 還有其他建構函式，但是它們不用於功能結構，因此未在此處列出。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="8bdb2-118">建構函式</span><span class="sxs-lookup"><span data-stu-id="8bdb2-118">Constructor</span></span>|<span data-ttu-id="8bdb2-119">描述</span><span class="sxs-lookup"><span data-stu-id="8bdb2-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="8bdb2-120">建立 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="8bdb2-121">`name` 參數會指定項目的名稱；`content` 會指定項目的內容。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="8bdb2-122">在將其 <xref:System.Xml.Linq.XElement> 初始化為指定之名稱的情況下，建立 <xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="8bdb2-123">在將其 <xref:System.Xml.Linq.XElement> 初始化為指定之名稱的情況下，建立 <xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="8bdb2-124">系統會從參數清單的內容建立屬性和/或子項目。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="8bdb2-125">`content` 參數非常有彈性。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="8bdb2-126">它支援物件為 <xref:System.Xml.Linq.XElement> 之有效子系的任何型別。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="8bdb2-127">下列規則適用於傳入此參數的不同型別物件：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
-   <span data-ttu-id="8bdb2-128">字串當做文字內容加入。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-128">A string is added as text content.</span></span>  
  
-   <span data-ttu-id="8bdb2-129"><xref:System.Xml.Linq.XElement> 當做子項目加入。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
-   <span data-ttu-id="8bdb2-130"><xref:System.Xml.Linq.XAttribute> 當做屬性加入。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
-   <span data-ttu-id="8bdb2-131"><xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> 或 <xref:System.Xml.Linq.XText> 當做子內容加入。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
-   <span data-ttu-id="8bdb2-132">系統會列舉 <xref:System.Collections.IEnumerable>，並將這些規則遞迴地套用到結果。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
-   <span data-ttu-id="8bdb2-133">若是其他任何型別，則會呼叫其 `ToString` 方法，並將結果當做文字內容加入。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="8bdb2-134">建立包含內容的 XElement</span><span class="sxs-lookup"><span data-stu-id="8bdb2-134">Creating an XElement with Content</span></span>  
 <span data-ttu-id="8bdb2-135">您可以建立包含具有單一方法呼叫之簡單內容的 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="8bdb2-136">如果要這樣做，請將內容指定為第二個參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="8bdb2-137">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="8bdb2-138">您可以傳遞任何型別的物件當做內容。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="8bdb2-139">例如，下列程式碼會建立包含浮點數的項目當做內容：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="8bdb2-140">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="8bdb2-141">浮點數為 Boxed 而且會傳入建構函式。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="8bdb2-142">Boxed 數字會轉換為字串，並當做項目的內容使用。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="8bdb2-143">建立包含子項目的 XElement</span><span class="sxs-lookup"><span data-stu-id="8bdb2-143">Creating an XElement with a Child Element</span></span>  
 <span data-ttu-id="8bdb2-144">如果您要針對內容引數傳遞 <xref:System.Xml.Linq.XElement> 類別的執行個體，建構函式會建立包含子項目的項目：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="8bdb2-145">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="8bdb2-146">建立包含多個子項目的 XElement</span><span class="sxs-lookup"><span data-stu-id="8bdb2-146">Creating an XElement with Multiple Child Elements</span></span>  
 <span data-ttu-id="8bdb2-147">您可以針對內容傳入多個 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="8bdb2-148">每個 <xref:System.Xml.Linq.XElement> 物件都會當做子項目包含在內。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="8bdb2-149">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="8bdb2-150">藉由延伸以上的範例，您可以建立完整的 XML 樹狀結構，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),                                                   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
Console.WriteLine(contacts);  
```  
  
 <span data-ttu-id="8bdb2-151">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-151">This example produces the following output:</span></span>  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="8bdb2-152">建立空項目</span><span class="sxs-lookup"><span data-stu-id="8bdb2-152">Creating an Empty Element</span></span>  
 <span data-ttu-id="8bdb2-153">若要建立空的 <xref:System.Xml.Linq.XElement>，您不用將任何內容傳遞到建構函式。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-153">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="8bdb2-154">下列範例會建立空項目：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-154">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="8bdb2-155">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-155">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="8bdb2-156">附加與複製</span><span class="sxs-lookup"><span data-stu-id="8bdb2-156">Attaching vs. Cloning</span></span>  
 <span data-ttu-id="8bdb2-157">如先前所述，加入 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement>) 或 <xref:System.Xml.Linq.XAttribute> 物件時，如果新內容沒有父代，這些物件只會附加到 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-157">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="8bdb2-158">如果新內容已經成為父代，或是其他 XML 樹狀的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="8bdb2-158">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 <span data-ttu-id="8bdb2-159">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8bdb2-159">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bdb2-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="8bdb2-160">See Also</span></span>  
 [<span data-ttu-id="8bdb2-161">建立 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="8bdb2-161">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
