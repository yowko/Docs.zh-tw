---
title: interface - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 2cb3121907b50d8151257739de0b66fcb597f364
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237892"
---
# <a name="interface-c-reference"></a><span data-ttu-id="b3f77-102">interface (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b3f77-102">interface (C# Reference)</span></span>

<span data-ttu-id="b3f77-103">介面只會包含[方法](../../programming-guide/classes-and-structs/methods.md)、[屬性](../../programming-guide/classes-and-structs/properties.md)、[事件](../../programming-guide/events/index.md)或[索引子](../../programming-guide/indexers/index.md)的簽章。</span><span class="sxs-lookup"><span data-stu-id="b3f77-103">An interface contains only the signatures of [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [events](../../programming-guide/events/index.md) or [indexers](../../programming-guide/indexers/index.md).</span></span> <span data-ttu-id="b3f77-104">實作介面的類別或結構必須實作在介面定義中指定的介面成員。</span><span class="sxs-lookup"><span data-stu-id="b3f77-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="b3f77-105">在下列範例中，類別 `ImplementationClass` 必須實作名為 `SampleMethod` 的方法，該方法沒有參數並會傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="b3f77-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="b3f77-106">如需詳細資訊與範例，請參閱[介面](../../programming-guide/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b3f77-106">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="b3f77-107">範例</span><span class="sxs-lookup"><span data-stu-id="b3f77-107">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="b3f77-108">介面可以是命名空間或類別的成員，而且可以包含下列成員的簽章：</span><span class="sxs-lookup"><span data-stu-id="b3f77-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>

- [<span data-ttu-id="b3f77-109">方法</span><span class="sxs-lookup"><span data-stu-id="b3f77-109">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="b3f77-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b3f77-110">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)

- [<span data-ttu-id="b3f77-111">索引子</span><span class="sxs-lookup"><span data-stu-id="b3f77-111">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)

- [<span data-ttu-id="b3f77-112">事件</span><span class="sxs-lookup"><span data-stu-id="b3f77-112">Events</span></span>](event.md)

<span data-ttu-id="b3f77-113">介面可以繼承一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="b3f77-113">An interface can inherit from one or more base interfaces.</span></span>

<span data-ttu-id="b3f77-114">當基底類型清單包含基底類別和介面時，基底類別一定會排在清單的第一個。</span><span class="sxs-lookup"><span data-stu-id="b3f77-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="b3f77-115">實作介面的類別能夠明確實作該介面的成員。</span><span class="sxs-lookup"><span data-stu-id="b3f77-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="b3f77-116">明確實作的成員不能經由類別執行個體存取，只能經由介面的執行個體來存取。</span><span class="sxs-lookup"><span data-stu-id="b3f77-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>

<span data-ttu-id="b3f77-117">如需明確介面實作的詳細資訊和程式碼範例，請參閱[明確介面實作](../../programming-guide/interfaces/explicit-interface-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="b3f77-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="b3f77-118">範例</span><span class="sxs-lookup"><span data-stu-id="b3f77-118">Example</span></span>

<span data-ttu-id="b3f77-119">下列範例示範介面實作。</span><span class="sxs-lookup"><span data-stu-id="b3f77-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="b3f77-120">在此範例中，介面包含屬性宣告，而類別包含實作。</span><span class="sxs-lookup"><span data-stu-id="b3f77-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="b3f77-121">實作 `IPoint` 的任何類別執行個體都有整數屬性 `x` 和 `y`。</span><span class="sxs-lookup"><span data-stu-id="b3f77-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="b3f77-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b3f77-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b3f77-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3f77-123">See also</span></span>

- [<span data-ttu-id="b3f77-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b3f77-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b3f77-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b3f77-125">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="b3f77-126">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="b3f77-126">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="b3f77-127">參考型別</span><span class="sxs-lookup"><span data-stu-id="b3f77-127">Reference Types</span></span>](reference-types.md)  
- [<span data-ttu-id="b3f77-128">介面</span><span class="sxs-lookup"><span data-stu-id="b3f77-128">Interfaces</span></span>](../../programming-guide/interfaces/index.md)  
- [<span data-ttu-id="b3f77-129">使用屬性</span><span class="sxs-lookup"><span data-stu-id="b3f77-129">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)  
- [<span data-ttu-id="b3f77-130">使用索引子</span><span class="sxs-lookup"><span data-stu-id="b3f77-130">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)  
- [<span data-ttu-id="b3f77-131">class</span><span class="sxs-lookup"><span data-stu-id="b3f77-131">class</span></span>](class.md)  
- [<span data-ttu-id="b3f77-132">struct</span><span class="sxs-lookup"><span data-stu-id="b3f77-132">struct</span></span>](struct.md)  
- [<span data-ttu-id="b3f77-133">介面</span><span class="sxs-lookup"><span data-stu-id="b3f77-133">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
