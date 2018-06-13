---
title: 處理全域命名空間 (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: c1f34b374f956ec0a8b9658742e529d7ccb1b2ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648901"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="7b55a-102">處理全域命名空間 (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7b55a-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="7b55a-103">在 Visual Basic 中的 XML 常值的重要功能的其中一個是使用宣告 XML 命名空間的能力`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7b55a-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="7b55a-104">利用這個功能，您可以宣告使用前置詞的 XML 命名空間，或者，您可以宣告預設的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b55a-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="7b55a-105">這項功能在兩種情況下很有用。</span><span class="sxs-lookup"><span data-stu-id="7b55a-105">This capability is useful in two situations.</span></span> <span data-ttu-id="7b55a-106">第一，在 XML 常值中宣告的命名空間不會延續到內嵌的運算式中。</span><span class="sxs-lookup"><span data-stu-id="7b55a-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="7b55a-107">宣告全域命名空間會減少您必須做的工作量，以便搭配命名空間使用內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="7b55a-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="7b55a-108">第二，您必須宣告全域命名空間，才能搭配 XML 使用命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b55a-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="7b55a-109">您可以在專案層級宣告全域命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b55a-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="7b55a-110">您也可以在複寫專案層級全域命名空間的模組層級宣告全域命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b55a-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="7b55a-111">最後，您可以在 XML 常值中複寫全域命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b55a-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="7b55a-112">使用位於全域宣告之命名空間中的 XML 常值或 XML 屬性時，您可以在 Visual Studio 中，將滑鼠停留在 XML 常值或屬性的擴充名稱上，藉以查看它們。</span><span class="sxs-lookup"><span data-stu-id="7b55a-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="7b55a-113">您將會在工具提示中看到擴充名稱。</span><span class="sxs-lookup"><span data-stu-id="7b55a-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="7b55a-114">您可以使用 <xref:System.Xml.Linq.XNamespace> 方法，取得對應到全域命名空間的 `GetXmlNamespace` 物件。</span><span class="sxs-lookup"><span data-stu-id="7b55a-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="7b55a-115">全域命名空間的範例</span><span class="sxs-lookup"><span data-stu-id="7b55a-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="7b55a-116">下列範例會使用 `Imports` 陳述式宣告預設的全域命名空間，然後使用 XML 常值來初始化該命名空間中的 <xref:System.Xml.Linq.XElement> 物件：</span><span class="sxs-lookup"><span data-stu-id="7b55a-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7b55a-117">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7b55a-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="7b55a-118">下列範例會宣告具有前置詞的全域命名空間，然後使用 XML 常值來初始化項目：</span><span class="sxs-lookup"><span data-stu-id="7b55a-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7b55a-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7b55a-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="7b55a-120">全域命名空間與內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="7b55a-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="7b55a-121">在 XML 常值中宣告的命名空間不會延續到內嵌的運算式中。</span><span class="sxs-lookup"><span data-stu-id="7b55a-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="7b55a-122">下列範例會宣告預設的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b55a-122">The following example declares a default namespace.</span></span> <span data-ttu-id="7b55a-123">接著，它會使用 `Child` 項目的內嵌運算式。</span><span class="sxs-lookup"><span data-stu-id="7b55a-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="7b55a-124">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7b55a-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="7b55a-125">如同您所見，所產生的 XML 包括預設命名空間的宣告，因此 `Child` 項目不在任何命名空間中。</span><span class="sxs-lookup"><span data-stu-id="7b55a-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="7b55a-126">您可以在內嵌的運算式中重新宣告命名空間，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7b55a-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="7b55a-127">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7b55a-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="7b55a-128">不過，這種方法在使用上較為麻煩，所以全域預設命名空間仍然是較佳的方法。</span><span class="sxs-lookup"><span data-stu-id="7b55a-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="7b55a-129">透過全域預設命名空間，您可以使用 XML 常值，而不需宣告命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b55a-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="7b55a-130">所產生的 XML 將會位於全域宣告的預設命名空間中。</span><span class="sxs-lookup"><span data-stu-id="7b55a-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7b55a-131">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7b55a-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="7b55a-132">搭配 XML 屬性使用命名空間</span><span class="sxs-lookup"><span data-stu-id="7b55a-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="7b55a-133">如果您使用命名空間中的 XML 樹狀結構，而且您使用 XML 屬性，則您必須使用全域命名空間，XML 屬性才會也在正確的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="7b55a-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="7b55a-134">下列範例會在命名空間中宣告 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="7b55a-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="7b55a-135">接著，它會列印 `Child` 項目的計數。</span><span class="sxs-lookup"><span data-stu-id="7b55a-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="7b55a-136">這個範例表示沒有 `Child` 項目。</span><span class="sxs-lookup"><span data-stu-id="7b55a-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="7b55a-137">它會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7b55a-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="7b55a-138">但是，如果您要宣告預設的全域命名空間，則 XML 常值和 XML 屬性都會位於預設的全域命名空間中：</span><span class="sxs-lookup"><span data-stu-id="7b55a-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7b55a-139">這個範例表示有一個 `Child` 項目，</span><span class="sxs-lookup"><span data-stu-id="7b55a-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="7b55a-140">它會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7b55a-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="7b55a-141">如果您要宣告具有前置詞的全域命名空間，可以將前置詞同時用於 XML 常值和 XML 屬性：</span><span class="sxs-lookup"><span data-stu-id="7b55a-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="7b55a-142">XNamespace 和全域命名空間</span><span class="sxs-lookup"><span data-stu-id="7b55a-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="7b55a-143">您可以使用 <xref:System.Xml.Linq.XNamespace> 方法，取得 `GetXmlNamespace` 物件：</span><span class="sxs-lookup"><span data-stu-id="7b55a-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7b55a-144">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7b55a-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b55a-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b55a-145">See Also</span></span>  
 [<span data-ttu-id="7b55a-146">處理 XML 命名空間 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b55a-146">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
