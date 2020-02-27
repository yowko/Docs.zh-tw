---
title: 存取修飾詞 - C# 程式設計手冊
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628224"
---
# <a name="access-modifiers-c-programming-guide"></a><span data-ttu-id="c68b9-102">存取修飾詞 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c68b9-102">Access Modifiers (C# Programming Guide)</span></span>

<span data-ttu-id="c68b9-103">所有類型和類型成員都具有存取範圍層級。</span><span class="sxs-lookup"><span data-stu-id="c68b9-103">All types and type members have an accessibility level.</span></span> <span data-ttu-id="c68b9-104">存取範圍層級控制是否可以從元件或其他元件中的其他程式碼使用它們。</span><span class="sxs-lookup"><span data-stu-id="c68b9-104">The accessibility level controls whether they can be used from other code in your assembly or other assemblies.</span></span> <span data-ttu-id="c68b9-105">當您宣告類型或成員時，請使用下列存取修飾詞來指定其存取範圍：</span><span class="sxs-lookup"><span data-stu-id="c68b9-105">Use the following access modifiers to specify the accessibility of a type or member when you declare it:</span></span>

- <span data-ttu-id="c68b9-106">[public](../../language-reference/keywords/public.md)：類型或成員可由相同元件中的任何其他程式碼或參考它的另一個元件來存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-106">[public](../../language-reference/keywords/public.md): The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>
- <span data-ttu-id="c68b9-107">[私](../../language-reference/keywords/private.md)用：類型或成員只能由相同 `class` 或 `struct`中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-107">[private](../../language-reference/keywords/private.md): The type or member can be accessed only by code in the same `class` or `struct`.</span></span>
- <span data-ttu-id="c68b9-108">[protected](../../language-reference/keywords/protected.md)：類型或成員只能由相同 `class`中的程式碼或衍生自該 `class`的 `class` 存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-108">[protected](../../language-reference/keywords/protected.md): The type or member can be accessed only by code in the same `class`, or in a `class` that is derived from that `class`.</span></span>
- <span data-ttu-id="c68b9-109">[內部](../../language-reference/keywords/internal.md)：類型或成員可由相同元件中的任何程式碼存取，但不能由另一個元件存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-109">[internal](../../language-reference/keywords/internal.md): The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>
- <span data-ttu-id="c68b9-110">[protected internal](../../language-reference/keywords/protected-internal.md)：類型或成員可由其宣告所在之元件中的任何程式碼存取，或從另一個元件中的衍生 `class`。</span><span class="sxs-lookup"><span data-stu-id="c68b9-110">[protected internal](../../language-reference/keywords/protected-internal.md): The type or member can be accessed by any code in the assembly in which it's declared, or from within a derived `class` in another assembly.</span></span>
- <span data-ttu-id="c68b9-111">[私用保護](../../language-reference/keywords/private-protected.md)：類型或成員只能在其宣告元件、相同 `class` 中的程式碼或衍生自該 `class`的類型中存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-111">[private protected](../../language-reference/keywords/private-protected.md): The type or member can be accessed only within its declaring assembly, by code in the same `class` or in a type that is derived from that `class`.</span></span>

<span data-ttu-id="c68b9-112">下列範例示範如何指定類型和成員的存取修飾詞︰</span><span class="sxs-lookup"><span data-stu-id="c68b9-112">The following examples demonstrate how to specify access modifiers on a type and member:</span></span>

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

<span data-ttu-id="c68b9-113">並非所有的存取修飾詞對所有內容中的所有類型或成員都有效。</span><span class="sxs-lookup"><span data-stu-id="c68b9-113">Not all access modifiers are valid for all types or members in all contexts.</span></span> <span data-ttu-id="c68b9-114">在某些情況下，類型成員的存取範圍會受到其包含類型的存取範圍所限制。</span><span class="sxs-lookup"><span data-stu-id="c68b9-114">In some cases, the accessibility of a type member is constrained by the accessibility of its containing type.</span></span>

## <a name="class-and-struct-accessibility"></a><span data-ttu-id="c68b9-115">類別和結構協助工具</span><span class="sxs-lookup"><span data-stu-id="c68b9-115">Class and struct accessibility</span></span>  

<span data-ttu-id="c68b9-116">直接在命名空間內宣告的類別和結構（換句話說，不是在其他類別或結構內）可以是 `public` 或 `internal`。</span><span class="sxs-lookup"><span data-stu-id="c68b9-116">Classes and structs declared directly within a namespace (in other words, that aren't nested within other classes or structs) can be either `public` or `internal`.</span></span> <span data-ttu-id="c68b9-117">如果未指定任何存取修飾詞，`Internal` 是預設值。</span><span class="sxs-lookup"><span data-stu-id="c68b9-117">`Internal` is the default if no access modifier is specified.</span></span>  

<span data-ttu-id="c68b9-118">結構成員（包括嵌套類別和結構）可以 `public`、`internal`或 `private`來宣告。</span><span class="sxs-lookup"><span data-stu-id="c68b9-118">Struct members, including nested classes and structs, can be declared `public`, `internal`, or `private`.</span></span> <span data-ttu-id="c68b9-119">類別成員（包括嵌套類別和結構）可以是 `public`、`protected internal`、`protected`、`internal`、`private protected`或 `private`。</span><span class="sxs-lookup"><span data-stu-id="c68b9-119">Class members, including nested classes and structs, can be `public`, `protected internal`, `protected`, `internal`, `private protected`, or `private`.</span></span> <span data-ttu-id="c68b9-120">類別和結構成員（包括嵌套類別和結構）預設具有 `private` 存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-120">Class and struct members,  including nested classes and structs, have `private` access by default.</span></span> <span data-ttu-id="c68b9-121">無法從包含類型外部存取私用的巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="c68b9-121">Private nested types aren't accessible from outside the containing type.</span></span>

<span data-ttu-id="c68b9-122">衍生類別的存取範圍無法高於其基底類型。</span><span class="sxs-lookup"><span data-stu-id="c68b9-122">Derived classes can't have greater accessibility than their base types.</span></span> <span data-ttu-id="c68b9-123">您無法宣告衍生自內部類別 `A`的公用類別 `B`。</span><span class="sxs-lookup"><span data-stu-id="c68b9-123">You can't declare a public class `B` that derives from an internal class `A`.</span></span> <span data-ttu-id="c68b9-124">如果允許，則會產生 `A` public 的效果，因為 `A` 的所有 `protected` 或 `internal` 成員都可以從衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-124">If allowed, it would have the effect of making `A` public, because all `protected` or `internal` members of `A` are accessible from the derived class.</span></span>

<span data-ttu-id="c68b9-125">您可以使用 `InternalsVisibleToAttribute`，讓特定的其他元件存取您的內部類型。</span><span class="sxs-lookup"><span data-stu-id="c68b9-125">You can enable specific other assemblies to access your internal types by using the `InternalsVisibleToAttribute`.</span></span> <span data-ttu-id="c68b9-126">如需詳細資訊，請參閱 [Friend Assemblies](../../../standard/assembly/friend.md) (Friend 組件)。</span><span class="sxs-lookup"><span data-stu-id="c68b9-126">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="class-and-struct-member-accessibility"></a><span data-ttu-id="c68b9-127">類別和結構成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="c68b9-127">Class and struct member accessibility</span></span>  

<span data-ttu-id="c68b9-128">您可使用六種存取類型的任一種，宣告類別成員 (包括巢狀類別和結構)。</span><span class="sxs-lookup"><span data-stu-id="c68b9-128">Class members (including nested classes and structs) can be declared with any of the six types of access.</span></span> <span data-ttu-id="c68b9-129">結構成員不能宣告為 `protected`、`protected internal`或 `private protected`，因為結構不支援繼承。</span><span class="sxs-lookup"><span data-stu-id="c68b9-129">Struct members can't be declared as `protected`, `protected internal`, or `private protected` because structs don't support inheritance.</span></span>

<span data-ttu-id="c68b9-130">一般來說，成員的存取範圍不會大於包含它之類型的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="c68b9-130">Normally, the accessibility of a member isn't greater than the accessibility of the type that contains it.</span></span> <span data-ttu-id="c68b9-131">不過，如果成員執行介面方法或覆寫在公用基類中定義的虛擬方法，則內部類別的 `public` 成員可能可以從元件外部存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-131">However, a `public` member of an internal class might be accessible from outside the assembly if the member implements interface methods or overrides virtual methods that are defined in a public base class.</span></span>

<span data-ttu-id="c68b9-132">任何成員欄位、屬性或事件的類型，都必須至少與成員本身一樣可以存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-132">The type of any member field, property, or event must be at least as accessible as the member itself.</span></span> <span data-ttu-id="c68b9-133">同樣地，任何方法、索引子或委派的傳回型別和參數類型，都必須至少與成員本身一樣可以存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-133">Similarly, the return type and the parameter types of any method, indexer, or delegate must be at least as accessible as the member itself.</span></span> <span data-ttu-id="c68b9-134">例如，除非也 `public``C`，否則您不能有傳回類別 `C` 的 `public` 方法 `M`。</span><span class="sxs-lookup"><span data-stu-id="c68b9-134">For example, you can't have a `public` method `M` that returns a class `C` unless `C` is also `public`.</span></span> <span data-ttu-id="c68b9-135">同樣地，如果 `A` 宣告為 `private`，您就不能有 `A` 類型的 `protected` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c68b9-135">Likewise, you can't have a `protected` property of type `A` if `A` is declared as `private`.</span></span>

<span data-ttu-id="c68b9-136">使用者定義的運算子必須一律宣告為 `public` 和 `static`。</span><span class="sxs-lookup"><span data-stu-id="c68b9-136">User-defined operators must always be declared as `public` and `static`.</span></span> <span data-ttu-id="c68b9-137">如需詳細資訊，請參閱[運算子多載](../../language-reference/operators/operator-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="c68b9-137">For more information, see [Operator overloading](../../language-reference/operators/operator-overloading.md).</span></span>

<span data-ttu-id="c68b9-138">完成項不能有存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="c68b9-138">Finalizers can't have accessibility modifiers.</span></span>

<span data-ttu-id="c68b9-139">若要設定 `class` 或 `struct` 成員的存取層級，請將適當的關鍵字新增至成員宣告，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c68b9-139">To set the access level for a `class` or `struct` member, add the appropriate keyword to the member declaration, as shown in the following example.</span></span>

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a><span data-ttu-id="c68b9-140">其他類型</span><span class="sxs-lookup"><span data-stu-id="c68b9-140">Other types</span></span>

<span data-ttu-id="c68b9-141">直接在命名空間內宣告的介面可以 `public` 或 `internal`，而且就像類別和結構一樣，介面預設為 `internal` 存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-141">Interfaces declared directly within a namespace can be `public` or `internal` and, just like classes and structs, interfaces default to `internal` access.</span></span> <span data-ttu-id="c68b9-142">預設會 `public` 介面成員，因為介面的目的是要讓其他類型可以存取類別或結構。</span><span class="sxs-lookup"><span data-stu-id="c68b9-142">Interface members are `public` by default because the purpose of an interface is to enable other types to access a class or struct.</span></span> <span data-ttu-id="c68b9-143">介面成員宣告可能包含任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="c68b9-143">Interface member declarations may include any access modifier.</span></span> <span data-ttu-id="c68b9-144">這最適用于靜態方法，以提供類別的所有實作者所需的一般程式。</span><span class="sxs-lookup"><span data-stu-id="c68b9-144">This is most useful for static methods to provide common implementations needed by all implementors of a class.</span></span>

<span data-ttu-id="c68b9-145">列舉成員一律 `public`，而且不能套用任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="c68b9-145">Enumeration members are always `public`, and no access modifiers can be applied.</span></span>

<span data-ttu-id="c68b9-146">委派的行為類似類別和結構。</span><span class="sxs-lookup"><span data-stu-id="c68b9-146">Delegates behave like classes and structs.</span></span> <span data-ttu-id="c68b9-147">根據預設，當直接在命名空間中宣告時，它們會有 `internal` 的存取權，並在進行嵌套時 `private` 存取。</span><span class="sxs-lookup"><span data-stu-id="c68b9-147">By default, they have `internal` access when declared directly within a namespace, and `private` access when nested.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c68b9-148">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c68b9-148">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="c68b9-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c68b9-149">See also</span></span>

- [<span data-ttu-id="c68b9-150">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c68b9-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c68b9-151">類別和結構</span><span class="sxs-lookup"><span data-stu-id="c68b9-151">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="c68b9-152">介面</span><span class="sxs-lookup"><span data-stu-id="c68b9-152">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="c68b9-153">private</span><span class="sxs-lookup"><span data-stu-id="c68b9-153">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="c68b9-154">public</span><span class="sxs-lookup"><span data-stu-id="c68b9-154">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="c68b9-155">internal</span><span class="sxs-lookup"><span data-stu-id="c68b9-155">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="c68b9-156">protected</span><span class="sxs-lookup"><span data-stu-id="c68b9-156">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="c68b9-157">protected internal</span><span class="sxs-lookup"><span data-stu-id="c68b9-157">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)
- [<span data-ttu-id="c68b9-158">private protected</span><span class="sxs-lookup"><span data-stu-id="c68b9-158">private protected</span></span>](../../language-reference/keywords/private-protected.md)
- [<span data-ttu-id="c68b9-159">class</span><span class="sxs-lookup"><span data-stu-id="c68b9-159">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="c68b9-160">struct</span><span class="sxs-lookup"><span data-stu-id="c68b9-160">struct</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="c68b9-161">interface</span><span class="sxs-lookup"><span data-stu-id="c68b9-161">interface</span></span>](../../language-reference/keywords/interface.md)
