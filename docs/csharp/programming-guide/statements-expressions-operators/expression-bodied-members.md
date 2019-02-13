---
title: 運算式主體成員 - C# 程式設計指南
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7c282157639a6a60270ce8dbebbc91dd0e0a3f3
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826612"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="f2d1c-102">運算式主體成員 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f2d1c-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="f2d1c-103">運算式主體定義可讓您以極為簡潔且可讀的形式提供成員的實作。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="f2d1c-104">只要任何所支援成員 (例如方法或屬性) 的邏輯包含單一運算式，就可以使用運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="f2d1c-105">運算式主體定義的一般語法如下︰</span><span class="sxs-lookup"><span data-stu-id="f2d1c-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="f2d1c-106">其中 *expression* 是有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="f2d1c-107">方法和唯讀屬性的運算式主體定義支援是在 C# 6 中引進，並在 C# 7.0 中擴充。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="f2d1c-108">運算式主體定義可以與下表中所列的類型成員搭配使用︰</span><span class="sxs-lookup"><span data-stu-id="f2d1c-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="f2d1c-109">成員</span><span class="sxs-lookup"><span data-stu-id="f2d1c-109">Member</span></span>  |<span data-ttu-id="f2d1c-110">支援作為...</span><span class="sxs-lookup"><span data-stu-id="f2d1c-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="f2d1c-111">方法</span><span class="sxs-lookup"><span data-stu-id="f2d1c-111">Method</span></span>](#methods)  |<span data-ttu-id="f2d1c-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="f2d1c-112">C# 6</span></span> |
|[<span data-ttu-id="f2d1c-113">唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="f2d1c-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="f2d1c-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="f2d1c-114">C# 6</span></span>  |
|[<span data-ttu-id="f2d1c-115">Property</span><span class="sxs-lookup"><span data-stu-id="f2d1c-115">Property</span></span>](#properties)  |<span data-ttu-id="f2d1c-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="f2d1c-116">C# 7.0</span></span> |
|[<span data-ttu-id="f2d1c-117">建構函式</span><span class="sxs-lookup"><span data-stu-id="f2d1c-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="f2d1c-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="f2d1c-118">C# 7.0</span></span> |
|[<span data-ttu-id="f2d1c-119">完成項</span><span class="sxs-lookup"><span data-stu-id="f2d1c-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="f2d1c-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="f2d1c-120">C# 7.0</span></span> |
|[<span data-ttu-id="f2d1c-121">索引子</span><span class="sxs-lookup"><span data-stu-id="f2d1c-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="f2d1c-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="f2d1c-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="f2d1c-123">方法</span><span class="sxs-lookup"><span data-stu-id="f2d1c-123">Methods</span></span>

<span data-ttu-id="f2d1c-124">運算式主體方法包含傳回型別符合方法傳回型別之值的單一運算式，或是傳回可執行某項作業之 `void` 的方法。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="f2d1c-125">例如，覆寫 <xref:System.Object.ToString%2A> 方法的類型通常會包括可傳回目前物件之字串表示的單一運算式。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="f2d1c-126">下列範例定義 `Person` 類別，以將 <xref:System.Object.ToString%2A> 方法覆寫為運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="f2d1c-127">它也會定義 `DisplayName` 方法，以向主控台顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="f2d1c-128">請注意，`return` 關鍵字未用於 `ToString` 運算式主體定義中。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="f2d1c-129">如需詳細資訊，請參閱[方法 (C# 程式設計手冊)](../classes-and-structs/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="f2d1c-130">唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="f2d1c-130">Read-only properties</span></span>

<span data-ttu-id="f2d1c-131">從 C# 6 開始，您可以使用運算式主體定義來實作唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="f2d1c-132">若要這麼做，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="f2d1c-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="f2d1c-133">下列範例會定義 `Location` 類別，其唯讀 `Name` 屬性會實作為可傳回私用 `locationName` 欄位值的運算式主體定義：</span><span class="sxs-lookup"><span data-stu-id="f2d1c-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="f2d1c-134">如需屬性的詳細資訊，請參閱[屬性 (C# 程式設計手冊)](../classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="f2d1c-135">屬性</span><span class="sxs-lookup"><span data-stu-id="f2d1c-135">Properties</span></span>

<span data-ttu-id="f2d1c-136">從 C# 7.0 開始，您可以使用運算式主體定義來實作屬性 `get` 和 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="f2d1c-137">下列範例示範如何進行這項操作：</span><span class="sxs-lookup"><span data-stu-id="f2d1c-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="f2d1c-138">如需屬性的詳細資訊，請參閱[屬性 (C# 程式設計手冊)](../classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="f2d1c-139">建構函式</span><span class="sxs-lookup"><span data-stu-id="f2d1c-139">Constructors</span></span>

<span data-ttu-id="f2d1c-140">建構函式的運算式主體定義通常會包含單一指派運算式或方法呼叫，以處理建構函式的引數，或初始化執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="f2d1c-141">下列範例定義 `Location` 類別，這個類別的建構函式包含名為 *name* 的單一字串參數。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="f2d1c-142">運算式主體定義會將引數指派給 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="f2d1c-143">如需詳細資訊，請參閱[建構函式 (C# 程式設計手冊)](../classes-and-structs/constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="f2d1c-144">完成項</span><span class="sxs-lookup"><span data-stu-id="f2d1c-144">Finalizers</span></span>

<span data-ttu-id="f2d1c-145">完成項的運算式主體定義通常包含清除陳述式，例如，發行不受管理資源的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="f2d1c-146">下列範例定義完成項，以使用運算式主體定義來指出已呼叫完成項。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="f2d1c-147">如需詳細資訊，請參閱[完成項 (C# 程式設計手冊)](../classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="f2d1c-148">索引子</span><span class="sxs-lookup"><span data-stu-id="f2d1c-148">Indexers</span></span>

<span data-ttu-id="f2d1c-149">如同屬性，如果 get 存取子所包含的單一陳述式傳回值，或 set 存取子執行簡單指派，則索引子的 get 和 set 存取子會包含運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-149">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="f2d1c-150">下列範例會定義名為 `Sports` 的類別，這個類別包括內含數個運動名稱的內部 <xref:System.String> 陣列。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="f2d1c-151">索引子的 get 和 set 存取子會實作為運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-151">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="f2d1c-152">如需詳細資訊，請參閱[索引子 (C# 程式設計手冊)](../indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
