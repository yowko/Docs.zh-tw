---
title: interface - C# 參考
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625848"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="c9ab6-102">:::no-loc text="interface":::（C# 參考）</span><span class="sxs-lookup"><span data-stu-id="c9ab6-102">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="c9ab6-103">介面定義協定。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-103">An interface defines a contract.</span></span> <span data-ttu-id="c9ab6-104">任何[`class`](class.md)或[`struct`](../builtin-types/struct.md)實現該協定都必須提供介面中定義的成員的實現。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-104">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="c9ab6-105">從 C# 8.0 開始，介面可以定義成員的預設實現。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-105">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="c9ab6-106">它還可以定義[`static`](static.md)成員，以便為通用功能提供單個實現。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-106">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="c9ab6-107">在下列範例中，類別 `ImplementationClass` 必須實作名為 `SampleMethod` 的方法，該方法沒有參數並會傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-107">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="c9ab6-108">如需詳細資訊與範例，請參閱[介面](../../programming-guide/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-108">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="c9ab6-109">範例</span><span class="sxs-lookup"><span data-stu-id="c9ab6-109">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="c9ab6-110">介面可以是命名空間或類的成員。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-110">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="c9ab6-111">介面聲明可以包含以下成員的聲明（沒有任何實現的簽名）：</span><span class="sxs-lookup"><span data-stu-id="c9ab6-111">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="c9ab6-112">方法</span><span class="sxs-lookup"><span data-stu-id="c9ab6-112">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="c9ab6-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c9ab6-113">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="c9ab6-114">索引子</span><span class="sxs-lookup"><span data-stu-id="c9ab6-114">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="c9ab6-115">事件</span><span class="sxs-lookup"><span data-stu-id="c9ab6-115">Events</span></span>](event.md)

<span data-ttu-id="c9ab6-116">上述成員聲明通常不包含正文。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-116">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="c9ab6-117">從 C# 8.0 開始，介面成員可以聲明正文。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-117">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="c9ab6-118">這稱為*預設實現*。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-118">This is called a *default implementation*.</span></span> <span data-ttu-id="c9ab6-119">具有正文的成員允許介面為不提供重寫實現的類和結構提供"預設"實現。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-119">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="c9ab6-120">此外，從 C# 8.0 開始，介面可能包括：</span><span class="sxs-lookup"><span data-stu-id="c9ab6-120">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="c9ab6-121">常數</span><span class="sxs-lookup"><span data-stu-id="c9ab6-121">Constants</span></span>](const.md)
- [<span data-ttu-id="c9ab6-122">運營商</span><span class="sxs-lookup"><span data-stu-id="c9ab6-122">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="c9ab6-123">[靜態建構函式](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="c9ab6-123">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="c9ab6-124">巢狀型別</span><span class="sxs-lookup"><span data-stu-id="c9ab6-124">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="c9ab6-125">靜態欄位、方法、屬性、索引子和事件</span><span class="sxs-lookup"><span data-stu-id="c9ab6-125">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="c9ab6-126">使用明確介面實作語法的成員聲明。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-126">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="c9ab6-127">顯式訪問修改器（預設訪問為[`public`](access-modifiers.md)）。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-127">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="c9ab6-128">介面可能不包含實例狀態。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-128">Interfaces may not contain instance state.</span></span> <span data-ttu-id="c9ab6-129">雖然現在允許靜態欄位，但介面中不允許實例欄位。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-129">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="c9ab6-130">[介面中不支援實例自動屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)，因為它們會隱式聲明隱藏欄位。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-130">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="c9ab6-131">此規則對屬性聲明有微妙的影響。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-131">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="c9ab6-132">在介面聲明中，以下代碼不聲明自動實現的屬性，就像它在`class`或 中`struct`那樣。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-132">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="c9ab6-133">相反，它聲明一個屬性，該屬性沒有預設實現，但必須以實現介面的任何類型的實現：</span><span class="sxs-lookup"><span data-stu-id="c9ab6-133">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="c9ab6-134">介面可以繼承一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-134">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="c9ab6-135">當介面重寫在基介面中實現[的方法時](override.md)，它必須使用[明確介面實作](../../programming-guide/interfaces/explicit-interface-implementation.md)語法。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-135">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="c9ab6-136">當基底類型清單包含基底類別和介面時，基底類別一定會排在清單的第一個。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-136">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="c9ab6-137">實作介面的類別能夠明確實作該介面的成員。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-137">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="c9ab6-138">明確實作的成員不能經由類別執行個體存取，只能經由介面的執行個體來存取。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-138">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="c9ab6-139">此外，預設介面成員只能通過介面的實例進行訪問。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-139">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="c9ab6-140">有關明確介面實作的詳細資訊，請參閱[明確介面實作](../../programming-guide/interfaces/explicit-interface-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-140">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="c9ab6-141">範例</span><span class="sxs-lookup"><span data-stu-id="c9ab6-141">Example</span></span>

<span data-ttu-id="c9ab6-142">下列範例示範介面實作。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-142">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="c9ab6-143">在此範例中，介面包含屬性宣告，而類別包含實作。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-143">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="c9ab6-144">實作 `IPoint` 的任何類別執行個體都有整數屬性 `x` 和 `y`。</span><span class="sxs-lookup"><span data-stu-id="c9ab6-144">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="c9ab6-145">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c9ab6-145">C# language specification</span></span>

<span data-ttu-id="c9ab6-146">有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[介面](~/_csharplang/spec/interfaces.md)部分和預設介面成員的功能規格[- C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="c9ab6-146">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="c9ab6-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9ab6-147">See also</span></span>

- [<span data-ttu-id="c9ab6-148">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c9ab6-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c9ab6-149">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c9ab6-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c9ab6-150">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c9ab6-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c9ab6-151">參考類型</span><span class="sxs-lookup"><span data-stu-id="c9ab6-151">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="c9ab6-152">介面</span><span class="sxs-lookup"><span data-stu-id="c9ab6-152">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="c9ab6-153">使用屬性</span><span class="sxs-lookup"><span data-stu-id="c9ab6-153">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="c9ab6-154">使用索引子</span><span class="sxs-lookup"><span data-stu-id="c9ab6-154">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="c9ab6-155">介面</span><span class="sxs-lookup"><span data-stu-id="c9ab6-155">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
