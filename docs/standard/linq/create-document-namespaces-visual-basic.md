---
title: 如何在 Visual Basic LINQ to XML 中建立具有命名空間的檔
description: 在 Visual Basic 中使用 XML 常值，以建立具有前置詞的預設命名空間或命名空間的檔。
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 48e2a1abf8f7a82df3db5cb2f580804d67776b15
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552275"
---
# <a name="how-to-create-a-document-with-namespaces-in-visual-basic-linq-to-xml"></a><span data-ttu-id="1357f-103">如何在 Visual Basic (LINQ to XML) 中建立具有命名空間的檔</span><span class="sxs-lookup"><span data-stu-id="1357f-103">How to create a document with namespaces in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="1357f-104">本文說明如何在 Visual Basic 中建立包含命名空間的檔。</span><span class="sxs-lookup"><span data-stu-id="1357f-104">This article shows how to create a document with namespaces in Visual Basic.</span></span>

<span data-ttu-id="1357f-105">在 Visual Basic 中使用 XML 常值時，使用者可以定義一個預設的 XML 全域命名空間。</span><span class="sxs-lookup"><span data-stu-id="1357f-105">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="1357f-106">這個命名空間同時為 XML 常值和 XML 屬性的預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="1357f-106">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="1357f-107">XML 預設命名空間可在專案層級或檔案層級定義。</span><span class="sxs-lookup"><span data-stu-id="1357f-107">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="1357f-108">如果是在檔案層級定義的，它會覆寫專案層級的預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="1357f-108">If it's defined at the file level, it overrides the default namespace at the project level.</span></span>

<span data-ttu-id="1357f-109">您也可以定義其他命名空間，並為這些命名空間指定命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="1357f-109">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span> <span data-ttu-id="1357f-110">您可以使用 `Imports` 關鍵字來定義這兩種類型的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1357f-110">You use the `Imports` keyword to define both types of namespace.</span></span>

<span data-ttu-id="1357f-111">如需詳細資訊，請參閱 [Visual Basic 中的 XML 常](xml-literals.md)值。</span><span class="sxs-lookup"><span data-stu-id="1357f-111">For more information, see [XML literals in Visual Basic](xml-literals.md).</span></span>

<span data-ttu-id="1357f-112">請注意，XML 預設命名空間僅適用於項目，而不適用於屬性。</span><span class="sxs-lookup"><span data-stu-id="1357f-112">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="1357f-113">預設命名空間中的屬性預設為。</span><span class="sxs-lookup"><span data-stu-id="1357f-113">Attributes are by default in the default namespace.</span></span> <span data-ttu-id="1357f-114">不過，您可以使用命名空間前置詞，將屬性放到命名空間中。</span><span class="sxs-lookup"><span data-stu-id="1357f-114">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>

## <a name="example-create-a-document-that-has-a-namespace"></a><span data-ttu-id="1357f-115">範例：建立具有命名空間的檔</span><span class="sxs-lookup"><span data-stu-id="1357f-115">Example: Create a document that has a namespace</span></span>

<span data-ttu-id="1357f-116">此範例會建立包含命名空間的文件。</span><span class="sxs-lookup"><span data-stu-id="1357f-116">This example creates a document that contains a namespace.</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child aw:Att="attvalue"/>
            </aw:Root>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="1357f-117">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1357f-117">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child aw:Att="attvalue" />
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a><span data-ttu-id="1357f-118">範例：建立具有兩個命名空間的檔，一個具有前置詞</span><span class="sxs-lookup"><span data-stu-id="1357f-118">Example: Create a document that has two namespaces, one with a prefix</span></span>

<span data-ttu-id="1357f-119">此範例會建立包含兩個命名空間的檔。</span><span class="sxs-lookup"><span data-stu-id="1357f-119">This example creates a document that contains two namespaces.</span></span> <span data-ttu-id="1357f-120">其中一個是預設命名空間，另一個則有前置詞。</span><span class="sxs-lookup"><span data-stu-id="1357f-120">One is the default namespace, the other has a prefix.</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child Att="attvalue"/>
                <fc:Child2>child2 content</fc:Child2>
            </Root>
        Console.WriteLine(root)
    End Sub

End Module
```

<span data-ttu-id="1357f-121">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1357f-121">This example produces the following output:</span></span>

```xml
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">
  <Child Att="attvalue" />
  <fc:Child2>child2 content</fc:Child2>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a><span data-ttu-id="1357f-122">範例：建立具有兩個命名空間的檔，兩者都有首碼</span><span class="sxs-lookup"><span data-stu-id="1357f-122">Example: Create a document that has two namespaces, both with prefixes</span></span>

<span data-ttu-id="1357f-123">下列範例會建立包含兩個命名空間的檔，這兩個命名空間都具有命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="1357f-123">The following example creates a document that contains two namespaces, both having namespace prefixes.</span></span>

<span data-ttu-id="1357f-124">當序列化 XML 樹狀結構時，LINQ to XML 會發出必要的命名空間宣告，讓每個專案都在其指定的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="1357f-124">When serializing an XML tree, LINQ to XML emits namespace declarations as required so that each element is in its designated namespace.</span></span>

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

End Module
```

<span data-ttu-id="1357f-125">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1357f-125">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="1357f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1357f-126">See also</span></span>

- [<span data-ttu-id="1357f-127">命名空間總覽</span><span class="sxs-lookup"><span data-stu-id="1357f-127">Namespaces overview</span></span>](namespaces-overview.md)
