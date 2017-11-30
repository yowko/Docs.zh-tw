---
title: "在 C# 7.2 最新消息"
description: "7.2 C# 中的新功能的概觀。"
keywords: "C# 語言設計中，7.2，Visual Studio 2017，"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: a580a4a3a0a49e97ea8fb96699d1d978a9bc0a64
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="efb9b-104">在 C# 7.2 最新消息</span><span class="sxs-lookup"><span data-stu-id="efb9b-104">What's new in C# 7.2</span></span>

<span data-ttu-id="efb9b-105">C# 7.2 是另一個點發行，加入一些有用的功能。</span><span class="sxs-lookup"><span data-stu-id="efb9b-105">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="efb9b-106">這一版的一個佈景主題使用更有效率地實值類型，避免不必要的複本或配置。</span><span class="sxs-lookup"><span data-stu-id="efb9b-106">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span> 

<span data-ttu-id="efb9b-107">其餘的功能會很小，很好的功能。</span><span class="sxs-lookup"><span data-stu-id="efb9b-107">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="efb9b-108">使用 C# 7.2[語言版本選擇](csharp-7-1.md#language-version-selection)選取編譯器語言版本的組態項目。</span><span class="sxs-lookup"><span data-stu-id="efb9b-108">C# 7.2 uses the [language version selection](csharp-7-1.md#language-version-selection) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="efb9b-109">在此版本中的新語言功能包括：</span><span class="sxs-lookup"><span data-stu-id="efb9b-109">The new language features in this release are:</span></span>

* [<span data-ttu-id="efb9b-110">具有實值類型的參考語意</span><span class="sxs-lookup"><span data-stu-id="efb9b-110">Reference semantics with value types</span></span>](#reference-semantics-with-value-types)
  - <span data-ttu-id="efb9b-111">啟用使用參考語意的實值類型使用的語法改進項目組合。</span><span class="sxs-lookup"><span data-stu-id="efb9b-111">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="efb9b-112">非尾端的具名引數</span><span class="sxs-lookup"><span data-stu-id="efb9b-112">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="efb9b-113">具名引數後面可以接著位置引數。</span><span class="sxs-lookup"><span data-stu-id="efb9b-113">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="efb9b-114">數值常值中的前置底線</span><span class="sxs-lookup"><span data-stu-id="efb9b-114">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="efb9b-115">數值常值現在可以有任何列印的數字之前的前置底線。</span><span class="sxs-lookup"><span data-stu-id="efb9b-115">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="efb9b-116">`private protected`存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="efb9b-116">`private protected` access modifier</span></span>](#private-protected)
  - <span data-ttu-id="efb9b-117">`private protected`存取修飾詞可讓您在相同的組件中的衍生類別的存取。</span><span class="sxs-lookup"><span data-stu-id="efb9b-117">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>

## <a name="reference-semantics-with-value-types"></a><span data-ttu-id="efb9b-118">具有實值類型的參考語意</span><span class="sxs-lookup"><span data-stu-id="efb9b-118">Reference semantics with value types</span></span>

<span data-ttu-id="efb9b-119">7.2 中導入的語言功能可讓您使用實值型別時使用的參考語意。</span><span class="sxs-lookup"><span data-stu-id="efb9b-119">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="efb9b-120">它們被設計來提升效能，請將複製的實值類型而不會產生與使用參考類型相關聯的記憶體配置降到最低。</span><span class="sxs-lookup"><span data-stu-id="efb9b-120">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="efb9b-121">此功能包含：</span><span class="sxs-lookup"><span data-stu-id="efb9b-121">The features include:</span></span>

 - <span data-ttu-id="efb9b-122">`in`修飾詞來指定引數是傳址方式傳遞，但不是能修改以呼叫之方法的參數。</span><span class="sxs-lookup"><span data-stu-id="efb9b-122">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span>
 - <span data-ttu-id="efb9b-123">`ref readonly`方法傳回時，以指出方法傳址方式傳回其值，但不允許寫入該物件上的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="efb9b-123">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span>
 - <span data-ttu-id="efb9b-124">`readonly struct`宣告，以表示結構是不變，而且會傳遞做為`in`其成員方法的參數。</span><span class="sxs-lookup"><span data-stu-id="efb9b-124">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span>
 - <span data-ttu-id="efb9b-125">`ref struct`宣告，以指出結構類型會直接存取受管理的記憶體，且必須一律堆疊配置。</span><span class="sxs-lookup"><span data-stu-id="efb9b-125">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span>

<span data-ttu-id="efb9b-126">您可以閱讀更多個需所有這些變更中[使用實值型別參考語意](../reference-semantics-with-value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="efb9b-126">You can read more about all these changes in [Using value types with reference semantics](../reference-semantics-with-value-types.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="efb9b-127">非尾端的具名引數</span><span class="sxs-lookup"><span data-stu-id="efb9b-127">Non-trailing named arguments</span></span>

<span data-ttu-id="efb9b-128">方法會呼叫現在可以使用具名引數前面位置引數，這些具名引數時在正確的位置。</span><span class="sxs-lookup"><span data-stu-id="efb9b-128">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="efb9b-129">如需詳細資訊，請參閱[具名和選擇性引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="efb9b-129">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="efb9b-130">數值常值中的前置底線</span><span class="sxs-lookup"><span data-stu-id="efb9b-130">Leading underscores in numeric literals</span></span>

<span data-ttu-id="efb9b-131">不允許對 C# 7.0 中的數字分隔符號的支援實作`_`是常值的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="efb9b-131">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="efb9b-132">十六進位和二進位的數值常值可能會立即開始使用`_`。</span><span class="sxs-lookup"><span data-stu-id="efb9b-132">Hex and binary numeric literals may now begin with an `_`.</span></span> 

<span data-ttu-id="efb9b-133">例如: </span><span class="sxs-lookup"><span data-stu-id="efb9b-133">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

<span data-ttu-id="efb9b-134">最後，為新複合的存取修飾詞：`private protected`表示可能會由相同組件中宣告的衍生類別中存取成員。</span><span class="sxs-lookup"><span data-stu-id="efb9b-134">Finally, a new compound access modifier: `private protected` indicates that a member may be accessed by derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="efb9b-135">雖然`protected internal`可讓您存取由衍生的類別或類別，可位於相同的組件，`private protected`限制存取相同組件中宣告的衍生類型。</span><span class="sxs-lookup"><span data-stu-id="efb9b-135">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="efb9b-136">如需詳細資訊，請參閱[存取修飾詞](../language-reference/keywords/access-modifiers.md)語言參考中。</span><span class="sxs-lookup"><span data-stu-id="efb9b-136">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>
