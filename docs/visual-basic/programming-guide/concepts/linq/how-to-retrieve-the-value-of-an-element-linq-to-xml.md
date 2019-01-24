---
title: HOW TO：擷取值的項目 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: 710b5d3e9c636c832d52206921f21c8141cf4319
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671521"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a><span data-ttu-id="15802-102">HOW TO：擷取值的項目 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15802-102">How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="15802-103">本主題顯示如何取得項目的值。</span><span class="sxs-lookup"><span data-stu-id="15802-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="15802-104">以下有兩種主要的方式可達成此目標。</span><span class="sxs-lookup"><span data-stu-id="15802-104">There are two main ways to do this.</span></span> <span data-ttu-id="15802-105">其中一種方式為，將 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 轉型為所需的型別。</span><span class="sxs-lookup"><span data-stu-id="15802-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="15802-106">然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別，並將其指派給您的變數。</span><span class="sxs-lookup"><span data-stu-id="15802-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="15802-107">或者，您可以使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性或 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="15802-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="15802-108">使用 Visual Basic 時，最好的方法是使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="15802-108">With Visual Basic, the best approach is to use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15802-109">範例</span><span class="sxs-lookup"><span data-stu-id="15802-109">Example</span></span>  
 <span data-ttu-id="15802-110">若要擷取項目的值，您只要將 <xref:System.Xml.Linq.XElement> 物件轉型為所需的型別即可。</span><span class="sxs-lookup"><span data-stu-id="15802-110">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="15802-111">您永遠可以將項目轉型為字串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="15802-111">You can always cast an element to a string, as follows:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="15802-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="15802-112">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="15802-113">範例</span><span class="sxs-lookup"><span data-stu-id="15802-113">Example</span></span>  
 <span data-ttu-id="15802-114">您也可以將項目轉型為非字串的型別。</span><span class="sxs-lookup"><span data-stu-id="15802-114">You can also cast elements to types other than string.</span></span> <span data-ttu-id="15802-115">例如，如果您有包含整數的項目，您可以將其轉型為 `int`，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="15802-115">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 <span data-ttu-id="15802-116">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="15802-116">This example produces the following output:</span></span>  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="15802-117">會針對下列資料類型提供明確轉換運算子：`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID` 和 `GUID?`。</span><span class="sxs-lookup"><span data-stu-id="15802-117">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="15802-118">會提供 <xref:System.Xml.Linq.XAttribute> 物件相同的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="15802-118">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15802-119">範例</span><span class="sxs-lookup"><span data-stu-id="15802-119">Example</span></span>  
 <span data-ttu-id="15802-120">您可以使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性來擷取項目的內容：</span><span class="sxs-lookup"><span data-stu-id="15802-120">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="15802-121">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="15802-121">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="15802-122">範例</span><span class="sxs-lookup"><span data-stu-id="15802-122">Example</span></span>  
 <span data-ttu-id="15802-123">即使您不確定項目是否存在，您有時候還是會嘗試擷取項目的值。</span><span class="sxs-lookup"><span data-stu-id="15802-123">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="15802-124">在這個情況下，當您將轉換的項目指派給可為 Null 的型別 (`string` 或 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中其中一個可為 Null 的型別) 時，如果項目不存在，被指派的變數只會設定為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="15802-124">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), if the element does not exist the assigned variable is just set to `Nothing`.</span></span> <span data-ttu-id="15802-125">下列程式碼顯示，項目可能存在或可能不存在時，使用轉型比使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性更為容易。</span><span class="sxs-lookup"><span data-stu-id="15802-125">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child1>child 1 content</Child1>  
                           <Child2>2</Child2>  
                       </Root>  
  
' The following assignments show why it is easier to use  
' casting when the element might or might not exist.  
  
Dim c1 As String = CStr(root.Element("Child1"))  
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element does not exist", c1))  
  
Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))  
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element does not exist", c2.ToString()))  
  
Dim c3 As String = CStr(root.Element("Child3"))  
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element does not exist", c3))  
  
Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))  
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element does not exist", c4.ToString()))  
  
Console.WriteLine()  
  
' The following assignments show the required code when using  
' the Value property when the attribute might or might not exist.  
' Notice that this is more difficult than the casting approach.  
  
Dim e1 As XElement = root.Element("Child1")  
Dim v1 As String  
If (e1 Is Nothing) Then  
    v1 = Nothing  
Else  
    v1 = e1.Value  
End If  
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element does not exist", v1))  
  
Dim e2 As XElement = root.Element("Child2")  
Dim v2 As Nullable(Of Integer)  
If (e2 Is Nothing) Then  
    v2 = Nothing  
Else  
    v2 = e2.Value  
End If  
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element does not exist", v2))  
  
Dim e3 As XElement = root.Element("Child3")  
Dim v3 As String  
If (e3 Is Nothing) Then  
    v3 = Nothing  
Else  
    v3 = e3.Value  
End If  
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element does not exist", v3))  
  
Dim e4 As XElement = root.Element("Child4")  
Dim v4 As Nullable(Of Integer)  
If (e4 Is Nothing) Then  
    v4 = Nothing  
Else  
    v4 = e4.Value  
End If  
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element does not exist", v4))  
```  
  
 <span data-ttu-id="15802-126">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="15802-126">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="15802-127">一般而言，使用轉換擷取元素及屬性內容時，您可以撰寫較簡易的程式碼。</span><span class="sxs-lookup"><span data-stu-id="15802-127">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15802-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15802-128">See also</span></span>
- [<span data-ttu-id="15802-129">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15802-129">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
