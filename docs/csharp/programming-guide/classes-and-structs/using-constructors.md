---
title: 使用建構函式 - C# 程式設計手冊
description: '此範例示範如何在 c # 中使用 new 運算子來具現化類別。 在為新物件配置記憶體之後，會叫用簡單的函式。'
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 161c243f16f6705fa8fcf79360f92a74e4d0b27b
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899252"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="7465c-104">使用建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="7465c-104">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="7465c-105">建立[類別](../../language-reference/keywords/class.md)或[結構](../../language-reference/builtin-types/struct.md)時，會呼叫其建構函式。</span><span class="sxs-lookup"><span data-stu-id="7465c-105">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="7465c-106">建構函式的名稱與類別或結構相同，而且通常會初始化新物件的資料成員。</span><span class="sxs-lookup"><span data-stu-id="7465c-106">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="7465c-107">在下列範例中，使用一個簡單的建構函式定義名為 `Taxi` 的類別。</span><span class="sxs-lookup"><span data-stu-id="7465c-107">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="7465c-108">然後使用 [new](../../language-reference/operators/new-operator.md) 運算子具現化此類別。</span><span class="sxs-lookup"><span data-stu-id="7465c-108">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="7465c-109">為新物件配置記憶體之後，`new` 運算子會立即叫用 `Taxi` 建構函式。</span><span class="sxs-lookup"><span data-stu-id="7465c-109">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[TaxiExample#1](snippets/using-constructors/Program.cs#1)]
  
 <span data-ttu-id="7465c-110">不接受任何參數的建構函式稱為「無參數建構函式」。</span><span class="sxs-lookup"><span data-stu-id="7465c-110">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="7465c-111">每當使用 `new` 運算子來具現化物件，而且未提供引數給 `new` 時，便會叫用無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="7465c-111">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="7465c-112">如需詳細資訊，請參閱[執行個體建構函式](./instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="7465c-112">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="7465c-113">除非類別是[靜態](../../language-reference/keywords/static.md)，否則沒有建構函式的類別會從 C# 編譯器取得一個公開無參數建構函式，以啟用類別具現化。</span><span class="sxs-lookup"><span data-stu-id="7465c-113">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="7465c-114">如需詳細資訊，請參閱 [靜態類別和靜態類別成員](./static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="7465c-114">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="7465c-115">您可以將建構函式設為私用，避免具現化類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7465c-115">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[PrivateConstructor#2](snippets/using-constructors/Program.cs#2)]
  
 <span data-ttu-id="7465c-116">如需詳細資訊，請參閱 [私用建構函式](./private-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="7465c-116">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="7465c-117">[結構](../../language-reference/builtin-types/struct.md)型別的建構函式與類別建構函式相似，但 `structs` 無法包含明確的無參數建構函式，因為編譯器會自動提供一個。</span><span class="sxs-lookup"><span data-stu-id="7465c-117">Constructors for [struct](../../language-reference/builtin-types/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="7465c-118">這個函式會將中的每個欄位初始化 `struct` 為 [預設值](../../language-reference/builtin-types/default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="7465c-118">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="7465c-119">但是，這個無參數建構函式只會在使用 `new` 具現化 `struct` 時叫用。</span><span class="sxs-lookup"><span data-stu-id="7465c-119">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="7465c-120">例如，此程式碼使用 <xref:System.Int32> 的無參數建構函式，因此您可以保證該整數已進行初始化：</span><span class="sxs-lookup"><span data-stu-id="7465c-120">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="7465c-121">不過，下列程式碼由於未使用 `new`，而且會嘗試使用尚未初始化的物件，因此會造成編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="7465c-121">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="7465c-122">或者，您可以初始化或指派以 `structs` 為基礎的物件 (包括所有內建數字類型)，再如下列範例所示使用這些物件：</span><span class="sxs-lookup"><span data-stu-id="7465c-122">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="7465c-123">因此您不需要呼叫實值型別的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="7465c-123">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="7465c-124">類別和 `structs` 都可以定義使用參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="7465c-124">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="7465c-125">使用參數的建構函式必須透過 `new` 陳述式或 [base](../../language-reference/keywords/base.md) 陳述式呼叫。</span><span class="sxs-lookup"><span data-stu-id="7465c-125">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="7465c-126">類別和 `structs` 也可以定義多個建構函式，且皆無須定義無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="7465c-126">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="7465c-127">例如：</span><span class="sxs-lookup"><span data-stu-id="7465c-127">For example:</span></span>  
  
 [!code-csharp[EmployeeExample#3](snippets/using-constructors/Program.cs#3)]
  
 <span data-ttu-id="7465c-128">使用下列任一陳述式即可建立此類別：</span><span class="sxs-lookup"><span data-stu-id="7465c-128">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[InstantiatingEmployeeConstructors#4](snippets/using-constructors/Program.cs#4)]
  
 <span data-ttu-id="7465c-129">建構函式可以使用 `base` 關鍵字呼叫基底類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="7465c-129">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="7465c-130">例如：</span><span class="sxs-lookup"><span data-stu-id="7465c-130">For example:</span></span>  
  
 [!code-csharp[ManagerInheritingEmployee#5](snippets/using-constructors/Program.cs#5)]
  
 <span data-ttu-id="7465c-131">在此範例中，執行建構函式的區塊之前，會先呼叫基底類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="7465c-131">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="7465c-132">不論是否有參數，都可以使用 `base` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7465c-132">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="7465c-133">建構函式的任何參數都可以作為 `base` 的參數使用，或作為運算式的一部分使用。</span><span class="sxs-lookup"><span data-stu-id="7465c-133">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="7465c-134">如需詳細資訊，請參閱 [base](../../language-reference/keywords/base.md)。</span><span class="sxs-lookup"><span data-stu-id="7465c-134">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="7465c-135">在衍生類別中，如果未使用 `base` 關鍵字明確呼叫基底類別建構函式，則會隱含呼叫無參數建構函式 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="7465c-135">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="7465c-136">這表示下列建構函式宣告的作用相同：</span><span class="sxs-lookup"><span data-stu-id="7465c-136">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[ManagerImplicitlyCallingParameterlessBaseConstructor#6](snippets/using-constructors/Program.cs#6)]
  
 [!code-csharp[ManagerExplicitlyCallingParameterlessBaseConstructor#7](snippets/using-constructors/Program.cs#7)]
  
 <span data-ttu-id="7465c-137">如果基底類別未提供無參數建構函式，衍生類別就必須使用 `base` 明確呼叫基底建構函式。</span><span class="sxs-lookup"><span data-stu-id="7465c-137">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="7465c-138">建構函式可以使用 [this](../../language-reference/keywords/this.md) 關鍵字來叫用相同物件中的另一個建構函式。</span><span class="sxs-lookup"><span data-stu-id="7465c-138">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="7465c-139">如同 `base`，不論是否有參數，都可以使用 `this`，而且建構函式中的任何參數都可以作為 `this` 的參數使用，或作為運算式的一部分使用。</span><span class="sxs-lookup"><span data-stu-id="7465c-139">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="7465c-140">例如，上述範例中的第二個建構函式可使用 `this` 重寫成：</span><span class="sxs-lookup"><span data-stu-id="7465c-140">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[EmployeeCallingConstructorInSameClass#8](snippets/using-constructors/Program.cs#8)]
  
 <span data-ttu-id="7465c-141">在上述範例中使用 `this` 會呼叫下列建構函式：</span><span class="sxs-lookup"><span data-stu-id="7465c-141">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[ConstructorBeingCalledByThisKeyword#9](snippets/using-constructors/Program.cs#9)]
  
 <span data-ttu-id="7465c-142">建構函式可以標記為 [public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) 或 [private protected](../../language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="7465c-142">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="7465c-143">這些存取修飾詞定義類別使用者如何建構類別。</span><span class="sxs-lookup"><span data-stu-id="7465c-143">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="7465c-144">如需詳細資訊，請參閱[存取修飾詞](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="7465c-144">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="7465c-145">建構函式可使用 [static](../../language-reference/keywords/static.md) 關鍵字宣告為靜態。</span><span class="sxs-lookup"><span data-stu-id="7465c-145">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="7465c-146">靜態建構函式會在即將存取任何靜態欄位之前自動進行呼叫，而且通常會用來初始化靜態類別成員。</span><span class="sxs-lookup"><span data-stu-id="7465c-146">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="7465c-147">如需詳細資訊，請參閱[靜態建構函式](./static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="7465c-147">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7465c-148">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="7465c-148">C# Language Specification</span></span>  

<span data-ttu-id="7465c-149">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[執行個體建構函式](~/_csharplang/spec/classes.md#instance-constructors)和[靜態建構函式](~/_csharplang/spec/classes.md#static-constructors)。</span><span class="sxs-lookup"><span data-stu-id="7465c-149">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="7465c-150">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="7465c-150">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7465c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7465c-151">See also</span></span>

- [<span data-ttu-id="7465c-152">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7465c-152">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7465c-153">類別和結構</span><span class="sxs-lookup"><span data-stu-id="7465c-153">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="7465c-154">建構函式</span><span class="sxs-lookup"><span data-stu-id="7465c-154">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="7465c-155">完成項</span><span class="sxs-lookup"><span data-stu-id="7465c-155">Finalizers</span></span>](./destructors.md)
