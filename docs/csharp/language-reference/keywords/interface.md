---
title: interface - C# 參考
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: b315d1f04c9e74700afba8ee7871b23ab4b2fd28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744687"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="81c4e-102">:::no-loc text="interface"::: （C#參考）</span><span class="sxs-lookup"><span data-stu-id="81c4e-102">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="81c4e-103">介面會定義合約。</span><span class="sxs-lookup"><span data-stu-id="81c4e-103">An interface defines a contract.</span></span> <span data-ttu-id="81c4e-104">任何執行該合約的[`class`](class.md)或[`struct`](struct.md)都必須提供在介面中定義之成員的實作為。</span><span class="sxs-lookup"><span data-stu-id="81c4e-104">Any [`class`](class.md) or [`struct`](struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="81c4e-105">從C# 8.0 開始，介面可能會定義成員的預設實值。</span><span class="sxs-lookup"><span data-stu-id="81c4e-105">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="81c4e-106">它也可以定義[`static`](static.md)成員，以便為一般功能提供單一的執行方式。</span><span class="sxs-lookup"><span data-stu-id="81c4e-106">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="81c4e-107">在下列範例中，類別 `ImplementationClass` 必須實作名為 `SampleMethod` 的方法，該方法沒有參數並會傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="81c4e-107">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="81c4e-108">如需詳細資訊與範例，請參閱[介面](../../programming-guide/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="81c4e-108">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="81c4e-109">範例</span><span class="sxs-lookup"><span data-stu-id="81c4e-109">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="81c4e-110">介面可以是命名空間或類別的成員。</span><span class="sxs-lookup"><span data-stu-id="81c4e-110">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="81c4e-111">介面宣告可以包含下列成員的宣告（不含任何執行的簽章）：</span><span class="sxs-lookup"><span data-stu-id="81c4e-111">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="81c4e-112">方法</span><span class="sxs-lookup"><span data-stu-id="81c4e-112">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="81c4e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="81c4e-113">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="81c4e-114">索引子</span><span class="sxs-lookup"><span data-stu-id="81c4e-114">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="81c4e-115">事件</span><span class="sxs-lookup"><span data-stu-id="81c4e-115">Events</span></span>](event.md)

<span data-ttu-id="81c4e-116">這些前面的成員宣告通常不會包含主體。</span><span class="sxs-lookup"><span data-stu-id="81c4e-116">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="81c4e-117">從C# 8.0 開始，介面成員可以宣告主體。</span><span class="sxs-lookup"><span data-stu-id="81c4e-117">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="81c4e-118">這稱為「*預設實值*」。</span><span class="sxs-lookup"><span data-stu-id="81c4e-118">This is called a *default implementation*.</span></span> <span data-ttu-id="81c4e-119">具有主體的成員允許介面為不提供覆寫實作為的類別和結構提供「預設」的執行。</span><span class="sxs-lookup"><span data-stu-id="81c4e-119">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="81c4e-120">此外，從C# 8.0 開始，介面可能包括：</span><span class="sxs-lookup"><span data-stu-id="81c4e-120">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="81c4e-121">常數</span><span class="sxs-lookup"><span data-stu-id="81c4e-121">Constants</span></span>](const.md)
- [<span data-ttu-id="81c4e-122">運算子</span><span class="sxs-lookup"><span data-stu-id="81c4e-122">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="81c4e-123">[靜態](../../programming-guide/classes-and-structs/constructors.md#static-constructors)的函式。</span><span class="sxs-lookup"><span data-stu-id="81c4e-123">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="81c4e-124">巢狀類型</span><span class="sxs-lookup"><span data-stu-id="81c4e-124">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="81c4e-125">靜態欄位、方法、屬性、索引子和事件</span><span class="sxs-lookup"><span data-stu-id="81c4e-125">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="81c4e-126">使用明確介面執行語法的成員宣告。</span><span class="sxs-lookup"><span data-stu-id="81c4e-126">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="81c4e-127">明確存取修飾詞（預設存取是[`public`](access-modifiers.md)）。</span><span class="sxs-lookup"><span data-stu-id="81c4e-127">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="81c4e-128">介面可能不包含實例狀態。</span><span class="sxs-lookup"><span data-stu-id="81c4e-128">Interfaces may not contain instance state.</span></span> <span data-ttu-id="81c4e-129">雖然現在允許靜態欄位，但介面中不允許實例欄位。</span><span class="sxs-lookup"><span data-stu-id="81c4e-129">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="81c4e-130">介面中不支援[實例 auto 屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)，因為它們會隱含宣告隱藏的欄位。</span><span class="sxs-lookup"><span data-stu-id="81c4e-130">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="81c4e-131">此規則對屬性宣告有細微的影響。</span><span class="sxs-lookup"><span data-stu-id="81c4e-131">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="81c4e-132">在介面宣告中，下列程式碼不會宣告自動實作用的屬性，就像在 `class` 或 `struct`中的一樣。</span><span class="sxs-lookup"><span data-stu-id="81c4e-132">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="81c4e-133">相反地，它會宣告沒有預設值的屬性，但必須在任何實作為介面的型別中執行：</span><span class="sxs-lookup"><span data-stu-id="81c4e-133">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="81c4e-134">介面可以繼承一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="81c4e-134">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="81c4e-135">當介面覆寫在基底介面中實[作為的方法](override.md)時，它必須使用[明確介面的實](../../programming-guide/interfaces/explicit-interface-implementation.md)語法。</span><span class="sxs-lookup"><span data-stu-id="81c4e-135">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="81c4e-136">當基底類型清單包含基底類別和介面時，基底類別一定會排在清單的第一個。</span><span class="sxs-lookup"><span data-stu-id="81c4e-136">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="81c4e-137">實作介面的類別能夠明確實作該介面的成員。</span><span class="sxs-lookup"><span data-stu-id="81c4e-137">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="81c4e-138">明確實作的成員不能經由類別執行個體存取，只能經由介面的執行個體來存取。</span><span class="sxs-lookup"><span data-stu-id="81c4e-138">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="81c4e-139">此外，預設介面成員只能透過介面的實例來存取。</span><span class="sxs-lookup"><span data-stu-id="81c4e-139">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="81c4e-140">如需明確介面執行的詳細資訊，請參閱[明確介面實](../../programming-guide/interfaces/explicit-interface-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="81c4e-140">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="81c4e-141">範例</span><span class="sxs-lookup"><span data-stu-id="81c4e-141">Example</span></span>

<span data-ttu-id="81c4e-142">下列範例示範介面實作。</span><span class="sxs-lookup"><span data-stu-id="81c4e-142">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="81c4e-143">在此範例中，介面包含屬性宣告，而類別包含實作。</span><span class="sxs-lookup"><span data-stu-id="81c4e-143">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="81c4e-144">實作 `IPoint` 的任何類別執行個體都有整數屬性 `x` 和 `y`。</span><span class="sxs-lookup"><span data-stu-id="81c4e-144">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="81c4e-145">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="81c4e-145">C# language specification</span></span>

<span data-ttu-id="81c4e-146">如需詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[介面](~/_csharplang/spec/interfaces.md)一節和[預設介面成員的功能規格- C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="81c4e-146">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="81c4e-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81c4e-147">See also</span></span>

- [<span data-ttu-id="81c4e-148">C# 參考</span><span class="sxs-lookup"><span data-stu-id="81c4e-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="81c4e-149">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="81c4e-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="81c4e-150">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="81c4e-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="81c4e-151">參考型別</span><span class="sxs-lookup"><span data-stu-id="81c4e-151">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="81c4e-152">介面</span><span class="sxs-lookup"><span data-stu-id="81c4e-152">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="81c4e-153">使用屬性</span><span class="sxs-lookup"><span data-stu-id="81c4e-153">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="81c4e-154">使用索引子</span><span class="sxs-lookup"><span data-stu-id="81c4e-154">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="81c4e-155">class</span><span class="sxs-lookup"><span data-stu-id="81c4e-155">class</span></span>](class.md)
- [<span data-ttu-id="81c4e-156">struct</span><span class="sxs-lookup"><span data-stu-id="81c4e-156">struct</span></span>](struct.md)
- [<span data-ttu-id="81c4e-157">介面</span><span class="sxs-lookup"><span data-stu-id="81c4e-157">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
