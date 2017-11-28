---
title: "原子化同質化 XName 和 XNamespace 物件 (LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d3c0b1278411c41d002c546f4b1a3be9975a801
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="8bc6c-102">原子化同質化 XName 和 XNamespace 物件 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bc6c-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8bc6c-103"><xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 物件是「不可部分完成」的物件。也就是說，如果它們包含相同的限定名稱，它們就會參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="8bc6c-104">這會針對查詢產生效能優勢：當您比較兩個不可部分完成的名稱是否相等時，基礎中繼語言 (Intermediate Language) 只需要判斷這兩個參考是否指向相同的物件即可。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="8bc6c-105">基礎程式碼不需要進行耗時的字串比較。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="8bc6c-106">不可部分完成語意</span><span class="sxs-lookup"><span data-stu-id="8bc6c-106">Atomization Semantics</span></span>  
 <span data-ttu-id="8bc6c-107">不可部分完成是表示，如果兩個 <xref:System.Xml.Linq.XName> 物件具有相同的本機名稱，而且位於相同的命名空間 (Namespace) 中，它們就會共用相同的執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="8bc6c-108">同樣地，如果兩個 <xref:System.Xml.Linq.XNamespace> 物件具有相同的命名空間 URI，它們就會共用相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="8bc6c-109">若要讓某個類別 (Class) 啟用不可部分完成的物件，此類別的建構函式 (Constructor) 必須是私用 (Private) 而非公用 (Public)。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="8bc6c-110">這是因為如果建構函式為公用，您就可以建立非不可部分完成的物件。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="8bc6c-111"><xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 類別會實作隱含轉換運算子，將字串轉換成 <xref:System.Xml.Linq.XName> 或 <xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="8bc6c-112">這就是您取得這些物件之執行個體的方式。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="8bc6c-113">您無法使用建構函式來取得執行個體，因為無法存取建構函式。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="8bc6c-114"><xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 也會實作等號比較運算子和不等比較運算子，以便判斷所比較的兩個物件是否為相同執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bc6c-115">範例</span><span class="sxs-lookup"><span data-stu-id="8bc6c-115">Example</span></span>  
 <span data-ttu-id="8bc6c-116">下列程式碼會建立一些 <xref:System.Xml.Linq.XElement> 物件，並且示範相同的名稱會共用相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
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
  
 <span data-ttu-id="8bc6c-117">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8bc6c-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="8bc6c-118">如先前所述，不可部分完成之物件的優點在於，當您使用其中一個採取 <xref:System.Xml.Linq.XName> 當做參數的座標軸方法時，此座標軸方法只需要判斷兩個名稱是否參考相同的執行個體，即可選取所需的項目。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="8bc6c-119">下列範例會將 <xref:System.Xml.Linq.XName> 傳遞至 <xref:System.Xml.Linq.XContainer.Descendants%2A> 方法呼叫，而且這樣做會由於不可部分完成模式而具有較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="8bc6c-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 <span data-ttu-id="8bc6c-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8bc6c-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bc6c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bc6c-121">See Also</span></span>  
 [<span data-ttu-id="8bc6c-122">效能 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bc6c-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
