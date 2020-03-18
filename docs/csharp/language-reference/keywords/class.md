---
title: class 關鍵字 - C# 參考
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 500160d3bc9280b866e5f5ba24c5edc623e752c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673091"
---
# <a name="class-c-reference"></a><span data-ttu-id="4ab22-102">類別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4ab22-102">class (C# Reference)</span></span>

<span data-ttu-id="4ab22-103">使用 `class` 關鍵字宣告類別，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="4ab22-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="4ab22-104">備註</span><span class="sxs-lookup"><span data-stu-id="4ab22-104">Remarks</span></span>

<span data-ttu-id="4ab22-105">僅允許在 C# 中使用單一繼承。</span><span class="sxs-lookup"><span data-stu-id="4ab22-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="4ab22-106">換句話說，類別可以只從一個基底類別繼承實作。</span><span class="sxs-lookup"><span data-stu-id="4ab22-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="4ab22-107">不過，類別可以實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="4ab22-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="4ab22-108">下表顯示類別繼承和介面實作範例︰</span><span class="sxs-lookup"><span data-stu-id="4ab22-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="4ab22-109">繼承</span><span class="sxs-lookup"><span data-stu-id="4ab22-109">Inheritance</span></span>|<span data-ttu-id="4ab22-110">範例</span><span class="sxs-lookup"><span data-stu-id="4ab22-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="4ab22-111">None</span><span class="sxs-lookup"><span data-stu-id="4ab22-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="4ab22-112">Single</span><span class="sxs-lookup"><span data-stu-id="4ab22-112">Single</span></span>|`class DerivedClass : BaseClass { }`|
|<span data-ttu-id="4ab22-113">無，實作兩個介面</span><span class="sxs-lookup"><span data-stu-id="4ab22-113">None, implements two interfaces</span></span>|`class ImplClass : IFace1, IFace2 { }`|
|<span data-ttu-id="4ab22-114">單一，實作一個介面</span><span class="sxs-lookup"><span data-stu-id="4ab22-114">Single, implements one interface</span></span>|`class ImplDerivedClass : BaseClass, IFace1 { }`|

<span data-ttu-id="4ab22-115">直接在命名空間內宣告的類別 (未巢狀在其他類別內) 可以是 [public](./public.md) 或 [internal](./internal.md)。</span><span class="sxs-lookup"><span data-stu-id="4ab22-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="4ab22-116">類別預設為 `internal`。</span><span class="sxs-lookup"><span data-stu-id="4ab22-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="4ab22-117">類別成員 (包含巢狀類別) 可以是 [public](public.md)、[protected internal](protected-internal.md)、[protected](protected.md)、[internal](internal.md)、[private](private.md) 或 [private protected](private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="4ab22-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="4ab22-118">成員預設是 `private`。</span><span class="sxs-lookup"><span data-stu-id="4ab22-118">Members are `private` by default.</span></span>

<span data-ttu-id="4ab22-119">如需詳細資訊，請參閱[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="4ab22-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="4ab22-120">您可以宣告具有型別參數的泛型類別。</span><span class="sxs-lookup"><span data-stu-id="4ab22-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="4ab22-121">如需詳細資訊，請參閱[泛型類別](../../programming-guide/generics/generic-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="4ab22-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="4ab22-122">類別可以包含下列成員的宣告︰</span><span class="sxs-lookup"><span data-stu-id="4ab22-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="4ab22-123">建構函式</span><span class="sxs-lookup"><span data-stu-id="4ab22-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="4ab22-124">常數</span><span class="sxs-lookup"><span data-stu-id="4ab22-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="4ab22-125">領域</span><span class="sxs-lookup"><span data-stu-id="4ab22-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="4ab22-126">完成項</span><span class="sxs-lookup"><span data-stu-id="4ab22-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="4ab22-127">方法</span><span class="sxs-lookup"><span data-stu-id="4ab22-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="4ab22-128">屬性</span><span class="sxs-lookup"><span data-stu-id="4ab22-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="4ab22-129">索引子</span><span class="sxs-lookup"><span data-stu-id="4ab22-129">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="4ab22-130">運營商</span><span class="sxs-lookup"><span data-stu-id="4ab22-130">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="4ab22-131">事件</span><span class="sxs-lookup"><span data-stu-id="4ab22-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="4ab22-132">委派</span><span class="sxs-lookup"><span data-stu-id="4ab22-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="4ab22-133">類</span><span class="sxs-lookup"><span data-stu-id="4ab22-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="4ab22-134">介面</span><span class="sxs-lookup"><span data-stu-id="4ab22-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="4ab22-135">結構類型</span><span class="sxs-lookup"><span data-stu-id="4ab22-135">Structure types</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="4ab22-136">枚舉類型</span><span class="sxs-lookup"><span data-stu-id="4ab22-136">Enumeration types</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="4ab22-137">範例</span><span class="sxs-lookup"><span data-stu-id="4ab22-137">Example</span></span>

<span data-ttu-id="4ab22-138">下列範例示範如何宣告類別欄位、建構函式和方法。</span><span class="sxs-lookup"><span data-stu-id="4ab22-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="4ab22-139">它也會示範物件具現化和列印執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="4ab22-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="4ab22-140">在此範例中，宣告兩個類別。</span><span class="sxs-lookup"><span data-stu-id="4ab22-140">In this example, two classes are declared.</span></span> <span data-ttu-id="4ab22-141">第一個類別 `Child`，包含兩個私用欄位 (`name` 和 `age`)、兩個公用建構函式和一個公用方法。</span><span class="sxs-lookup"><span data-stu-id="4ab22-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="4ab22-142">第二個類別 `StringTest` 是用來包含 `Main`。</span><span class="sxs-lookup"><span data-stu-id="4ab22-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="4ab22-143">註解</span><span class="sxs-lookup"><span data-stu-id="4ab22-143">Comments</span></span>

<span data-ttu-id="4ab22-144">請注意，在上述範例中，只能透過 `Child` 類別的公用方法來存取私用欄位 (`name` 和 `age`)。</span><span class="sxs-lookup"><span data-stu-id="4ab22-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="4ab22-145">例如，您無法使用如下的陳述式，從 `Main` 方法列印子系的名稱︰</span><span class="sxs-lookup"><span data-stu-id="4ab22-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="4ab22-146">只有在 `Main` 已是類別的成員時，才能從 `Main` 存取 `Child` 的 private 成員。</span><span class="sxs-lookup"><span data-stu-id="4ab22-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="4ab22-147">類型已宣告在存取修飾詞未預設為 `private` 的類別內，因此，如果已移除關鍵字，則此範例中的資料成員仍然會是 `private`。</span><span class="sxs-lookup"><span data-stu-id="4ab22-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="4ab22-148">最後，請注意到針對使用無參數建構函式 (`child3`) 建立的物件，`age` 欄位預設已初始化為零。</span><span class="sxs-lookup"><span data-stu-id="4ab22-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4ab22-149">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4ab22-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4ab22-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ab22-150">See also</span></span>

- [<span data-ttu-id="4ab22-151">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4ab22-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4ab22-152">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4ab22-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4ab22-153">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="4ab22-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4ab22-154">參考類型</span><span class="sxs-lookup"><span data-stu-id="4ab22-154">Reference Types</span></span>](./reference-types.md)
