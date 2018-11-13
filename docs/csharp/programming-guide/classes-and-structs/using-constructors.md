---
title: 使用建構函式 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: d10b0de0a3811e615297b31d2d9c8934c9338078
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "43529016"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="39d3b-102">使用建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="39d3b-102">Using Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="39d3b-103">建立[類別](../../../csharp/language-reference/keywords/class.md)或[結構](../../../csharp/language-reference/keywords/struct.md)時，會呼叫其建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-103">When a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="39d3b-104">建構函式的名稱與類別或結構相同，而且通常會初始化新物件的資料成員。</span><span class="sxs-lookup"><span data-stu-id="39d3b-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="39d3b-105">在下列範例中，使用一個簡單的建構函式定義名為 `Taxi` 的類別。</span><span class="sxs-lookup"><span data-stu-id="39d3b-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="39d3b-106">然後使用 [new](../../../csharp/language-reference/keywords/new.md) 運算子具現化此類別。</span><span class="sxs-lookup"><span data-stu-id="39d3b-106">This class is then instantiated with the [new](../../../csharp/language-reference/keywords/new.md) operator.</span></span> <span data-ttu-id="39d3b-107">為新物件配置記憶體之後，`new` 運算子會立即叫用 `Taxi` 建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 <span data-ttu-id="39d3b-108">不使用任何參數的建構函式稱為 *預設建構函式*。</span><span class="sxs-lookup"><span data-stu-id="39d3b-108">A constructor that takes no parameters is called a *default constructor*.</span></span> <span data-ttu-id="39d3b-109">每當使用 `new` 運算子來具現化物件，而且未提供引數給 `new` 時，便會叫用預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-109">Default constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="39d3b-110">如需詳細資訊，請參閱[執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="39d3b-110">For more information, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="39d3b-111">除非是[靜態](../../../csharp/language-reference/keywords/static.md)類別，否則只要是沒有建構函式的類別，C# 編譯器都會指定公用預設建構函式，以啟用類別具現化。</span><span class="sxs-lookup"><span data-stu-id="39d3b-111">Unless the class is [static](../../../csharp/language-reference/keywords/static.md), classes without constructors are given a public default constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="39d3b-112">如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="39d3b-112">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="39d3b-113">您可以將建構函式設為私用，避免具現化類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="39d3b-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 <span data-ttu-id="39d3b-114">如需詳細資訊，請參閱 [私用建構函式](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="39d3b-114">For more information, see [Private Constructors](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span></span>  
  
 <span data-ttu-id="39d3b-115">[結構](../../../csharp/language-reference/keywords/struct.md)類型的建構函式與類別建構函式類似，但 `structs` 不能包含明確的預設建構函式，因為編譯器已自動提供一個預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-115">Constructors for [struct](../../../csharp/language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit default constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="39d3b-116">此建構函式會將 `struct` 中的每個欄位都初始化為預設值。</span><span class="sxs-lookup"><span data-stu-id="39d3b-116">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="39d3b-117">如需詳細資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。</span><span class="sxs-lookup"><span data-stu-id="39d3b-117">For more information, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="39d3b-118">不過，只有 `struct` 是以 `new` 具現化時，才會呼叫此預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-118">However, this default constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="39d3b-119">例如，此程式碼使用 <xref:System.Int32> 的預設建構函式，以確保整數已初始化：</span><span class="sxs-lookup"><span data-stu-id="39d3b-119">For example, this code uses the default constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="39d3b-120">不過，下列程式碼由於未使用 `new`，而且會嘗試使用尚未初始化的物件，因此會造成編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="39d3b-120">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="39d3b-121">或者，您可以初始化或指派以 `structs` 為基礎的物件 (包括所有內建數字類型)，再如下列範例所示使用這些物件：</span><span class="sxs-lookup"><span data-stu-id="39d3b-121">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="39d3b-122">因此不需要呼叫實值型別的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-122">So calling the default constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="39d3b-123">類別和 `structs` 都可以定義使用參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-123">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="39d3b-124">使用參數的建構函式必須透過 `new` 陳述式或 [base](../../../csharp/language-reference/keywords/base.md) 陳述式呼叫。</span><span class="sxs-lookup"><span data-stu-id="39d3b-124">Constructors that take parameters must be called through a `new` statement or a [base](../../../csharp/language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="39d3b-125">類別和 `structs` 也可以定義多個建構函式，而且都不必定義預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-125">Classes and `structs` can also define multiple constructors, and neither is required to define a default constructor.</span></span> <span data-ttu-id="39d3b-126">例如: </span><span class="sxs-lookup"><span data-stu-id="39d3b-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 <span data-ttu-id="39d3b-127">使用下列任一陳述式即可建立此類別：</span><span class="sxs-lookup"><span data-stu-id="39d3b-127">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 <span data-ttu-id="39d3b-128">建構函式可以使用 `base` 關鍵字呼叫基底類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-128">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="39d3b-129">例如: </span><span class="sxs-lookup"><span data-stu-id="39d3b-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 <span data-ttu-id="39d3b-130">在此範例中，執行建構函式的區塊之前，會先呼叫基底類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-130">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="39d3b-131">不論是否有參數，都可以使用 `base` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="39d3b-131">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="39d3b-132">建構函式的任何參數都可以作為 `base` 的參數使用，或作為運算式的一部分使用。</span><span class="sxs-lookup"><span data-stu-id="39d3b-132">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="39d3b-133">如需詳細資訊，請參閱 [base](../../../csharp/language-reference/keywords/base.md)。</span><span class="sxs-lookup"><span data-stu-id="39d3b-133">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="39d3b-134">在衍生類別中，如果未使用 `base` 關鍵字明確呼叫基底類別建構函式，則會隱含呼叫預設建構函式 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="39d3b-134">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the default constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="39d3b-135">這表示下列建構函式宣告的作用相同：</span><span class="sxs-lookup"><span data-stu-id="39d3b-135">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 <span data-ttu-id="39d3b-136">如果基底類別未提供預設建構函式，衍生類別就必須使用 `base` 明確呼叫基底建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-136">If a base class does not offer a default constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="39d3b-137">建構函式可以使用 [this](../../../csharp/language-reference/keywords/this.md) 關鍵字來叫用相同物件中的另一個建構函式。</span><span class="sxs-lookup"><span data-stu-id="39d3b-137">A constructor can invoke another constructor in the same object by using the [this](../../../csharp/language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="39d3b-138">如同 `base`，不論是否有參數，都可以使用 `this`，而且建構函式中的任何參數都可以作為 `this` 的參數使用，或作為運算式的一部分使用。</span><span class="sxs-lookup"><span data-stu-id="39d3b-138">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="39d3b-139">例如，上述範例中的第二個建構函式可使用 `this` 重寫成：</span><span class="sxs-lookup"><span data-stu-id="39d3b-139">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 <span data-ttu-id="39d3b-140">在上述範例中使用 `this` 會呼叫下列建構函式：</span><span class="sxs-lookup"><span data-stu-id="39d3b-140">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 <span data-ttu-id="39d3b-141">建構函式可以標記為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[protected internal](../../../csharp/language-reference/keywords/protected-internal.md) 或 [private protected](../../../csharp/language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="39d3b-141">Constructors can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="39d3b-142">這些存取修飾詞定義類別使用者如何建構類別。</span><span class="sxs-lookup"><span data-stu-id="39d3b-142">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="39d3b-143">如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="39d3b-143">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="39d3b-144">建構函式可使用 [static](../../../csharp/language-reference/keywords/static.md) 關鍵字宣告為靜態。</span><span class="sxs-lookup"><span data-stu-id="39d3b-144">A constructor can be declared static by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="39d3b-145">靜態建構函式會在即將存取任何靜態欄位之前自動進行呼叫，而且通常會用來初始化靜態類別成員。</span><span class="sxs-lookup"><span data-stu-id="39d3b-145">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="39d3b-146">如需詳細資訊，請參閱[靜態建構函式](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="39d3b-146">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="39d3b-147">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="39d3b-147">C# Language Specification</span></span>  

<span data-ttu-id="39d3b-148">如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)的[執行個體建構函式](~/_csharplang/spec/classes.md#instance-constructors)和[靜態建構函式](~/_csharplang/spec/classes.md#static-constructors)。</span><span class="sxs-lookup"><span data-stu-id="39d3b-148">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="39d3b-149">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="39d3b-149">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="39d3b-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="39d3b-150">See Also</span></span>

- [<span data-ttu-id="39d3b-151">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="39d3b-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="39d3b-152">類別和結構</span><span class="sxs-lookup"><span data-stu-id="39d3b-152">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="39d3b-153">建構函式</span><span class="sxs-lookup"><span data-stu-id="39d3b-153">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="39d3b-154">完成項</span><span class="sxs-lookup"><span data-stu-id="39d3b-154">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
