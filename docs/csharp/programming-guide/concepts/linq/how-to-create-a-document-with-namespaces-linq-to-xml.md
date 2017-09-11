---
title: "如何：建立包含命名空間的文件 (C#) (LINQ to XML) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: ae67df8b5672fc38c790880077d89c122a310485
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="bbaee-102">如何：建立包含命名空間的文件 (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="bbaee-102">How to: Create a Document with Namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="bbaee-103">本主題顯示如何利用命名空間建立文件。</span><span class="sxs-lookup"><span data-stu-id="bbaee-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbaee-104">範例</span><span class="sxs-lookup"><span data-stu-id="bbaee-104">Example</span></span>  
 <span data-ttu-id="bbaee-105">若要建立位於命名空間中的項目或屬性，您必須先宣告並初始化 <xref:System.Xml.Linq.XNamespace> 物件。</span><span class="sxs-lookup"><span data-stu-id="bbaee-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="bbaee-106">然後，您可以使用加法運算子多載來結合命名空間與本機名稱 (以字串表示)。</span><span class="sxs-lookup"><span data-stu-id="bbaee-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="bbaee-107">下列範例會使用一個命名空間建立文件。</span><span class="sxs-lookup"><span data-stu-id="bbaee-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="bbaee-108">根據預設，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 會使用預設命名空間來序列化此文件。</span><span class="sxs-lookup"><span data-stu-id="bbaee-108">By default, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="bbaee-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bbaee-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="bbaee-110">範例</span><span class="sxs-lookup"><span data-stu-id="bbaee-110">Example</span></span>  
 <span data-ttu-id="bbaee-111">下列範例會使用一個命名空間建立文件。</span><span class="sxs-lookup"><span data-stu-id="bbaee-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="bbaee-112">該範例也會建立宣告具有命名空間前置詞之命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="bbaee-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="bbaee-113">若要建立宣告具有前置詞之命名空間的屬性，您可以建立屬性，其中屬性的名稱是命名空間前置詞，而這個名稱位於 <xref:System.Xml.Linq.XNamespace.Xmlns%2A> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="bbaee-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="bbaee-114">這個屬性的值為命名空間的 URI。</span><span class="sxs-lookup"><span data-stu-id="bbaee-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="bbaee-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bbaee-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="bbaee-116">範例</span><span class="sxs-lookup"><span data-stu-id="bbaee-116">Example</span></span>  
 <span data-ttu-id="bbaee-117">下列範例顯示如何建立包含兩個命名空間的文件。</span><span class="sxs-lookup"><span data-stu-id="bbaee-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="bbaee-118">一個是預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="bbaee-118">One is the default namespace.</span></span> <span data-ttu-id="bbaee-119">另一個是具有前置詞的命名空間。</span><span class="sxs-lookup"><span data-stu-id="bbaee-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="bbaee-120">藉由將命名空間屬性包含到根項目 (Root Element) 中，系統會序列化命名空間，讓 http://www.adventure-works.com 成為預設命名空間，而 www.fourthcoffee.com 則利用 "fc" 的前置詞序列化。</span><span class="sxs-lookup"><span data-stu-id="bbaee-120">By including namespace attributes in the root element, the namespaces are serialized so that http://www.adventure-works.com is the default namespace, and www.fourthcoffee.com is serialized with a prefix of "fc".</span></span> <span data-ttu-id="bbaee-121">若要建立宣告預設命名空間的屬性，您可以建立名稱為 "xmlns"，而且沒有命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="bbaee-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="bbaee-122">屬性的值為預設的命名空間 URI。</span><span class="sxs-lookup"><span data-stu-id="bbaee-122">The value of the attribute is the default namespace URI.</span></span>  
  
```csharp  
// The http://www.adventure-works.com namespace is forced to be the default namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute("xmlns", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="bbaee-123">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bbaee-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="bbaee-124">範例</span><span class="sxs-lookup"><span data-stu-id="bbaee-124">Example</span></span>  
 <span data-ttu-id="bbaee-125">下列範例會建立包含兩個命名空間 (兩者皆擁有命名空間前置詞) 的文件。</span><span class="sxs-lookup"><span data-stu-id="bbaee-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),  
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="bbaee-126">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bbaee-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="bbaee-127">範例</span><span class="sxs-lookup"><span data-stu-id="bbaee-127">Example</span></span>  
 <span data-ttu-id="bbaee-128">達到相同結果的另一個方法是，使用展開名稱來代替宣告和建立 <xref:System.Xml.Linq.XNamespace> 物件。</span><span class="sxs-lookup"><span data-stu-id="bbaee-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="bbaee-129">這個方法會有效能隱含作用。</span><span class="sxs-lookup"><span data-stu-id="bbaee-129">This approach has performance implications.</span></span> <span data-ttu-id="bbaee-130">每次您將包含展開名稱的字串傳遞到 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 時，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 就必須剖析名稱、尋找不可部分完成的命名空間，然後尋找不可部分完成的名稱。</span><span class="sxs-lookup"><span data-stu-id="bbaee-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="bbaee-131">這個程序會使用 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="bbaee-131">This process takes CPU time.</span></span> <span data-ttu-id="bbaee-132">如果效能對您很重要，您可能會想要明確宣告並使用 <xref:System.Xml.Linq.XNamespace> 物件。</span><span class="sxs-lookup"><span data-stu-id="bbaee-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="bbaee-133">如果效能是很重要的問題，請參閱[預先同質化 XName 物件 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) 以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bbaee-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="bbaee-134">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bbaee-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbaee-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbaee-135">See Also</span></span>  
 [<span data-ttu-id="bbaee-136">處理 XML 命名空間 (C#)</span><span class="sxs-lookup"><span data-stu-id="bbaee-136">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
