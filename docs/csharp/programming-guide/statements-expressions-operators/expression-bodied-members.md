---
title: 運算式主體成員 - C# 程式設計指南
description: 瞭解運算式主體的成員。 請參閱使用屬性、函式、完成項和其他的運算式主體定義的程式碼範例。
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: e68e96e4aa3ff6a64590459a7197da1833e1a275
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381654"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="c617a-104">運算式主體成員 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c617a-104">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="c617a-105">運算式主體定義可讓您以極為簡潔且可讀的形式提供成員的實作。</span><span class="sxs-lookup"><span data-stu-id="c617a-105">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="c617a-106">只要任何所支援成員 (例如方法或屬性) 的邏輯包含單一運算式，就可以使用運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="c617a-106">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="c617a-107">運算式主體定義的一般語法如下︰</span><span class="sxs-lookup"><span data-stu-id="c617a-107">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="c617a-108">其中 *expression* 是有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="c617a-108">where *expression* is a valid expression.</span></span>

<span data-ttu-id="c617a-109">方法和唯讀屬性的運算式主體定義支援是在 C# 6 中引進，並在 C# 7.0 中擴充。</span><span class="sxs-lookup"><span data-stu-id="c617a-109">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="c617a-110">運算式主體定義可以與下表中所列的類型成員搭配使用︰</span><span class="sxs-lookup"><span data-stu-id="c617a-110">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="c617a-111">成員</span><span class="sxs-lookup"><span data-stu-id="c617a-111">Member</span></span>  |<span data-ttu-id="c617a-112">支援作為...</span><span class="sxs-lookup"><span data-stu-id="c617a-112">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="c617a-113">方法</span><span class="sxs-lookup"><span data-stu-id="c617a-113">Method</span></span>](#methods)  |<span data-ttu-id="c617a-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="c617a-114">C# 6</span></span> |
|[<span data-ttu-id="c617a-115">唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="c617a-115">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="c617a-116">C# 6</span><span class="sxs-lookup"><span data-stu-id="c617a-116">C# 6</span></span>  |
|[<span data-ttu-id="c617a-117">屬性</span><span class="sxs-lookup"><span data-stu-id="c617a-117">Property</span></span>](#properties)  |<span data-ttu-id="c617a-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="c617a-118">C# 7.0</span></span> |
|[<span data-ttu-id="c617a-119">函數</span><span class="sxs-lookup"><span data-stu-id="c617a-119">Constructor</span></span>](#constructors)   |<span data-ttu-id="c617a-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="c617a-120">C# 7.0</span></span> |
|[<span data-ttu-id="c617a-121">完成項</span><span class="sxs-lookup"><span data-stu-id="c617a-121">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="c617a-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="c617a-122">C# 7.0</span></span> |
|[<span data-ttu-id="c617a-123">索引子</span><span class="sxs-lookup"><span data-stu-id="c617a-123">Indexer</span></span>](#indexers)       |<span data-ttu-id="c617a-124">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="c617a-124">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="c617a-125">方法</span><span class="sxs-lookup"><span data-stu-id="c617a-125">Methods</span></span>

<span data-ttu-id="c617a-126">運算式主體方法包含傳回型別符合方法傳回型別之值的單一運算式，或是傳回可執行某項作業之 `void` 的方法。</span><span class="sxs-lookup"><span data-stu-id="c617a-126">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="c617a-127">例如，覆寫 <xref:System.Object.ToString%2A> 方法的類型通常會包括可傳回目前物件之字串表示的單一運算式。</span><span class="sxs-lookup"><span data-stu-id="c617a-127">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="c617a-128">下列範例定義 `Person` 類別，以將 <xref:System.Object.ToString%2A> 方法覆寫為運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="c617a-128">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="c617a-129">它也會定義 `DisplayName` 方法，以向主控台顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c617a-129">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="c617a-130">請注意，`return` 關鍵字未用於 `ToString` 運算式主體定義中。</span><span class="sxs-lookup"><span data-stu-id="c617a-130">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="c617a-131">如需詳細資訊，請參閱[方法 (C# 程式設計手冊)](../classes-and-structs/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="c617a-131">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="c617a-132">唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="c617a-132">Read-only properties</span></span>

<span data-ttu-id="c617a-133">從 C# 6 開始，您可以使用運算式主體定義來實作唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="c617a-133">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="c617a-134">若要這麼做，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="c617a-134">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="c617a-135">下列範例會定義 `Location` 類別，其唯讀 `Name` 屬性會實作為可傳回私用 `locationName` 欄位值的運算式主體定義：</span><span class="sxs-lookup"><span data-stu-id="c617a-135">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="c617a-136">如需屬性的詳細資訊，請參閱[屬性 (C# 程式設計手冊)](../classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c617a-136">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="c617a-137">屬性</span><span class="sxs-lookup"><span data-stu-id="c617a-137">Properties</span></span>

<span data-ttu-id="c617a-138">從 C# 7.0 開始，您可以使用運算式主體定義來實作屬性 `get` 和 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="c617a-138">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="c617a-139">下列範例示範如何進行這項操作：</span><span class="sxs-lookup"><span data-stu-id="c617a-139">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="c617a-140">如需屬性的詳細資訊，請參閱[屬性 (C# 程式設計手冊)](../classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c617a-140">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="c617a-141">建構函式</span><span class="sxs-lookup"><span data-stu-id="c617a-141">Constructors</span></span>

<span data-ttu-id="c617a-142">建構函式的運算式主體定義通常會包含單一指派運算式或方法呼叫，以處理建構函式的引數，或初始化執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="c617a-142">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="c617a-143">下列範例定義 `Location` 類別，這個類別的建構函式包含名為 *name* 的單一字串參數。</span><span class="sxs-lookup"><span data-stu-id="c617a-143">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="c617a-144">運算式主體定義會將引數指派給 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c617a-144">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="c617a-145">如需詳細資訊，請參閱[建構函式 (C# 程式設計手冊)](../classes-and-structs/constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="c617a-145">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="c617a-146">完成項</span><span class="sxs-lookup"><span data-stu-id="c617a-146">Finalizers</span></span>

<span data-ttu-id="c617a-147">完成項的運算式主體定義通常包含清除陳述式，例如，發行不受管理資源的陳述式。</span><span class="sxs-lookup"><span data-stu-id="c617a-147">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="c617a-148">下列範例定義完成項，以使用運算式主體定義來指出已呼叫完成項。</span><span class="sxs-lookup"><span data-stu-id="c617a-148">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="c617a-149">如需詳細資訊，請參閱[完成項 (C# 程式設計手冊)](../classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="c617a-149">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="c617a-150">索引子</span><span class="sxs-lookup"><span data-stu-id="c617a-150">Indexers</span></span>

<span data-ttu-id="c617a-151">如同屬性， `get` `set` 如果 `get` 存取子包含傳回值的單一運算式，或存取子執行簡單的指派，則索引子和存取子會包含運算式主體定義 `set` 。</span><span class="sxs-lookup"><span data-stu-id="c617a-151">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="c617a-152">下列範例會定義名為 `Sports` 的類別，這個類別包括內含數個運動名稱的內部 <xref:System.String> 陣列。</span><span class="sxs-lookup"><span data-stu-id="c617a-152">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="c617a-153">索引子 `get` 和 `set` 存取子都會實作為運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="c617a-153">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="c617a-154">如需詳細資訊，請參閱[索引子 (C# 程式設計手冊)](../indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c617a-154">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
