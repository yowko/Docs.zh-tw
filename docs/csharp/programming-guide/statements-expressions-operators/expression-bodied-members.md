---
title: "運算式主體成員 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: b77f656d36dc4f0a715755e13bfcd6c3515c697b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/15/2017

---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="b5989-102">運算式主體成員 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b5989-102">Expression-bodied members (C# programming guide)</span></span>
<span data-ttu-id="b5989-103">運算式主體定義可讓您以極為簡潔且可讀的形式提供成員的實作。</span><span class="sxs-lookup"><span data-stu-id="b5989-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="b5989-104">只要任何所支援成員 (例如方法或屬性) 的邏輯包含單一運算式，就可以使用運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="b5989-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="b5989-105">運算式主體定義的一般語法如下︰</span><span class="sxs-lookup"><span data-stu-id="b5989-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="b5989-106">其中 *expression* 是有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="b5989-106">where *expression* is a valid expression.</span></span> 

<span data-ttu-id="b5989-107">方法和屬性 get 存取子的運算式主體定義支援是在 C# 6 中引進，並在 C# 7 中擴充。</span><span class="sxs-lookup"><span data-stu-id="b5989-107">Support for expression body definitions was introduced for methods and property get accessors in C# 6 and was expanded in C# 7.</span></span> <span data-ttu-id="b5989-108">運算式主體定義可以與下表中所列的類型成員搭配使用︰</span><span class="sxs-lookup"><span data-stu-id="b5989-108">Expression body definitions can be used with the type members listed in the following table:</span></span> 

|<span data-ttu-id="b5989-109">成員</span><span class="sxs-lookup"><span data-stu-id="b5989-109">Member</span></span>  |<span data-ttu-id="b5989-110">支援作為...</span><span class="sxs-lookup"><span data-stu-id="b5989-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="b5989-111">方法</span><span class="sxs-lookup"><span data-stu-id="b5989-111">Method</span></span>](#methods)  |<span data-ttu-id="b5989-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="b5989-112">C# 6</span></span> |
|[<span data-ttu-id="b5989-113">建構函式</span><span class="sxs-lookup"><span data-stu-id="b5989-113">Constructor</span></span>](#constructors)   |<span data-ttu-id="b5989-114">C# 7</span><span class="sxs-lookup"><span data-stu-id="b5989-114">C# 7</span></span> |
|[<span data-ttu-id="b5989-115">完成項</span><span class="sxs-lookup"><span data-stu-id="b5989-115">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="b5989-116">C# 7</span><span class="sxs-lookup"><span data-stu-id="b5989-116">C# 7</span></span> |
|[<span data-ttu-id="b5989-117">屬性 Get</span><span class="sxs-lookup"><span data-stu-id="b5989-117">Property Get</span></span>](#property-get-statements)  |<span data-ttu-id="b5989-118">C# 6</span><span class="sxs-lookup"><span data-stu-id="b5989-118">C# 6</span></span> |
|[<span data-ttu-id="b5989-119">屬性 Set</span><span class="sxs-lookup"><span data-stu-id="b5989-119">Property Set</span></span>](#property-set-statements)  |<span data-ttu-id="b5989-120">C# 7</span><span class="sxs-lookup"><span data-stu-id="b5989-120">C# 7</span></span> |
|[<span data-ttu-id="b5989-121">索引子</span><span class="sxs-lookup"><span data-stu-id="b5989-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="b5989-122">C# 7</span><span class="sxs-lookup"><span data-stu-id="b5989-122">C# 7</span></span> |

## <a name="methods"></a><span data-ttu-id="b5989-123">方法</span><span class="sxs-lookup"><span data-stu-id="b5989-123">Methods</span></span>

<span data-ttu-id="b5989-124">運算式主體方法包含傳回型別符合方法傳回型別之值的單一運算式，或是傳回可執行某項作業之 `void` 的方法。</span><span class="sxs-lookup"><span data-stu-id="b5989-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="b5989-125">例如，覆寫 <xref:System.Object.ToString%2A> 方法的類型通常會包括可傳回目前物件之字串表示的單一運算式。</span><span class="sxs-lookup"><span data-stu-id="b5989-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span> 

<span data-ttu-id="b5989-126">下列範例定義 `Person` 類別，以將 <xref:System.Object.ToString%2A> 方法覆寫為運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="b5989-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="b5989-127">它也會定義 `Show` 方法，以向主控台顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="b5989-127">It also defines a `Show` method that displays a name to the console.</span></span> <span data-ttu-id="b5989-128">請注意，`return` 關鍵字未用於 `ToString` 運算式主體定義中。</span><span class="sxs-lookup"><span data-stu-id="b5989-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

<span data-ttu-id="b5989-129">[!code-cs[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]</span><span class="sxs-lookup"><span data-stu-id="b5989-129">[!code-cs[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]</span></span>  

<span data-ttu-id="b5989-130">如需詳細資訊，請參閱[方法 (C# 程式設計手冊)](../classes-and-structs/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="b5989-130">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>
 
## <a name="constructors"></a><span data-ttu-id="b5989-131">建構函式</span><span class="sxs-lookup"><span data-stu-id="b5989-131">Constructors</span></span>

<span data-ttu-id="b5989-132">建構函式的運算式主體定義通常會包含單一指派運算式或方法呼叫，以處理建構函式的引數，或初始化執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="b5989-132">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span> 

<span data-ttu-id="b5989-133">下列範例定義 `Location` 類別，這個類別的建構函式包含名為 *name* 的單一字串參數。</span><span class="sxs-lookup"><span data-stu-id="b5989-133">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="b5989-134">運算式主體定義會將引數指派給 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b5989-134">The expression body definition assigns the argument to the `Name` property.</span></span>

<span data-ttu-id="b5989-135">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="b5989-135">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span></span>  

<span data-ttu-id="b5989-136">如需詳細資訊，請參閱[建構函式 (C# 程式設計手冊)](../classes-and-structs/constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="b5989-136">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="b5989-137">完成項</span><span class="sxs-lookup"><span data-stu-id="b5989-137">Finalizers</span></span>

<span data-ttu-id="b5989-138">完成項的運算式主體定義通常包含清除陳述式，例如，發行不受管理資源的陳述式。</span><span class="sxs-lookup"><span data-stu-id="b5989-138">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="b5989-139">下列範例定義完成項，以使用運算式主體定義來指出已呼叫完成項。</span><span class="sxs-lookup"><span data-stu-id="b5989-139">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

<span data-ttu-id="b5989-140">[!code-cs[運算式主體完成項](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="b5989-140">[!code-cs[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]</span></span>  

<span data-ttu-id="b5989-141">如需詳細資訊，請參閱[完成項 (C# 程式設計手冊)](../classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="b5989-141">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="property-get-statements"></a><span data-ttu-id="b5989-142">屬性 get 陳述式</span><span class="sxs-lookup"><span data-stu-id="b5989-142">Property get statements</span></span>

<span data-ttu-id="b5989-143">如果您選擇自行實作屬性 get 存取子，則可以使用單一運算式的運算式主體定義，而單一運算式只會傳回屬性值。</span><span class="sxs-lookup"><span data-stu-id="b5989-143">If you choose to implement a property get accessor yourself, you can use an expression body definition for single expressions that simply return the property value.</span></span> <span data-ttu-id="b5989-144">請注意，不會使用 `return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b5989-144">Note that the `return` statement isn't used.</span></span>

<span data-ttu-id="b5989-145">下列範例會定義 `Location.Name` 屬性，這個屬性的屬性 get 存取子會傳回支援這個屬性的私用 `locationName` 欄位值。</span><span class="sxs-lookup"><span data-stu-id="b5989-145">The following example defines a `Location.Name` property whose property get accessor returns the value of the private `locationName` field that backs the property.</span></span> 

<span data-ttu-id="b5989-146">[!code-cs[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="b5989-146">[!code-cs[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span></span>  

<span data-ttu-id="b5989-147">您可以實作使用運算式主體定義的唯讀屬性，而不需要明確 `set` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b5989-147">Read-only properties that use an expression body definition can be implemented without an explicit `set` statement.</span></span> <span data-ttu-id="b5989-148">其語法為：</span><span class="sxs-lookup"><span data-stu-id="b5989-148">The syntax is:</span></span>

```csharp
PropertyName => returnValue;
```

<span data-ttu-id="b5989-149">下列範例會定義 `Location` 類別，這個類別的唯讀 `Name` 屬性實作為可傳回私用 `locationName` 欄位值的運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="b5989-149">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field.</span></span>

<span data-ttu-id="b5989-150">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="b5989-150">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]</span></span>  

<span data-ttu-id="b5989-151">如需詳細資訊，請參閱[屬性 (C# 程式設計手冊)](../classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b5989-151">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="property-set-statements"></a><span data-ttu-id="b5989-152">屬性 set 陳述式</span><span class="sxs-lookup"><span data-stu-id="b5989-152">Property set statements</span></span>

<span data-ttu-id="b5989-153">如果您選擇自行實作屬性 set 存取子，則可以使用單行運算式的運算式主體定義，而單行運算式會將值指派給支援此屬性的欄位。</span><span class="sxs-lookup"><span data-stu-id="b5989-153">If you choose to implement a property set accessor yourself, you can use an expression body definition for a single-line expression that assigns a value to the field that backs the property.</span></span>

<span data-ttu-id="b5989-154">下列範例會定義 `Location.Name` 屬性，這個屬性的屬性 set 陳述式會將其輸入引數指派給支援這個屬性的私用 `locationName` 欄位。</span><span class="sxs-lookup"><span data-stu-id="b5989-154">The following example defines a `Location.Name` property whose property set statement assigns its input argument to the private `locationName` field that backs the property.</span></span>

<span data-ttu-id="b5989-155">[!code-cs[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="b5989-155">[!code-cs[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span></span>  

<span data-ttu-id="b5989-156">如需詳細資訊，請參閱[屬性 (C# 程式設計手冊)](../classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b5989-156">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="b5989-157">索引子</span><span class="sxs-lookup"><span data-stu-id="b5989-157">Indexers</span></span>

<span data-ttu-id="b5989-158">如同屬性，如果 get 存取子所包含的單一陳述式傳回值，或 set 存取子執行簡單指派，則索引子的 get 和 set 存取子會包含運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="b5989-158">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="b5989-159">下列範例會定義名為 `Sports` 的類別，這個類別包括內含數個運動名稱的內部 <xref:System.String> 陣列。</span><span class="sxs-lookup"><span data-stu-id="b5989-159">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="b5989-160">索引子的 get 和 set 存取子會實作為運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="b5989-160">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

<span data-ttu-id="b5989-161">[!code-cs[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="b5989-161">[!code-cs[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]</span></span> 

<span data-ttu-id="b5989-162">如需詳細資訊，請參閱[索引子 (C# 程式設計手冊)](../indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b5989-162">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>


