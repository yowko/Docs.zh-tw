---
title: 如何檢索元素的值(LINQ 到 XML)(C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: c4bb78e937fe0de08242923cdd7cd638abf571c7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805828"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="5036c-102">如何檢索元素的值(LINQ 到 XML)(C#)</span><span class="sxs-lookup"><span data-stu-id="5036c-102">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>

<span data-ttu-id="5036c-103">本文演示如何獲取元素的值。</span><span class="sxs-lookup"><span data-stu-id="5036c-103">This article shows how to get the value of elements.</span></span> <span data-ttu-id="5036c-104">有兩種主要取得值的方法:</span><span class="sxs-lookup"><span data-stu-id="5036c-104">There are two main ways to get the value:</span></span>

- <span data-ttu-id="5036c-105">將<xref:System.Xml.Linq.XElement><xref:System.Xml.Linq.XAttribute>或轉換為所需的類型。</span><span class="sxs-lookup"><span data-stu-id="5036c-105">Cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="5036c-106">然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別，並將其指派給您的變數。</span><span class="sxs-lookup"><span data-stu-id="5036c-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span>

- <span data-ttu-id="5036c-107">使用<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>或<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="5036c-107">Use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> or <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="5036c-108">您還可以使用這些屬性設置值。</span><span class="sxs-lookup"><span data-stu-id="5036c-108">You can also set the value using these properties.</span></span>

<span data-ttu-id="5036c-109">使用 C# 時,鑄件通常是更好的方法。</span><span class="sxs-lookup"><span data-stu-id="5036c-109">With C#, casting is generally the better approach.</span></span> <span data-ttu-id="5036c-110">如果將元素或屬性強制轉換為可 null 值類型,則在檢索可能存在或不存在的元素(或屬性)的值時,代碼的編寫更簡單。</span><span class="sxs-lookup"><span data-stu-id="5036c-110">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="5036c-111">本文[的最後一個示例](#element-might-not-exist-example)演示,在元素可能不存在的情況下,強制轉換更簡單。</span><span class="sxs-lookup"><span data-stu-id="5036c-111">The [last example](#element-might-not-exist-example) in this article demonstrates that casting is simpler in the case where the element might not exist.</span></span> <span data-ttu-id="5036c-112">不過，您無法像透過 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性般，透過轉型設定項目的內容。</span><span class="sxs-lookup"><span data-stu-id="5036c-112">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="string-cast-example"></a><span data-ttu-id="5036c-113">字串強制轉換範例</span><span class="sxs-lookup"><span data-stu-id="5036c-113">String cast example</span></span>  
 <span data-ttu-id="5036c-114">要檢索元素的值,請將<xref:System.Xml.Linq.XElement>物件強制轉換為所需的類型。</span><span class="sxs-lookup"><span data-stu-id="5036c-114">To retrieve the value of an element, cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="5036c-115">可以將元素轉換為字串,如下所示:</span><span class="sxs-lookup"><span data-stu-id="5036c-115">You can cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="5036c-116">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5036c-116">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a><span data-ttu-id="5036c-117">整數強制轉換範例</span><span class="sxs-lookup"><span data-stu-id="5036c-117">Integer cast example</span></span>  
 <span data-ttu-id="5036c-118">您也可以將項目轉型為非字串的型別。</span><span class="sxs-lookup"><span data-stu-id="5036c-118">You can also cast elements to types other than string.</span></span> <span data-ttu-id="5036c-119">例如，如果您有包含整數的項目，您可以將其轉型為 `int`，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="5036c-119">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="5036c-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5036c-120">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5036c-121">會針對下列資料類型提供明確轉換運算子：`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID` 和 `GUID?`。</span><span class="sxs-lookup"><span data-stu-id="5036c-121">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5036c-122">會提供 <xref:System.Xml.Linq.XAttribute> 物件相同的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="5036c-122">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="value-property-example"></a><span data-ttu-id="5036c-123">值屬性範例</span><span class="sxs-lookup"><span data-stu-id="5036c-123">Value property example</span></span>  
 <span data-ttu-id="5036c-124">您可以使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性來擷取項目的內容：</span><span class="sxs-lookup"><span data-stu-id="5036c-124">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="5036c-125">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5036c-125">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a><span data-ttu-id="5036c-126">元素可能不存在範例</span><span class="sxs-lookup"><span data-stu-id="5036c-126">Element might not exist example</span></span>
 <span data-ttu-id="5036c-127">有時,即使不確定元素是否存在,您也會嘗試檢索該元素的值。</span><span class="sxs-lookup"><span data-stu-id="5036c-127">Sometimes you try to retrieve the value of an element even though you're not sure if it exists.</span></span> <span data-ttu-id="5036c-128">在這種情況下,如果將強制轉換的元素分配給可 null 引用類型或空值類型時,如果該元素不存在,則分配的變數將設定`null`為 。</span><span class="sxs-lookup"><span data-stu-id="5036c-128">In this case, when you assign the casted element to a nullable reference type or nullable value type, if the element does not exist, the assigned variable is set to `null`.</span></span> <span data-ttu-id="5036c-129">下列程式碼顯示，項目可能存在或可能不存在時，使用轉型比使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性更為容易。</span><span class="sxs-lookup"><span data-stu-id="5036c-129">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 <span data-ttu-id="5036c-130">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5036c-130">This code produces the following output:</span></span>  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="5036c-131">一般而言，使用轉換擷取元素及屬性內容時，您可以撰寫較簡易的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5036c-131">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5036c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5036c-132">See also</span></span>

- [<span data-ttu-id="5036c-133">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="5036c-133">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
