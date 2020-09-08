---
title: '如何在 c # 中建立具有命名空間的檔-LINQ to XML'
description: '使用 c # 中的 XNamespace 物件來建立檔，其具有具有前置詞的預設命名空間或命名空間。'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 3ec9624bcc599a73a6872e5c4c79504a1a4b4380
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552278"
---
# <a name="how-to-create-a-document-with-namespaces-in-c-linq-to-xml"></a><span data-ttu-id="029ac-103">如何在 c # 中建立具有命名空間的檔 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="029ac-103">How to create a document with namespaces in C# (LINQ to XML)</span></span>

<span data-ttu-id="029ac-104">本文說明如何在 c # 中建立具有命名空間的檔。</span><span class="sxs-lookup"><span data-stu-id="029ac-104">This article shows how to create documents in C# that have namespaces.</span></span>

## <a name="example-declare-and-initialize-a-default-namespace"></a><span data-ttu-id="029ac-105">範例：宣告和初始化預設命名空間</span><span class="sxs-lookup"><span data-stu-id="029ac-105">Example: Declare and initialize a default namespace</span></span>

<span data-ttu-id="029ac-106">若要建立位於命名空間中的元素或屬性，您必須先宣告和初始化 <xref:System.Xml.Linq.XNamespace> 物件。</span><span class="sxs-lookup"><span data-stu-id="029ac-106">To create an element or an attribute that's in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="029ac-107">然後，您可以使用加法運算子多載來結合命名空間與本機名稱 (以字串表示)。</span><span class="sxs-lookup"><span data-stu-id="029ac-107">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>

<span data-ttu-id="029ac-108">下列範例會使用一個命名空間建立文件。</span><span class="sxs-lookup"><span data-stu-id="029ac-108">The following example creates a document with one namespace.</span></span> <span data-ttu-id="029ac-109">根據預設，LINQ to XML 會將此檔序列化為預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="029ac-109">By default, LINQ to XML serializes this document with a default namespace.</span></span>

```csharp
// Create an XML tree in a namespace.
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="029ac-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="029ac-110">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child>child content</Child>
</Root>
```

## <a name="example-create-a-document-that-has-a-namespace-and-an-attribute"></a><span data-ttu-id="029ac-111">範例：建立具有命名空間和屬性的檔</span><span class="sxs-lookup"><span data-stu-id="029ac-111">Example: Create a document that has a namespace and an attribute</span></span>

<span data-ttu-id="029ac-112">下列範例會使用一個命名空間建立文件。</span><span class="sxs-lookup"><span data-stu-id="029ac-112">The following example creates a document with one namespace.</span></span> <span data-ttu-id="029ac-113">該範例也會建立宣告具有命名空間前置詞之命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="029ac-113">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="029ac-114">若要建立宣告具有前置詞之命名空間的屬性，您可以建立屬性，其中屬性的名稱是命名空間前置詞，而這個名稱位於 <xref:System.Xml.Linq.XNamespace.Xmlns%2A> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="029ac-114">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="029ac-115">這個屬性的值為命名空間的 URI。</span><span class="sxs-lookup"><span data-stu-id="029ac-115">The value of this attribute is the URI of the namespace.</span></span>

```csharp
// Create an XML tree in a namespace, with a specified prefix
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="029ac-116">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="029ac-116">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a><span data-ttu-id="029ac-117">範例：建立具有兩個命名空間的檔，一個具有前置詞</span><span class="sxs-lookup"><span data-stu-id="029ac-117">Example: Create a document that has two namespaces, one with a prefix</span></span>

<span data-ttu-id="029ac-118">下列範例顯示如何建立包含兩個命名空間的文件。</span><span class="sxs-lookup"><span data-stu-id="029ac-118">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="029ac-119">其中一個是預設命名空間，另一個是具有前置詞的命名空間。</span><span class="sxs-lookup"><span data-stu-id="029ac-119">One is the default namespace, the other is a namespace with a prefix.</span></span>

<span data-ttu-id="029ac-120">藉由將命名空間屬性包含在根項目中，就會將命名空間序列化為 `http://www.adventure-works.com` 預設命名空間，並 `www.fourthcoffee.com` 使用的前置詞進行序列化 `fc` 。</span><span class="sxs-lookup"><span data-stu-id="029ac-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of `fc`.</span></span> <span data-ttu-id="029ac-121">若要建立宣告預設命名空間的屬性，您可以建立名稱 `xmlns` 不含命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="029ac-121">To create an attribute that declares a default namespace, you create an attribute with the name `xmlns`, without a namespace.</span></span> <span data-ttu-id="029ac-122">屬性的值為預設的命名空間 URI。</span><span class="sxs-lookup"><span data-stu-id="029ac-122">The value of the attribute is the default namespace URI.</span></span>

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

<span data-ttu-id="029ac-123">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="029ac-123">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <DifferentChild>other content</DifferentChild>
  </fc:Child>
  <Child2>c2 content</Child2>
  <fc:Child3>c3 content</fc:Child3>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a><span data-ttu-id="029ac-124">範例：建立具有兩個命名空間的檔，兩者都有首碼</span><span class="sxs-lookup"><span data-stu-id="029ac-124">Example: Create a document that has two namespaces, both with prefixes</span></span>

<span data-ttu-id="029ac-125">下列範例會建立包含兩個命名空間 (兩者皆擁有命名空間前置詞) 的文件。</span><span class="sxs-lookup"><span data-stu-id="029ac-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>

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

<span data-ttu-id="029ac-126">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="029ac-126">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="example-create-a-namespace-using-expanded-names"></a><span data-ttu-id="029ac-127">範例：使用展開的名稱建立命名空間</span><span class="sxs-lookup"><span data-stu-id="029ac-127">Example: Create a namespace using expanded names</span></span>

<span data-ttu-id="029ac-128">達到相同結果的另一個方法是，使用擴充名稱來代替宣告和建立 <xref:System.Xml.Linq.XNamespace> 物件。</span><span class="sxs-lookup"><span data-stu-id="029ac-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>

<span data-ttu-id="029ac-129">這個方法會有效能隱含作用。</span><span class="sxs-lookup"><span data-stu-id="029ac-129">This approach has performance implications.</span></span> <span data-ttu-id="029ac-130">每次您將包含擴充名稱的字串傳遞至 LINQ to XML 時，LINQ to XML 必須剖析名稱、尋找不可部分完成的命名空間，然後尋找不可部分完成的名稱。</span><span class="sxs-lookup"><span data-stu-id="029ac-130">Each time you pass a string that contains an expanded name to LINQ to XML, LINQ to XML must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="029ac-131">這個程序會使用 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="029ac-131">This process takes CPU time.</span></span> <span data-ttu-id="029ac-132">如果效能對您很重要，您可能會想要明確宣告並使用 <xref:System.Xml.Linq.XNamespace> 物件。</span><span class="sxs-lookup"><span data-stu-id="029ac-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>

<span data-ttu-id="029ac-133">如果效能是很重要的問題，請參閱 [預先不可部分完成的 XName 物件](pre-atomization-xname-objects.md) ，以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="029ac-133">If performance is an important issue, see [Pre-Atomization of XName Objects](pre-atomization-xname-objects.md) for more information.</span></span>

```csharp
// Create an XML tree in a namespace, with a specified prefix
XElement root = new XElement("{http://www.adventure-works.com}Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement("{http://www.adventure-works.com}Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="029ac-134">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="029ac-134">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="029ac-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="029ac-135">See also</span></span>

- [<span data-ttu-id="029ac-136">命名空間總覽</span><span class="sxs-lookup"><span data-stu-id="029ac-136">Namespaces overview</span></span>](namespaces-overview.md)
