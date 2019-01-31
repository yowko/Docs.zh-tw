---
title: HOW TO：擷取項目的值 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 2cf7390dde2d0dc1ea37d2dd28f753e5d7580cd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642603"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="74d20-102">HOW TO：擷取項目的值 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="74d20-102">How to: Retrieve the Value of an Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="74d20-103">本主題顯示如何取得項目的值。</span><span class="sxs-lookup"><span data-stu-id="74d20-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="74d20-104">以下有兩種主要的方式可達成此目標。</span><span class="sxs-lookup"><span data-stu-id="74d20-104">There are two main ways to do this.</span></span> <span data-ttu-id="74d20-105">其中一種方式為，將 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 轉型為所需的型別。</span><span class="sxs-lookup"><span data-stu-id="74d20-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="74d20-106">然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別，並將其指派給您的變數。</span><span class="sxs-lookup"><span data-stu-id="74d20-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="74d20-107">或者，您可以使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性或 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="74d20-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="74d20-108">不過，使用 C# 時，轉型 (Casting) 通常是較好的方法。</span><span class="sxs-lookup"><span data-stu-id="74d20-108">With C#, however, casting is generally the better approach.</span></span> <span data-ttu-id="74d20-109">如果您要將項目或屬性轉型為可為 Null 的型別 (Nullable Type)，擷取可能存在或可能不存在之項目 (或屬性) 的值時，較容易撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="74d20-109">If you cast the element or attribute to a nullable type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="74d20-110">本主題中的最後一個範例會示範這個情況。</span><span class="sxs-lookup"><span data-stu-id="74d20-110">The last example in this topic demonstrates this.</span></span> <span data-ttu-id="74d20-111">不過，您無法像透過 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性般，透過轉型設定項目的內容。</span><span class="sxs-lookup"><span data-stu-id="74d20-111">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74d20-112">範例</span><span class="sxs-lookup"><span data-stu-id="74d20-112">Example</span></span>  
 <span data-ttu-id="74d20-113">若要擷取項目的值，您只要將 <xref:System.Xml.Linq.XElement> 物件轉型為所需的型別即可。</span><span class="sxs-lookup"><span data-stu-id="74d20-113">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="74d20-114">您永遠可以將項目轉型為字串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="74d20-114">You can always cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="74d20-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="74d20-115">This example produces the following output:</span></span>  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="74d20-116">範例</span><span class="sxs-lookup"><span data-stu-id="74d20-116">Example</span></span>  
 <span data-ttu-id="74d20-117">您也可以將項目轉型為非字串的型別。</span><span class="sxs-lookup"><span data-stu-id="74d20-117">You can also cast elements to types other than string.</span></span> <span data-ttu-id="74d20-118">例如，如果您有包含整數的項目，您可以將其轉型為 `int`，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="74d20-118">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="74d20-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="74d20-119">This example produces the following output:</span></span>  
  
```  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="74d20-120">會針對下列資料類型提供明確轉換運算子：`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID` 和 `GUID?`。</span><span class="sxs-lookup"><span data-stu-id="74d20-120">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="74d20-121">會提供 <xref:System.Xml.Linq.XAttribute> 物件相同的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="74d20-121">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74d20-122">範例</span><span class="sxs-lookup"><span data-stu-id="74d20-122">Example</span></span>  
 <span data-ttu-id="74d20-123">您可以使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性來擷取項目的內容：</span><span class="sxs-lookup"><span data-stu-id="74d20-123">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="74d20-124">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="74d20-124">This example produces the following output:</span></span>  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="74d20-125">範例</span><span class="sxs-lookup"><span data-stu-id="74d20-125">Example</span></span>  
 <span data-ttu-id="74d20-126">即使您不確定項目是否存在，您有時候還是會嘗試擷取項目的值。</span><span class="sxs-lookup"><span data-stu-id="74d20-126">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="74d20-127">在這個情況下，當您將轉換的項目指派給可為 Null 的型別 (`string` 或 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中其中一個可為 Null 的型別) 時，如果項目不存在，被指派的變數只會設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="74d20-127">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), if the element does not exist the assigned variable is just set to `null`.</span></span> <span data-ttu-id="74d20-128">下列程式碼顯示，項目可能存在或可能不存在時，使用轉型比使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性更為容易。</span><span class="sxs-lookup"><span data-stu-id="74d20-128">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="74d20-129">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="74d20-129">This code produces the following output:</span></span>  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="74d20-130">一般而言，使用轉換擷取元素及屬性內容時，您可以撰寫較簡易的程式碼。</span><span class="sxs-lookup"><span data-stu-id="74d20-130">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d20-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74d20-131">See also</span></span>

- [<span data-ttu-id="74d20-132">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="74d20-132">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
