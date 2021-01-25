---
title: 存取修飾詞 - C# 程式設計手冊
description: 'C # 中的所有類型和類型成員都具有存取範圍層級，可控制是否可從其他程式碼使用。 請參閱這份存取修飾詞清單。'
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: d800116137e088a54edb221fb4f81ecd47b0278f
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757859"
---
# <a name="access-modifiers-c-programming-guide"></a><span data-ttu-id="a1a7d-104">存取修飾詞 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a1a7d-104">Access Modifiers (C# Programming Guide)</span></span>

<span data-ttu-id="a1a7d-105">所有類型和類型成員都具有存取範圍層級。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-105">All types and type members have an accessibility level.</span></span> <span data-ttu-id="a1a7d-106">存取範圍層級可控制是否可從元件或其他元件中的其他程式碼使用它們。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-106">The accessibility level controls whether they can be used from other code in your assembly or other assemblies.</span></span> <span data-ttu-id="a1a7d-107">當您宣告類型或成員時，請使用下列存取修飾詞來指定其存取範圍：</span><span class="sxs-lookup"><span data-stu-id="a1a7d-107">Use the following access modifiers to specify the accessibility of a type or member when you declare it:</span></span>

- <span data-ttu-id="a1a7d-108">[public](../../language-reference/keywords/public.md)：類型或成員可由相同元件中的任何其他程式碼或參考它的另一個元件存取。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-108">[public](../../language-reference/keywords/public.md): The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>
- <span data-ttu-id="a1a7d-109">[私](../../language-reference/keywords/private.md)用：類型或成員只能由相同或中的程式碼存取 `class` `struct` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-109">[private](../../language-reference/keywords/private.md): The type or member can be accessed only by code in the same `class` or `struct`.</span></span>
- <span data-ttu-id="a1a7d-110">[protected](../../language-reference/keywords/protected.md)：類型或成員只能由相同 `class` 或 `class` 衍生自的程式碼存取 `class` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-110">[protected](../../language-reference/keywords/protected.md): The type or member can be accessed only by code in the same `class`, or in a `class` that is derived from that `class`.</span></span>
- <span data-ttu-id="a1a7d-111">[internal](../../language-reference/keywords/internal.md)：相同元件中的任何程式碼都可以存取類型或成員，但不能存取另一個元件的類型或成員。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-111">[internal](../../language-reference/keywords/internal.md): The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>
- <span data-ttu-id="a1a7d-112">[protected internal](../../language-reference/keywords/protected-internal.md)：類型或成員可以由其宣告之元件中的任何程式碼存取，或從另一個元件的衍生記憶體取 `class` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-112">[protected internal](../../language-reference/keywords/protected-internal.md): The type or member can be accessed by any code in the assembly in which it's declared, or from within a derived `class` in another assembly.</span></span>
- <span data-ttu-id="a1a7d-113">[私用保護](../../language-reference/keywords/private-protected.md)：類型或成員只能在其宣告元件中，透過相同 `class` 或衍生自該型別的程式碼來存取 `class` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-113">[private protected](../../language-reference/keywords/private-protected.md): The type or member can be accessed only within its declaring assembly, by code in the same `class` or in a type that is derived from that `class`.</span></span>

<span data-ttu-id="a1a7d-114">下列範例示範如何指定類型和成員的存取修飾詞︰</span><span class="sxs-lookup"><span data-stu-id="a1a7d-114">The following examples demonstrate how to specify access modifiers on a type and member:</span></span>

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

<span data-ttu-id="a1a7d-115">並非所有存取修飾詞對所有內容中的所有類型或成員都有效。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-115">Not all access modifiers are valid for all types or members in all contexts.</span></span> <span data-ttu-id="a1a7d-116">在某些情況下，類型成員的存取範圍會受限於其包含類型的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-116">In some cases, the accessibility of a type member is constrained by the accessibility of its containing type.</span></span>

## <a name="class-and-struct-accessibility"></a><span data-ttu-id="a1a7d-117">類別和結構存取範圍</span><span class="sxs-lookup"><span data-stu-id="a1a7d-117">Class and struct accessibility</span></span>  

<span data-ttu-id="a1a7d-118">直接在命名空間內宣告的類別和結構 (換句話說，不會嵌套在其他類別或結構中) 可以是 `public` 或 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-118">Classes and structs declared directly within a namespace (in other words, that aren't nested within other classes or structs) can be either `public` or `internal`.</span></span> <span data-ttu-id="a1a7d-119">`internal` 如果未指定存取修飾詞，則為預設值。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-119">`internal` is the default if no access modifier is specified.</span></span>

<span data-ttu-id="a1a7d-120">結構成員（包括嵌套類別和結構）可以宣告為 `public` 、 `internal` 或 `private` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-120">Struct members, including nested classes and structs, can be declared `public`, `internal`, or `private`.</span></span> <span data-ttu-id="a1a7d-121">類別成員（包括嵌套類別和結構）可以是 `public` 、 `protected internal` 、 `protected` 、 `internal` 、 `private protected` 或 `private` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-121">Class members, including nested classes and structs, can be `public`, `protected internal`, `protected`, `internal`, `private protected`, or `private`.</span></span> <span data-ttu-id="a1a7d-122">類別和結構成員（包括嵌套類別和結構） `private` 預設具有存取權。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-122">Class and struct members,  including nested classes and structs, have `private` access by default.</span></span> <span data-ttu-id="a1a7d-123">私用巢狀型別無法從包含類型外部存取。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-123">Private nested types aren't accessible from outside the containing type.</span></span>

<span data-ttu-id="a1a7d-124">衍生類別的存取範圍不能比基底類型更大。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-124">Derived classes can't have greater accessibility than their base types.</span></span> <span data-ttu-id="a1a7d-125">您無法宣告 `B` 衍生自內部類別的公用類別 `A` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-125">You can't declare a public class `B` that derives from an internal class `A`.</span></span> <span data-ttu-id="a1a7d-126">如果允許，則會產生 public 的效果 `A` ，因為所有 `protected` 或 `internal` 成員 `A` 都可以從衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-126">If allowed, it would have the effect of making `A` public, because all `protected` or `internal` members of `A` are accessible from the derived class.</span></span>

<span data-ttu-id="a1a7d-127">您可以使用來啟用特定其他元件，以存取您的內部類型 `InternalsVisibleToAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-127">You can enable specific other assemblies to access your internal types by using the `InternalsVisibleToAttribute`.</span></span> <span data-ttu-id="a1a7d-128">如需詳細資訊，請參閱 [Friend 元件](../../../standard/assembly/friend.md)。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-128">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="class-and-struct-member-accessibility"></a><span data-ttu-id="a1a7d-129">類別和結構成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="a1a7d-129">Class and struct member accessibility</span></span>  

<span data-ttu-id="a1a7d-130">您可使用六種存取類型的任一種，宣告類別成員 (包括巢狀類別和結構)。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-130">Class members (including nested classes and structs) can be declared with any of the six types of access.</span></span> <span data-ttu-id="a1a7d-131">結構成員不可以宣告為 `protected` 、 `protected internal` 或， `private protected` 因為結構不支援繼承。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-131">Struct members can't be declared as `protected`, `protected internal`, or `private protected` because structs don't support inheritance.</span></span>

<span data-ttu-id="a1a7d-132">一般情況下，成員的存取範圍不會大於包含它之類型的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-132">Normally, the accessibility of a member isn't greater than the accessibility of the type that contains it.</span></span> <span data-ttu-id="a1a7d-133">但是， `public` 如果成員執行介面方法或覆寫公用基類中所定義的虛擬方法，則可以從元件外部存取內部類別的成員。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-133">However, a `public` member of an internal class might be accessible from outside the assembly if the member implements interface methods or overrides virtual methods that are defined in a public base class.</span></span>

<span data-ttu-id="a1a7d-134">任何成員欄位、屬性或事件的類型至少必須可以像成員本身一樣存取。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-134">The type of any member field, property, or event must be at least as accessible as the member itself.</span></span> <span data-ttu-id="a1a7d-135">同樣地，任何方法、索引子或委派的傳回型別和參數類型至少必須可以像成員本身一樣存取。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-135">Similarly, the return type and the parameter types of any method, indexer, or delegate must be at least as accessible as the member itself.</span></span> <span data-ttu-id="a1a7d-136">例如， `public` `M` `C` 除非也是，否則您 `C` 不能有傳回類別的方法 `public` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-136">For example, you can't have a `public` method `M` that returns a class `C` unless `C` is also `public`.</span></span> <span data-ttu-id="a1a7d-137">同樣地，如果是宣告為，則您不能具有 `protected` 類型的屬性 `A` `A` `private` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-137">Likewise, you can't have a `protected` property of type `A` if `A` is declared as `private`.</span></span>

<span data-ttu-id="a1a7d-138">使用者定義運算子必須一律宣告為 `public` 和 `static` 。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-138">User-defined operators must always be declared as `public` and `static`.</span></span> <span data-ttu-id="a1a7d-139">如需詳細資訊，請參閱[運算子多載](../../language-reference/operators/operator-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-139">For more information, see [Operator overloading](../../language-reference/operators/operator-overloading.md).</span></span>

<span data-ttu-id="a1a7d-140">完成項不能有存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-140">Finalizers can't have accessibility modifiers.</span></span>

<span data-ttu-id="a1a7d-141">若要設定或成員的存取層級 `class` `struct` ，請在成員宣告中加入適當的關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-141">To set the access level for a `class` or `struct` member, add the appropriate keyword to the member declaration, as shown in the following example.</span></span>

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a><span data-ttu-id="a1a7d-142">其他類型</span><span class="sxs-lookup"><span data-stu-id="a1a7d-142">Other types</span></span>

<span data-ttu-id="a1a7d-143">直接在命名空間內宣告的介面可以是 `public` 或 `internal` ，就像類別和結構一樣，介面預設為 `internal` access。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-143">Interfaces declared directly within a namespace can be `public` or `internal` and, just like classes and structs, interfaces default to `internal` access.</span></span> <span data-ttu-id="a1a7d-144">介面成員預設為， `public` 因為介面的用途是讓其他類型存取類別或結構。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-144">Interface members are `public` by default because the purpose of an interface is to enable other types to access a class or struct.</span></span> <span data-ttu-id="a1a7d-145">介面成員宣告可能包含任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-145">Interface member declarations may include any access modifier.</span></span> <span data-ttu-id="a1a7d-146">這最適用于靜態方法，以提供類別所有實作者所需的常見實作為。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-146">This is most useful for static methods to provide common implementations needed by all implementors of a class.</span></span>

<span data-ttu-id="a1a7d-147">列舉成員一律為 `public` ，而且不能套用任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-147">Enumeration members are always `public`, and no access modifiers can be applied.</span></span>

<span data-ttu-id="a1a7d-148">委派的行為類似類別和結構。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-148">Delegates behave like classes and structs.</span></span> <span data-ttu-id="a1a7d-149">依預設，當您 `internal` 直接在命名空間內宣告時，它們具有存取權，並 `private` 在進行嵌套時存取。</span><span class="sxs-lookup"><span data-stu-id="a1a7d-149">By default, they have `internal` access when declared directly within a namespace, and `private` access when nested.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a1a7d-150">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a1a7d-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="a1a7d-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1a7d-151">See also</span></span>

- [<span data-ttu-id="a1a7d-152">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a1a7d-152">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a1a7d-153">類別和結構</span><span class="sxs-lookup"><span data-stu-id="a1a7d-153">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="a1a7d-154">介面</span><span class="sxs-lookup"><span data-stu-id="a1a7d-154">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="a1a7d-155">私人</span><span class="sxs-lookup"><span data-stu-id="a1a7d-155">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="a1a7d-156">public</span><span class="sxs-lookup"><span data-stu-id="a1a7d-156">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="a1a7d-157">內部</span><span class="sxs-lookup"><span data-stu-id="a1a7d-157">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="a1a7d-158">受保護</span><span class="sxs-lookup"><span data-stu-id="a1a7d-158">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="a1a7d-159">protected internal</span><span class="sxs-lookup"><span data-stu-id="a1a7d-159">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)
- [<span data-ttu-id="a1a7d-160">private protected</span><span class="sxs-lookup"><span data-stu-id="a1a7d-160">private protected</span></span>](../../language-reference/keywords/private-protected.md)
- [<span data-ttu-id="a1a7d-161">class</span><span class="sxs-lookup"><span data-stu-id="a1a7d-161">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="a1a7d-162">結構</span><span class="sxs-lookup"><span data-stu-id="a1a7d-162">struct</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="a1a7d-163">interface</span><span class="sxs-lookup"><span data-stu-id="a1a7d-163">interface</span></span>](../../language-reference/keywords/interface.md)
