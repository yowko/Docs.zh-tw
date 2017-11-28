---
title: "型別參數的條件約束 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: "41"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f5382b0050b81ed3bb1a075a042bdc4034a3975d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a><span data-ttu-id="5a8f6-102">型別參數的條件約束 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5a8f6-102">Constraints on Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="5a8f6-103">當您定義泛型類別時，可以將限制套用至用戶端程式碼在具現化類別時可用於型別引數的類型種類。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-103">When you define a generic class, you can apply restrictions to the kinds of types that client code can use for type arguments when it instantiates your class.</span></span> <span data-ttu-id="5a8f6-104">如果用戶端程式碼嘗試使用條件約束不允許的類型來具現化類別，則結果是編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-104">If client code tries to instantiate your class by using a type that is not allowed by a constraint, the result is a compile-time error.</span></span> <span data-ttu-id="5a8f6-105">這些限制稱為條件約束。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-105">These restrictions are called constraints.</span></span> <span data-ttu-id="5a8f6-106">條件約束是使用 `where` 內容關鍵字所指定。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-106">Constraints are specified by using the `where` contextual keyword.</span></span> <span data-ttu-id="5a8f6-107">下表列出六種類型的條件約束：</span><span class="sxs-lookup"><span data-stu-id="5a8f6-107">The following table lists the six types of constraints:</span></span>  
  
|<span data-ttu-id="5a8f6-108">條件約束</span><span class="sxs-lookup"><span data-stu-id="5a8f6-108">Constraint</span></span>|<span data-ttu-id="5a8f6-109">描述</span><span class="sxs-lookup"><span data-stu-id="5a8f6-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="5a8f6-110">其中 T: 結構</span><span class="sxs-lookup"><span data-stu-id="5a8f6-110">where T: struct</span></span>|<span data-ttu-id="5a8f6-111">型別引數必須是實值型別。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-111">The type argument must be a value type.</span></span> <span data-ttu-id="5a8f6-112">您可以指定 <xref:System.Nullable> 以外的任何實值型別。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-112">Any value type except <xref:System.Nullable> can be specified.</span></span> <span data-ttu-id="5a8f6-113">如需詳細資訊，請參閱[使用可為 Null 的類型](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-113">See [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md) for more information.</span></span>|  
|<span data-ttu-id="5a8f6-114">其中 T : 類別</span><span class="sxs-lookup"><span data-stu-id="5a8f6-114">where T : class</span></span>|<span data-ttu-id="5a8f6-115">型別引數必須是參考型別；這也適用於任何類別、介面、委派或陣列類型。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-115">The type argument must be a reference type; this applies also to any class, interface, delegate, or array type.</span></span>|  
|<span data-ttu-id="5a8f6-116">其中 T : new()</span><span class="sxs-lookup"><span data-stu-id="5a8f6-116">where T : new()</span></span>|<span data-ttu-id="5a8f6-117">型別引數必須有公用無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-117">The type argument must have a public parameterless constructor.</span></span> <span data-ttu-id="5a8f6-118">與其他條件約束搭配使用時，`new()` 條件約束必須是最後一個指定的。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-118">When used together with other constraints, the `new()` constraint must be specified last.</span></span>|  
|<span data-ttu-id="5a8f6-119">其中 T : \<基底類別名稱></span><span class="sxs-lookup"><span data-stu-id="5a8f6-119">where T : \<base class name></span></span>|<span data-ttu-id="5a8f6-120">型別引數必須是或衍生自指定的基底類別。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-120">The type argument must be or derive from the specified base class.</span></span>|  
|<span data-ttu-id="5a8f6-121">其中 T : \<介面名稱></span><span class="sxs-lookup"><span data-stu-id="5a8f6-121">where T : \<interface name></span></span>|<span data-ttu-id="5a8f6-122">型別引數必須是或實作指定的介面。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-122">The type argument must be or implement the specified interface.</span></span> <span data-ttu-id="5a8f6-123">您可以指定多個介面條件約束。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-123">Multiple interface constraints can be specified.</span></span> <span data-ttu-id="5a8f6-124">條件約束介面也是泛型。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-124">The constraining interface can also be generic.</span></span>|  
|<span data-ttu-id="5a8f6-125">其中 T : U</span><span class="sxs-lookup"><span data-stu-id="5a8f6-125">where T : U</span></span>|<span data-ttu-id="5a8f6-126">針對 T 提供的型別引數必須是或衍生自針對 U 所提供的引數。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-126">The type argument supplied for T must be or derive from the argument supplied for U.</span></span>|  
  
## <a name="why-use-constraints"></a><span data-ttu-id="5a8f6-127">為什麼使用條件約束</span><span class="sxs-lookup"><span data-stu-id="5a8f6-127">Why Use Constraints</span></span>  
 <span data-ttu-id="5a8f6-128">如果您想要檢查泛型清單中的項目來判斷它是否有效，或比較它與某個其他項目，則編譯器必須保證用戶端程式碼所指定的任何型別引數將支援編譯器必須呼叫的運算子或方法。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-128">If you want to examine an item in a generic list to determine whether it is valid or to compare it to some other item, the compiler must have some guarantee that the operator or method it has to call will be supported by any type argument that might be specified by client code.</span></span> <span data-ttu-id="5a8f6-129">這項保證是透過將一或多個條件約束套用至泛型類別定義來獲得。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-129">This guarantee is obtained by applying one or more constraints to your generic class definition.</span></span> <span data-ttu-id="5a8f6-130">例如，基底類別條件約束會告知編譯器只有這個類型的物件或衍生自這個類型的物件才會用作型別引數。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-130">For example, the base class constraint tells the compiler that only objects of this type or derived from this type will be used as type arguments.</span></span> <span data-ttu-id="5a8f6-131">編譯器具有這項保證之後，就可以允許在泛型類別中呼叫該類型的方法。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-131">Once the compiler has this guarantee, it can allow methods of that type to be called in the generic class.</span></span> <span data-ttu-id="5a8f6-132">條件約束是使用 `where` 內容關鍵字所套用。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-132">Constraints are applied by using the contextual keyword `where`.</span></span> <span data-ttu-id="5a8f6-133">下列程式碼範例示範我們可以套用基底類別條件約束來新增至 `GenericList<T>` 類別的功能 (在[泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)中)。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-133">The following code example demonstrates the functionality we can add to the `GenericList<T>` class (in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md)) by applying a base class constraint.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]  
  
 <span data-ttu-id="5a8f6-134">條件約束可讓泛型類別使用 `Employee.Name` 屬性，因為類型 T 的所有項目一定是 `Employee` 物件或是繼承自 `Employee` 的物件。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-134">The constraint enables the generic class to use the `Employee.Name` property because all items of type T are guaranteed to be either an `Employee` object or an object that inherits from `Employee`.</span></span>  
  
 <span data-ttu-id="5a8f6-135">多個條件約束可以套用至相同的型別參數，而且條件約束本身可以是泛型型別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5a8f6-135">Multiple constraints can be applied to the same type parameter, and the constraints themselves can be generic types, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]  
  
 <span data-ttu-id="5a8f6-136">透過限制型別參數，即可增加條件約束類型和其繼承階層中所有類型所支援項目的允許作業和方法呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-136">By constraining the type parameter, you increase the number of allowable operations and method calls to those supported by the constraining type and all types in its inheritance hierarchy.</span></span> <span data-ttu-id="5a8f6-137">因此，當您設計泛型類別或方法時，如果要對簡單指派以外的泛型成員執行任何作業，或呼叫 `System.Object` 不支援的任何方法，則必須將條件約束套用至型別參數。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-137">Therefore, when you design generic classes or methods, if you will be performing any operation on the generic members beyond simple assignment or calling any methods not supported by `System.Object`, you will have to apply constraints to the type parameter.</span></span>  
  
 <span data-ttu-id="5a8f6-138">套用 `where T : class` 條件約束時，請避免在型別參數上使用 `==` 和 `!=` 運算子，因為這些運算子只會測試參考識別是否相等，但不會測試值是否相等。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-138">When applying the `where T : class` constraint, avoid the `==` and `!=` operators on the type parameter because these operators will test for reference identity only, not for value equality.</span></span> <span data-ttu-id="5a8f6-139">這是這種情況，即使在用作引數的類型中多載這些運算子也是一樣。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-139">This is the case even if these operators are overloaded in a type that is used as an argument.</span></span> <span data-ttu-id="5a8f6-140">下列程式碼說明這點；輸出為 false，即使 <xref:System.String> 類別多載 `==` 運算子也是一樣。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-140">The following code illustrates this point; the output is false even though the <xref:System.String> class overloads the `==` operator.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]  
  
 <span data-ttu-id="5a8f6-141">這項行為的原因在於，在編譯時間，編譯器只會知道 T 是參考型別，因此必須使用適用於所有參考型別的預設運算子。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-141">The reason for this behavior is that, at compile time, the compiler only knows that T is a reference type, and therefore must use the default operators that are valid for all reference types.</span></span> <span data-ttu-id="5a8f6-142">如果您必須測試值是否相等，建議方式也會套用 `where T : IComparable<T>` 條件約束，並在任何將用來建構泛型類別的類別中實作該介面。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-142">If you must test for value equality, the recommended way is to also apply the `where T : IComparable<T>` constraint and implement that interface in any class that will be used to construct the generic class.</span></span>  
  
## <a name="constraining-multiple-parameters"></a><span data-ttu-id="5a8f6-143">限制多個參數</span><span class="sxs-lookup"><span data-stu-id="5a8f6-143">Constraining Multiple Parameters</span></span>  
 <span data-ttu-id="5a8f6-144">您可以將條件約束套用至多個參數，以及將多個條件約束套用至單一參數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5a8f6-144">You can apply constraints to multiple parameters, and multiple constraints to a single parameter, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]  
  
## <a name="unbounded-type-parameters"></a><span data-ttu-id="5a8f6-145">未繫結的型別參數</span><span class="sxs-lookup"><span data-stu-id="5a8f6-145">Unbounded Type Parameters</span></span>  
 <span data-ttu-id="5a8f6-146">沒有條件約束的型別參數 (例如公用類別 `SampleClass<T>{}` 中的 T) 稱為「未繫結的型別參數」。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-146">Type parameters that have no constraints, such as T in public class `SampleClass<T>{}`, are called unbounded type parameters.</span></span> <span data-ttu-id="5a8f6-147">未繫結的型別參數具有下列規則：</span><span class="sxs-lookup"><span data-stu-id="5a8f6-147">Unbounded type parameters have the following rules:</span></span>  
  
-   <span data-ttu-id="5a8f6-148">因為不保證具體型別引數將支援 `!=` 和 `==` 運算子，所以無法使用這些運作子。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-148">The `!=` and `==` operators cannot be used because there is no guarantee that the concrete type argument will support these operators.</span></span>  
  
-   <span data-ttu-id="5a8f6-149">它們可以與 `System.Object` 進行來回轉換，或明確轉換成任何介面類型。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-149">They can be converted to and from `System.Object` or explicitly converted to any interface type.</span></span>  
  
-   <span data-ttu-id="5a8f6-150">您可以比較 [null](../../../csharp/language-reference/keywords/null.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-150">You can compare to [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="5a8f6-151">如果未繫結的參數與 `null` 進行比較，則型別引數是實值型別時，比較一律會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-151">If an unbounded parameter is compared to `null`, the comparison will always return false if the type argument is a value type.</span></span>  
  
## <a name="type-parameters-as-constraints"></a><span data-ttu-id="5a8f6-152">作為條件約束的型別參數</span><span class="sxs-lookup"><span data-stu-id="5a8f6-152">Type Parameters as Constraints</span></span>  
 <span data-ttu-id="5a8f6-153">具有專屬型別參數的成員函式需要將該參數限制為包含類型的型別參數時，將泛型型別參數用作條件約束十分有用，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5a8f6-153">The use of a generic type parameter as a constraint is useful when a member function with its own type parameter has to constrain that parameter to the type parameter of the containing type, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]  
  
 <span data-ttu-id="5a8f6-154">在上述範例中，`T` 是 `Add` 方法內容中的類型條件約束，以及 `List` 類別內容中的未繫結型別參數。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-154">In the previous example, `T` is a type constraint in the context of the `Add` method, and an unbounded type parameter in the context of the `List` class.</span></span>  
  
 <span data-ttu-id="5a8f6-155">型別參數也可以在泛型類別定義中用作條件約束。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-155">Type parameters can also be used as constraints in generic class definitions.</span></span> <span data-ttu-id="5a8f6-156">請注意，型別參數必須與任何其他型別參數一起宣告於角括弧內：</span><span class="sxs-lookup"><span data-stu-id="5a8f6-156">Note that the type parameter must be declared within the angle brackets together with any other type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]  
  
 <span data-ttu-id="5a8f6-157">型別參數作為條件約束對泛型類別來說極不實用，因為編譯器除了會假設型別參數衍生自 `System.Object` 之外，不會再做其他任何假設。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-157">The usefulness of type parameters as constraints with generic classes is very limited because the compiler can assume nothing about the type parameter except that it derives from `System.Object`.</span></span> <span data-ttu-id="5a8f6-158">如果您要強制兩個型別參數之間具有繼承關係，請在泛型類別上將型別參數用作條件約束。</span><span class="sxs-lookup"><span data-stu-id="5a8f6-158">Use type parameters as constraints on generic classes in scenarios in which you want to enforce an inheritance relationship between two type parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8f6-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a8f6-159">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="5a8f6-160">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5a8f6-160">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5a8f6-161">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="5a8f6-161">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="5a8f6-162">泛型類別</span><span class="sxs-lookup"><span data-stu-id="5a8f6-162">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
 [<span data-ttu-id="5a8f6-163">new 條件約束</span><span class="sxs-lookup"><span data-stu-id="5a8f6-163">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)
