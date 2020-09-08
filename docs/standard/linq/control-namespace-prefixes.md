---
title: 如何控制命名空間前置詞-LINQ to XML
description: '您可以在 c # 中序列化 XML 樹狀結構，並 Visual Basic 來控制命名空間前置詞。 若要這樣做，請插入宣告命名空間的屬性。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 07efc23c11cd0dc0d281968911cf24d6ecbc76a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552139"
---
# <a name="how-to-control-namespace-prefixes-linq-to-xml"></a><span data-ttu-id="9b9ce-104">如何控制命名空間前置詞 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9b9ce-104">How to control namespace prefixes (LINQ to XML)</span></span>

<span data-ttu-id="9b9ce-105">本文描述如何在 c # 中序列化 XML 樹狀結構和 Visual Basic 時，控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-105">This article describes how to control namespace prefixes when serializing an XML tree in C# and Visual Basic.</span></span>

<span data-ttu-id="9b9ce-106">在許多情況下，不需要控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-106">In many situations, it's not necessary to control namespace prefixes.</span></span> <span data-ttu-id="9b9ce-107">不過，某些 XML 程式設計工具需要它。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-107">However, certain XML programming tools require it.</span></span> <span data-ttu-id="9b9ce-108">例如，您可能會操作 XSLT 樣式表單或 XAML 檔，其中包含參考特定命名空間前置詞的內嵌 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-108">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes.</span></span> <span data-ttu-id="9b9ce-109">在這種情況下，請務必使用這些前置詞來序列化檔。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-109">In such a case, it's important that the document be serialized with those prefixes.</span></span> <span data-ttu-id="9b9ce-110">這是控制命名空間前置詞的常見原因。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-110">This is a common reason for controlling namespace prefixes.</span></span>

<span data-ttu-id="9b9ce-111">另一個原因是您想要讓使用者手動編輯 XML 檔，而且您想要建立方便使用者輸入的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-111">Another reason is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="9b9ce-112">例如，您可能要產生 XSD 文件。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-112">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="9b9ce-113">若要轉換結構描述，建議您使用 `xs` 或 `xsd` 做為結構描述命名空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-113">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>

<span data-ttu-id="9b9ce-114">若要控制命名空間前置詞，您可插入宣告命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-114">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="9b9ce-115">如果您宣告具有特定前置詞的命名空間，LINQ to XML 將會在序列化時嘗試接受命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-115">If you declare the namespaces with specific prefixes, LINQ to XML will attempt to honor the namespace prefixes when serializing.</span></span>

<span data-ttu-id="9b9ce-116">若要建立宣告具有特定前置詞之命名空間的屬性，您可以建立屬性，其中之屬性名稱的命名空間為 <xref:System.Xml.Linq.XNamespace.Xmlns%2A>，而屬性的名稱為命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-116">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="9b9ce-117">屬性的值為命名空間的 URI。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-117">The value of the attribute is the URI of the namespace.</span></span>

## <a name="example-create-two-namespaces-that-have-prefixes"></a><span data-ttu-id="9b9ce-118">範例：建立具有前置詞的兩個命名空間</span><span class="sxs-lookup"><span data-stu-id="9b9ce-118">Example: Create two namespaces that have prefixes</span></span>

<span data-ttu-id="9b9ce-119">這個範例會宣告兩個命名空間。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-119">This example declares two namespaces.</span></span> <span data-ttu-id="9b9ce-120">它會指定命名空間的前置詞 `aw` `http://www.adventure-works.com` ，以及 `fc` 命名空間的前置詞 `www.fourthcoffee.com` 。</span><span class="sxs-lookup"><span data-stu-id="9b9ce-120">It specifies the prefix `aw` for the `http://www.adventure-works.com` namespace, and the prefix `fc` for the `www.fourthcoffee.com` namespace.</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

This example produces the following output:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="9b9ce-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b9ce-121">See also</span></span>

- [<span data-ttu-id="9b9ce-122">命名空間總覽</span><span class="sxs-lookup"><span data-stu-id="9b9ce-122">Namespaces overview</span></span>](namespaces-overview.md)
