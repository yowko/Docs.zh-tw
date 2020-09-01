---
description: namespace 關鍵字 - C# 參考
title: namespace 關鍵字 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: a6cfd1c3d37cbdef1f0dd72ddca85ce91f2e183b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139576"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="59bf1-103">namespace (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="59bf1-103">namespace (C# Reference)</span></span>

<span data-ttu-id="59bf1-104">`namespace` 關鍵字用來宣告包含一組相關物件的範圍。</span><span class="sxs-lookup"><span data-stu-id="59bf1-104">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="59bf1-105">您可以使用命名空間來組織程式碼項目，並建立全域唯一的型別。</span><span class="sxs-lookup"><span data-stu-id="59bf1-105">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="59bf1-106">備註</span><span class="sxs-lookup"><span data-stu-id="59bf1-106">Remarks</span></span>

<span data-ttu-id="59bf1-107">在命名空間內，您可以宣告下列一或多個類型：</span><span class="sxs-lookup"><span data-stu-id="59bf1-107">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="59bf1-108">另一個命名空間</span><span class="sxs-lookup"><span data-stu-id="59bf1-108">another namespace</span></span>

- [<span data-ttu-id="59bf1-109">class</span><span class="sxs-lookup"><span data-stu-id="59bf1-109">class</span></span>](class.md)

- [<span data-ttu-id="59bf1-110">interface</span><span class="sxs-lookup"><span data-stu-id="59bf1-110">interface</span></span>](interface.md)

- [<span data-ttu-id="59bf1-111">結構</span><span class="sxs-lookup"><span data-stu-id="59bf1-111">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="59bf1-112">枚舉</span><span class="sxs-lookup"><span data-stu-id="59bf1-112">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="59bf1-113">delegate</span><span class="sxs-lookup"><span data-stu-id="59bf1-113">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="59bf1-114">無論是否在 C# 來源檔案中明確宣告命名空間，編譯器都會加入預設的命名空間。</span><span class="sxs-lookup"><span data-stu-id="59bf1-114">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="59bf1-115">這個未命名的命名空間，有時候是指全域命名空間，會出現在每個檔案中。</span><span class="sxs-lookup"><span data-stu-id="59bf1-115">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="59bf1-116">全域命名空間中的任何識別項都可用於具名命名空間中。</span><span class="sxs-lookup"><span data-stu-id="59bf1-116">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="59bf1-117">命名空間以隱含方式具有公用存取，且不可修改。</span><span class="sxs-lookup"><span data-stu-id="59bf1-117">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="59bf1-118">如需可在命名空間中指派給項目之存取修飾詞的討論，請參閱[存取修飾詞](access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="59bf1-118">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="59bf1-119">您可在兩個或多個宣告中定義命名空間。</span><span class="sxs-lookup"><span data-stu-id="59bf1-119">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="59bf1-120">例如，下例會將兩個類別定義為 `MyCompany` 命名空間的一部分︰</span><span class="sxs-lookup"><span data-stu-id="59bf1-120">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="59bf1-121">範例</span><span class="sxs-lookup"><span data-stu-id="59bf1-121">Example</span></span>

<span data-ttu-id="59bf1-122">下例顯示如何在巢狀命名空間中呼叫靜態方法。</span><span class="sxs-lookup"><span data-stu-id="59bf1-122">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="59bf1-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="59bf1-123">C# language specification</span></span>

<span data-ttu-id="59bf1-124">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[命名空間](~/_csharplang/spec/namespaces.md)一節。</span><span class="sxs-lookup"><span data-stu-id="59bf1-124">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59bf1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59bf1-125">See also</span></span>

- [<span data-ttu-id="59bf1-126">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="59bf1-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="59bf1-127">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="59bf1-127">C# keywords</span></span>](index.md)
- [<span data-ttu-id="59bf1-128">使用</span><span class="sxs-lookup"><span data-stu-id="59bf1-128">using</span></span>](using-directive.md)
- [<span data-ttu-id="59bf1-129">使用靜態</span><span class="sxs-lookup"><span data-stu-id="59bf1-129">using static</span></span>](using-static.md)
- [<span data-ttu-id="59bf1-130">命名空間別名限定詞 `::`</span><span class="sxs-lookup"><span data-stu-id="59bf1-130">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="59bf1-131">命名空間</span><span class="sxs-lookup"><span data-stu-id="59bf1-131">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
