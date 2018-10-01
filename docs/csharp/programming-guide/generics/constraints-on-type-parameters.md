---
title: 型別參數的條件約束 (C# 程式設計手冊)
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: df5a509296f3fb9e8e77a273a0636c74a6f86da3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47232712"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a><span data-ttu-id="380f5-102">型別參數的條件約束 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="380f5-102">Constraints on type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="380f5-103">條件約束會通知編譯器有關型別引數必須要有的功能。</span><span class="sxs-lookup"><span data-stu-id="380f5-103">Constraints inform the compiler about the capabilities a type argument must have.</span></span> <span data-ttu-id="380f5-104">如果沒有任何條件約束，則型別引數可以是任何型別。</span><span class="sxs-lookup"><span data-stu-id="380f5-104">Without any constraints, the type argument could be any type.</span></span> <span data-ttu-id="380f5-105">編譯器只能採用 <xref:System.Object?displayPropety=nameWithType> 成員，這是任何 .NET 型別的最終基底類別。</span><span class="sxs-lookup"><span data-stu-id="380f5-105">The compiler can only assume the members of <xref:System.Object?displayPropety=nameWithType>, which is the ultimate base class for any .NET type.</span></span> <span data-ttu-id="380f5-106">如需詳細資訊，請參閱[為什麼使用條件約束](#why-use-constraints)。</span><span class="sxs-lookup"><span data-stu-id="380f5-106">For more information, see [Why use constraints](#why-use-constraints).</span></span> <span data-ttu-id="380f5-107">如果用戶端程式碼嘗試使用條件約束不允許的類型來具現化類別，則結果是編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="380f5-107">If client code tries to instantiate your class by using a type that is not allowed by a constraint, the result is a compile-time error.</span></span> <span data-ttu-id="380f5-108">條件約束是使用 `where` 內容關鍵字所指定。</span><span class="sxs-lookup"><span data-stu-id="380f5-108">Constraints are specified by using the `where` contextual keyword.</span></span> <span data-ttu-id="380f5-109">下表列出七種類型的條件約束：</span><span class="sxs-lookup"><span data-stu-id="380f5-109">The following table lists the seven types of constraints:</span></span>

|<span data-ttu-id="380f5-110">條件約束</span><span class="sxs-lookup"><span data-stu-id="380f5-110">Constraint</span></span>|<span data-ttu-id="380f5-111">描述</span><span class="sxs-lookup"><span data-stu-id="380f5-111">Description</span></span>|
|----------------|-----------------|
|`where T : struct`|<span data-ttu-id="380f5-112">型別引數必須是實值型別。</span><span class="sxs-lookup"><span data-stu-id="380f5-112">The type argument must be a value type.</span></span> <span data-ttu-id="380f5-113">您可以指定 <xref:System.Nullable%601> 以外的任何實值型別。</span><span class="sxs-lookup"><span data-stu-id="380f5-113">Any value type except <xref:System.Nullable%601> can be specified.</span></span> <span data-ttu-id="380f5-114">如需可為 Null 型別的詳細資訊，請參閱[可為 Null 的型別](../nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="380f5-114">For more information about nullable types, see [Nullable types](../nullable-types/index.md).</span></span>|
|`where T : class`|<span data-ttu-id="380f5-115">型別引數必須是參考型別。</span><span class="sxs-lookup"><span data-stu-id="380f5-115">The type argument must be a reference type.</span></span> <span data-ttu-id="380f5-116">此條件約束也適用於任何類別、介面、委派或陣列型別。</span><span class="sxs-lookup"><span data-stu-id="380f5-116">This constraint applies also to any class, interface, delegate, or array type.</span></span>|
|`where T : unmanaged`|<span data-ttu-id="380f5-117">型別引數不得是參考型別，也不得包含任何巢狀層級的任何參考型別成員。</span><span class="sxs-lookup"><span data-stu-id="380f5-117">The type argument must not be a reference type and must not contain any reference type members at any level of nesting.</span></span>|
|`where T : new()`|<span data-ttu-id="380f5-118">型別引數必須有公用無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="380f5-118">The type argument must have a public parameterless constructor.</span></span> <span data-ttu-id="380f5-119">與其他條件約束搭配使用時，`new()` 條件約束必須是最後一個指定的。</span><span class="sxs-lookup"><span data-stu-id="380f5-119">When used together with other constraints, the `new()` constraint must be specified last.</span></span>|
|<span data-ttu-id="380f5-120">`where T :` *\<基底類別名稱>*</span><span class="sxs-lookup"><span data-stu-id="380f5-120">`where T :` *\<base class name>*</span></span>|<span data-ttu-id="380f5-121">型別引數必須是或衍生自指定的基底類別。</span><span class="sxs-lookup"><span data-stu-id="380f5-121">The type argument must be or derive from the specified base class.</span></span>|
|<span data-ttu-id="380f5-122">`where T :` *\<介面名稱>*</span><span class="sxs-lookup"><span data-stu-id="380f5-122">`where T :` *\<interface name>*</span></span>|<span data-ttu-id="380f5-123">型別引數必須是或實作指定的介面。</span><span class="sxs-lookup"><span data-stu-id="380f5-123">The type argument must be or implement the specified interface.</span></span> <span data-ttu-id="380f5-124">您可以指定多個介面條件約束。</span><span class="sxs-lookup"><span data-stu-id="380f5-124">Multiple interface constraints can be specified.</span></span> <span data-ttu-id="380f5-125">條件約束介面也是泛型。</span><span class="sxs-lookup"><span data-stu-id="380f5-125">The constraining interface can also be generic.</span></span>|
|`where T : U`|<span data-ttu-id="380f5-126">針對 T 提供的型別引數必須是或衍生自針對 U 所提供的引數。</span><span class="sxs-lookup"><span data-stu-id="380f5-126">The type argument supplied for T must be or derive from the argument supplied for U.</span></span>|

<span data-ttu-id="380f5-127">有些條件約束會互斥。</span><span class="sxs-lookup"><span data-stu-id="380f5-127">Some of the constraints are mutually exclusive.</span></span> <span data-ttu-id="380f5-128">所有實值型別都必須有可存取的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="380f5-128">All value types must have an accessible parameterless constructor.</span></span> <span data-ttu-id="380f5-129">`struct` 條件約束表示 `new()` 條件約束和 `new()` 條件約束不能與 `struct` 條件約束合併使用。</span><span class="sxs-lookup"><span data-stu-id="380f5-129">The `struct` constraint implies the `new()` constraint and the `new()` constraint cannot be combined with the `struct` constraint.</span></span> <span data-ttu-id="380f5-130">`unmanaged` 條件約束表示 `struct` 條件約束。</span><span class="sxs-lookup"><span data-stu-id="380f5-130">The `unmanaged` constraint implies the `struct` constraint.</span></span> <span data-ttu-id="380f5-131">`unmanaged` 條件約束不能與 `struct` 或 `new()` 條件約束合併使用。</span><span class="sxs-lookup"><span data-stu-id="380f5-131">The `unmanaged` constraint cannot be combined with either the `struct` or `new()` constraints.</span></span>

## <a name="why-use-constraints"></a><span data-ttu-id="380f5-132">為什麼使用條件約束</span><span class="sxs-lookup"><span data-stu-id="380f5-132">Why use constraints</span></span>

<span data-ttu-id="380f5-133">透過限制型別參數，即可增加條件約束類型和其繼承階層中所有類型所支援項目的允許作業和方法呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="380f5-133">By constraining the type parameter, you increase the number of allowable operations and method calls to those supported by the constraining type and all types in its inheritance hierarchy.</span></span> <span data-ttu-id="380f5-134">當您設計泛型類別或方法時，如果要對簡單指派以外的泛型成員執行任何作業，或呼叫 <xref:System.Object?displayProperty=nameWithType> 不支援的任何方法，則必須將條件約束套用至型別參數。</span><span class="sxs-lookup"><span data-stu-id="380f5-134">When you design generic classes or methods, if you will be performing any operation on the generic members beyond simple assignment or calling any methods not supported by <xref:System.Object?displayProperty=nameWithType>, you will have to apply constraints to the type parameter.</span></span> <span data-ttu-id="380f5-135">例如，基底類別條件約束會告知編譯器只有這個類型的物件或衍生自這個類型的物件才會用作型別引數。</span><span class="sxs-lookup"><span data-stu-id="380f5-135">For example, the base class constraint tells the compiler that only objects of this type or derived from this type will be used as type arguments.</span></span> <span data-ttu-id="380f5-136">編譯器具有這項保證之後，就可以允許在泛型類別中呼叫該類型的方法。</span><span class="sxs-lookup"><span data-stu-id="380f5-136">Once the compiler has this guarantee, it can allow methods of that type to be called in the generic class.</span></span> <span data-ttu-id="380f5-137">下列程式碼範例示範您可以套用基底類別條件約束來新增至 `GenericList<T>` 類別的功能 (在[泛型簡介](introduction-to-generics.md)中)。</span><span class="sxs-lookup"><span data-stu-id="380f5-137">The following code example demonstrates the functionality you can add to the `GenericList<T>` class (in [Introduction to Generics](introduction-to-generics.md)) by applying a base class constraint.</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

<span data-ttu-id="380f5-138">條件約束可讓泛型類別使用 `Employee.Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="380f5-138">The constraint enables the generic class to use the `Employee.Name` property.</span></span> <span data-ttu-id="380f5-139">條件約束指定 `T` 型別的所有項目保證都是 `Employee` 物件或繼承自 `Employee` 的物件。</span><span class="sxs-lookup"><span data-stu-id="380f5-139">The constraint specifies that all items of type `T` are guaranteed to be either an `Employee` object or an object that inherits from `Employee`.</span></span>

<span data-ttu-id="380f5-140">多個條件約束可以套用至相同的型別參數，而且條件約束本身可以是泛型型別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="380f5-140">Multiple constraints can be applied to the same type parameter, and the constraints themselves can be generic types, as follows:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

<span data-ttu-id="380f5-141">套用 `where T : class` 條件約束時，請避免在型別參數上使用 `==` 和 `!=` 運算子，因為這些運算子只會測試參考識別是否相等，但不會測試值是否相等。</span><span class="sxs-lookup"><span data-stu-id="380f5-141">When applying the `where T : class` constraint, avoid the `==` and `!=` operators on the type parameter because these operators will test for reference identity only, not for value equality.</span></span> <span data-ttu-id="380f5-142">即使在用作引數的型別中多載這些運算子，也會發生這種行為。</span><span class="sxs-lookup"><span data-stu-id="380f5-142">This behavior occurs even if these operators are overloaded in a type that is used as an argument.</span></span> <span data-ttu-id="380f5-143">下列程式碼說明這點；輸出為 false，即使 <xref:System.String> 類別多載 `==` 運算子也是一樣。</span><span class="sxs-lookup"><span data-stu-id="380f5-143">The following code illustrates this point; the output is false even though the <xref:System.String> class overloads the `==` operator.</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

<span data-ttu-id="380f5-144">編譯器在編譯時間只會知道 T 是參考型別，因此必須使用適用於所有參考型別的預設運算子。</span><span class="sxs-lookup"><span data-stu-id="380f5-144">The compiler only knows that T is a reference type at compile time and must use the default operators that are valid for all reference types.</span></span> <span data-ttu-id="380f5-145">如果您必須測試值是否相等，則建議同時套用 `where T : IEquatable<T>` 或 `where T : IComparable<T>` 條件約束，並在任何將用來建構泛型類別的類別中實作介面。</span><span class="sxs-lookup"><span data-stu-id="380f5-145">If you must test for value equality, the recommended way is to also apply the `where T : IEquatable<T>` or `where T : IComparable<T>` constraint and implement the interface in any class that will be used to construct the generic class.</span></span>

## <a name="constraining-multiple-parameters"></a><span data-ttu-id="380f5-146">限制多個參數</span><span class="sxs-lookup"><span data-stu-id="380f5-146">Constraining multiple parameters</span></span>

<span data-ttu-id="380f5-147">您可以將條件約束套用至多個參數，以及將多個條件約束套用至單一參數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="380f5-147">You can apply constraints to multiple parameters, and multiple constraints to a single parameter, as shown in the following example:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a><span data-ttu-id="380f5-148">未繫結的型別參數</span><span class="sxs-lookup"><span data-stu-id="380f5-148">Unbounded type parameters</span></span>

 <span data-ttu-id="380f5-149">沒有條件約束的型別參數 (例如公用類別 `SampleClass<T>{}` 中的 T) 稱為「未繫結的型別參數」。</span><span class="sxs-lookup"><span data-stu-id="380f5-149">Type parameters that have no constraints, such as T in public class `SampleClass<T>{}`, are called unbounded type parameters.</span></span> <span data-ttu-id="380f5-150">未繫結的型別參數具有下列規則：</span><span class="sxs-lookup"><span data-stu-id="380f5-150">Unbounded type parameters have the following rules:</span></span>

- <span data-ttu-id="380f5-151">因為不保證具體型別引數將支援 `!=` 和 `==` 運算子，所以無法使用這些運作子。</span><span class="sxs-lookup"><span data-stu-id="380f5-151">The `!=` and `==` operators cannot be used because there is no guarantee that the concrete type argument will support these operators.</span></span>
- <span data-ttu-id="380f5-152">它們可以與 `System.Object` 進行來回轉換，或明確轉換成任何介面類型。</span><span class="sxs-lookup"><span data-stu-id="380f5-152">They can be converted to and from `System.Object` or explicitly converted to any interface type.</span></span>
- <span data-ttu-id="380f5-153">您可以將它們與 [Null](../../language-reference/keywords/null.md) 比較。</span><span class="sxs-lookup"><span data-stu-id="380f5-153">You can compare them to [null](../../language-reference/keywords/null.md).</span></span> <span data-ttu-id="380f5-154">如果未繫結的參數與 `null` 進行比較，則型別引數是實值型別時，比較一律會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="380f5-154">If an unbounded parameter is compared to `null`, the comparison will always return false if the type argument is a value type.</span></span>

## <a name="type-parameters-as-constraints"></a><span data-ttu-id="380f5-155">作為條件約束的型別參數</span><span class="sxs-lookup"><span data-stu-id="380f5-155">Type parameters as constraints</span></span>

<span data-ttu-id="380f5-156">具有專屬型別參數的成員函式需要將該參數限制為包含類型的型別參數時，將泛型型別參數用作條件約束十分有用，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="380f5-156">The use of a generic type parameter as a constraint is useful when a member function with its own type parameter has to constrain that parameter to the type parameter of the containing type, as shown in the following example:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

<span data-ttu-id="380f5-157">在上述範例中，`T` 是 `Add` 方法內容中的類型條件約束，以及 `List` 類別內容中的未繫結型別參數。</span><span class="sxs-lookup"><span data-stu-id="380f5-157">In the previous example, `T` is a type constraint in the context of the `Add` method, and an unbounded type parameter in the context of the `List` class.</span></span>

<span data-ttu-id="380f5-158">型別參數也可以在泛型類別定義中用作條件約束。</span><span class="sxs-lookup"><span data-stu-id="380f5-158">Type parameters can also be used as constraints in generic class definitions.</span></span> <span data-ttu-id="380f5-159">型別參數必須與任何其他型別參數一起宣告於角括弧內：</span><span class="sxs-lookup"><span data-stu-id="380f5-159">The type parameter must be declared within the angle brackets together with any other type parameters:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

<span data-ttu-id="380f5-160">型別參數作為條件約束對泛型類別來說不實用，因為編譯器除了會假設型別參數衍生自 `System.Object` 之外，不會再做其他任何假設。</span><span class="sxs-lookup"><span data-stu-id="380f5-160">The usefulness of type parameters as constraints with generic classes is limited because the compiler can assume nothing about the type parameter except that it derives from `System.Object`.</span></span> <span data-ttu-id="380f5-161">如果您要強制兩個型別參數之間具有繼承關係，請在泛型類別上將型別參數用作條件約束。</span><span class="sxs-lookup"><span data-stu-id="380f5-161">Use type parameters as constraints on generic classes in scenarios in which you want to enforce an inheritance relationship between two type parameters.</span></span>

## <a name="unmanaged-constraint"></a><span data-ttu-id="380f5-162">非受控條件約束</span><span class="sxs-lookup"><span data-stu-id="380f5-162">Unmanaged constraint</span></span>

<span data-ttu-id="380f5-163">從 C# 7.3 開始，您可以使用 `unmanaged` 條件約束指定型別參數必須是「非受控型別」。</span><span class="sxs-lookup"><span data-stu-id="380f5-163">Beginning with C# 7.3, you can use the `unmanaged` constraint to specify that the type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="380f5-164">「非受控型別」是非參考型別的型別，而且未包含任何巢狀層級的參考型別欄位。</span><span class="sxs-lookup"><span data-stu-id="380f5-164">An **unmanaged type** is a type that is not a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="380f5-165">`unmanaged` 條件約束可讓您撰寫可重複使用的常式來使用型別，而型別可以操作為記憶體區塊，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="380f5-165">The `unmanaged` constraint enables you to write reusable routines to work with types that can be manipulated as blocks of memory, as shown in the following example:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

<span data-ttu-id="380f5-166">上述方法必須在 `unsafe` 內容中進行編譯，因為它在不知道是內建型別的型別上使用 `sizeof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="380f5-166">The preceding method must be compiled in an `unsafe` context because it uses the `sizeof` operator on a type not known to be a built-in type.</span></span> <span data-ttu-id="380f5-167">如果沒有 `unmanaged` 條件約束，則 `sizeof` 運算子無法使用。</span><span class="sxs-lookup"><span data-stu-id="380f5-167">Without the `unmanaged` constraint, the `sizeof` operator is unavailable.</span></span>

## <a name="delegate-constraints"></a><span data-ttu-id="380f5-168">委派條件約束</span><span class="sxs-lookup"><span data-stu-id="380f5-168">Delegate constraints</span></span>

<span data-ttu-id="380f5-169">而且，從 C# 7.3 開始，您可以使用 <xref:System.Delegate?displayProperty=nameWithType> 或 <xref:System.MulticastDelegate?displayProperty=nameWithType> 作為基底類別條件約束。</span><span class="sxs-lookup"><span data-stu-id="380f5-169">Also beginning with C# 7.3, you can use <xref:System.Delegate?displayProperty=nameWithType> or <xref:System.MulticastDelegate?displayProperty=nameWithType> as a base class constraint.</span></span> <span data-ttu-id="380f5-170">CLR 一律允許這個條件約束，但 C# 語言不允許它。</span><span class="sxs-lookup"><span data-stu-id="380f5-170">The CLR always allowed this constraint, but the C# language disallowed it.</span></span> <span data-ttu-id="380f5-171">`System.Delegate` 條件約束可讓您撰寫程式碼，以型別安全方式使用委派。</span><span class="sxs-lookup"><span data-stu-id="380f5-171">The `System.Delegate` constraint enables you to write code that works with delegates in a type-safe manner.</span></span> <span data-ttu-id="380f5-172">下列程式碼定義可結合兩個委派的擴充方法，但前提是它們的型別相同：</span><span class="sxs-lookup"><span data-stu-id="380f5-172">The following code defines an extension method that combines two delegates provided they are the same type:</span></span>

[!code-csharp[using the delegate constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

<span data-ttu-id="380f5-173">您可以使用上述方法來結合型別相同的委派：</span><span class="sxs-lookup"><span data-stu-id="380f5-173">You can use the above method to combine delegates that are the same type:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

<span data-ttu-id="380f5-174">如果您將最後一行取消註解，則不會編譯它。</span><span class="sxs-lookup"><span data-stu-id="380f5-174">If you uncomment the last line, it won't compile.</span></span> <span data-ttu-id="380f5-175">`first` 和 `test` 都是委派型別，但它們是不同的委派型別。</span><span class="sxs-lookup"><span data-stu-id="380f5-175">Both `first` and `test` are delegate types, but they are different delegate types.</span></span>

## <a name="enum-constraints"></a><span data-ttu-id="380f5-176">列舉條件約束</span><span class="sxs-lookup"><span data-stu-id="380f5-176">Enum constraints</span></span>

<span data-ttu-id="380f5-177">從 C# 7.3 開始，您也可以指定 <xref:System.Enum?displayProperty=nameWithType> 型別作為基底類別條件約束。</span><span class="sxs-lookup"><span data-stu-id="380f5-177">Beginning in C# 7.3, you can also specify the <xref:System.Enum?displayProperty=nameWithType> type as a base class constraint.</span></span> <span data-ttu-id="380f5-178">CLR 一律允許這個條件約束，但 C# 語言不允許它。</span><span class="sxs-lookup"><span data-stu-id="380f5-178">The CLR always allowed this constraint, but the C# language disallowed it.</span></span> <span data-ttu-id="380f5-179">使用 `System.Enum` 的泛型提供型別安全程式設計，以快取在 `System.Enum` 中使用靜態方法的結果。</span><span class="sxs-lookup"><span data-stu-id="380f5-179">Generics using `System.Enum` provide type-safe programming to cache results from using the static methods in `System.Enum`.</span></span> <span data-ttu-id="380f5-180">下列範例會尋找列舉型別的所有有效值，然後建置將這些值對應至其字串表示法的字典。</span><span class="sxs-lookup"><span data-stu-id="380f5-180">The following sample finds all the valid values for an enum type, and then builds a dictionary that maps those values to its string representation.</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

<span data-ttu-id="380f5-181">使用的方法會利用反映，而這會影響效能。</span><span class="sxs-lookup"><span data-stu-id="380f5-181">The methods used make use of reflection, which has performance implications.</span></span> <span data-ttu-id="380f5-182">您可以呼叫這個方法來建置可快取和重複使用的集合，而不是重複需要反映的呼叫。</span><span class="sxs-lookup"><span data-stu-id="380f5-182">You can call this method to build a collection that is cached and reused rather than repeating the calls that require reflection.</span></span>

<span data-ttu-id="380f5-183">您可以如下列範例所示使用它來建立列舉，並建置其值和名稱的字典：</span><span class="sxs-lookup"><span data-stu-id="380f5-183">You could use it as shown in the following sample to create an enum and build a dictionary of its values and names:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a><span data-ttu-id="380f5-184">請參閱</span><span class="sxs-lookup"><span data-stu-id="380f5-184">See Also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="380f5-185">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="380f5-185">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="380f5-186">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="380f5-186">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [<span data-ttu-id="380f5-187">泛型類別</span><span class="sxs-lookup"><span data-stu-id="380f5-187">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
- [<span data-ttu-id="380f5-188">new 條件約束</span><span class="sxs-lookup"><span data-stu-id="380f5-188">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
