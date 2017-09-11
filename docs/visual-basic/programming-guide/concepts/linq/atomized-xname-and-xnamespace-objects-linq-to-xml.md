---
title: "不可部分完成的 XName 和 XNamespace 物件 (LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 1303d0be3715bb6462ef28b1b2286b999661d240
ms.contentlocale: zh-tw
ms.lasthandoff: 06/01/2017


---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="0d043-102">不可部分完成的 XName 和 XNamespace 物件 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d043-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="0d043-103"><xref:System.Xml.Linq.XName>和<xref:System.Xml.Linq.XNamespace>物件*不可部分完成*; 也就是說，如果它們包含相同的限定的名稱時，它們參考相同的物件。</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="0d043-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="0d043-104">這會針對查詢產生效能優勢：當您比較兩個不可部分完成的名稱是否相等時，基礎中繼語言 (Intermediate Language) 只需要判斷這兩個參考是否指向相同的物件即可。</span><span class="sxs-lookup"><span data-stu-id="0d043-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="0d043-105">基礎程式碼不需要進行耗時的字串比較。</span><span class="sxs-lookup"><span data-stu-id="0d043-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="0d043-106">不可部分完成語意</span><span class="sxs-lookup"><span data-stu-id="0d043-106">Atomization Semantics</span></span>  
 <span data-ttu-id="0d043-107">不可部分完成是表示，如果兩個<xref:System.Xml.Linq.XName>物件具有相同的本機名稱，而且它們位於相同的命名空間，它們共用相同的執行個體。</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="0d043-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="0d043-108">相同地，如果兩個<xref:System.Xml.Linq.XNamespace>物件具有相同的命名空間 URI，它們會共用相同的執行個體。</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="0d043-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="0d043-109">若要讓某個類別 (Class) 啟用不可部分完成的物件，此類別的建構函式 (Constructor) 必須是私用 (Private) 而非公用 (Public)。</span><span class="sxs-lookup"><span data-stu-id="0d043-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="0d043-110">這是因為如果建構函式為公用，您就可以建立非不可部分完成的物件。</span><span class="sxs-lookup"><span data-stu-id="0d043-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="0d043-111"><xref:System.Xml.Linq.XName>和<xref:System.Xml.Linq.XNamespace>類別會實作隱含轉換運算子，將成為<xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>.</xref:System.Xml.Linq.XNamespace>或</xref:System.Xml.Linq.XName>字串轉換</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="0d043-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="0d043-112">這就是您取得這些物件之執行個體的方式。</span><span class="sxs-lookup"><span data-stu-id="0d043-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="0d043-113">您無法使用建構函式來取得執行個體，因為無法存取建構函式。</span><span class="sxs-lookup"><span data-stu-id="0d043-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="0d043-114"><xref:System.Xml.Linq.XName>和<xref:System.Xml.Linq.XNamespace>也會實作等號和不等比較運算子，以判斷兩個物件是否要比較相同的執行個體的參考。</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="0d043-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d043-115">範例</span><span class="sxs-lookup"><span data-stu-id="0d043-115">Example</span></span>  
 <span data-ttu-id="0d043-116">下列程式碼會建立一些<xref:System.Xml.Linq.XElement>物件，並且示範相同的名稱會共用相同的執行個體。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="0d043-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
```vb  
Dim r1 As New XElement("Root", "data1")  
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")  
  
If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
Dim n As XName = "Root"  
  
If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
```  
  
 <span data-ttu-id="0d043-117">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0d043-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="0d043-118">如先前所述，不可部分完成之物件的優點是，當您使用需要的座標軸方法的其中一個<xref:System.Xml.Linq.XName>做為參數，此座標軸方法只需要判斷兩個名稱參考相同的執行個體，來選取所需的項目。</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="0d043-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="0d043-119">下列範例會傳遞<xref:System.Xml.Linq.XName>至<xref:System.Xml.Linq.XContainer.Descendants%2A>方法呼叫，則會由於不可部分完成模式有更佳的效能。</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="0d043-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 <span data-ttu-id="0d043-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0d043-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d043-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d043-121">See Also</span></span>  
 [<span data-ttu-id="0d043-122">效能 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d043-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)

