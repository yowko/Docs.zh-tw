---
title: 存取修飾詞 - C# 程式設計手冊
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628224"
---
# <a name="access-modifiers-c-programming-guide"></a><span data-ttu-id="039f3-102">存取修飾詞 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="039f3-102">Access Modifiers (C# Programming Guide)</span></span>

<span data-ttu-id="039f3-103">所有類型和類型成員都有協助工具級別。</span><span class="sxs-lookup"><span data-stu-id="039f3-103">All types and type members have an accessibility level.</span></span> <span data-ttu-id="039f3-104">協助工具級別控制它們是否可以從程式集中的其他代碼或其他程式集使用。</span><span class="sxs-lookup"><span data-stu-id="039f3-104">The accessibility level controls whether they can be used from other code in your assembly or other assemblies.</span></span> <span data-ttu-id="039f3-105">在聲明類型或成員時，請使用以下訪問修改器指定其可訪問性：</span><span class="sxs-lookup"><span data-stu-id="039f3-105">Use the following access modifiers to specify the accessibility of a type or member when you declare it:</span></span>

- <span data-ttu-id="039f3-106">[公共](../../language-reference/keywords/public.md)：類型或成員可以由同一程式集中的任何其他代碼或引用它的其他程式集訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-106">[public](../../language-reference/keywords/public.md): The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>
- <span data-ttu-id="039f3-107">[私有](../../language-reference/keywords/private.md)： 類型或成員只能由同`class`一或`struct`中的代碼訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-107">[private](../../language-reference/keywords/private.md): The type or member can be accessed only by code in the same `class` or `struct`.</span></span>
- <span data-ttu-id="039f3-108">[受保護](../../language-reference/keywords/protected.md)： 類型或成員只能由同`class`一中的代碼或`class`派生自 該`class`的代碼訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-108">[protected](../../language-reference/keywords/protected.md): The type or member can be accessed only by code in the same `class`, or in a `class` that is derived from that `class`.</span></span>
- <span data-ttu-id="039f3-109">[內部](../../language-reference/keywords/internal.md)：類型或成員可以由同一程式集中的任何代碼訪問，但不能從其他程式集訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-109">[internal](../../language-reference/keywords/internal.md): The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>
- <span data-ttu-id="039f3-110">[受保護的內部](../../language-reference/keywords/protected-internal.md)：類型或成員可以由聲明它的程式集中的任何代碼訪問，也可以從派生於另一個程式集`class`中訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-110">[protected internal](../../language-reference/keywords/protected-internal.md): The type or member can be accessed by any code in the assembly in which it's declared, or from within a derived `class` in another assembly.</span></span>
- <span data-ttu-id="039f3-111">[私有受保護](../../language-reference/keywords/private-protected.md)： 類型或成員只能在其聲明程式集內、通過相同`class`代碼或派生自該`class`類型的代碼進行訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-111">[private protected](../../language-reference/keywords/private-protected.md): The type or member can be accessed only within its declaring assembly, by code in the same `class` or in a type that is derived from that `class`.</span></span>

<span data-ttu-id="039f3-112">下列範例示範如何指定類型和成員的存取修飾詞︰</span><span class="sxs-lookup"><span data-stu-id="039f3-112">The following examples demonstrate how to specify access modifiers on a type and member:</span></span>

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

<span data-ttu-id="039f3-113">並非所有訪問修改器對所有上下文中的所有類型或成員都有效。</span><span class="sxs-lookup"><span data-stu-id="039f3-113">Not all access modifiers are valid for all types or members in all contexts.</span></span> <span data-ttu-id="039f3-114">在某些情況下，類型成員的可訪問性受其包含類型的可訪問性的限制。</span><span class="sxs-lookup"><span data-stu-id="039f3-114">In some cases, the accessibility of a type member is constrained by the accessibility of its containing type.</span></span>

## <a name="class-and-struct-accessibility"></a><span data-ttu-id="039f3-115">類和結構可訪問性</span><span class="sxs-lookup"><span data-stu-id="039f3-115">Class and struct accessibility</span></span>  

<span data-ttu-id="039f3-116">直接在命名空間內聲明的類和結構（換句話說，不嵌套在其他類或結構中）可以是或`public``internal`。</span><span class="sxs-lookup"><span data-stu-id="039f3-116">Classes and structs declared directly within a namespace (in other words, that aren't nested within other classes or structs) can be either `public` or `internal`.</span></span> <span data-ttu-id="039f3-117">`Internal`如果未指定訪問修改器，則為預設值。</span><span class="sxs-lookup"><span data-stu-id="039f3-117">`Internal` is the default if no access modifier is specified.</span></span>  

<span data-ttu-id="039f3-118">可以聲明 結構成員（包括嵌套類和結構），可以聲明`public`、`internal`或`private`。</span><span class="sxs-lookup"><span data-stu-id="039f3-118">Struct members, including nested classes and structs, can be declared `public`, `internal`, or `private`.</span></span> <span data-ttu-id="039f3-119">類成員（包括嵌套`public`類和結構）可以是 、、、、、、、`internal``private protected``private``protected internal``protected`或 。</span><span class="sxs-lookup"><span data-stu-id="039f3-119">Class members, including nested classes and structs, can be `public`, `protected internal`, `protected`, `internal`, `private protected`, or `private`.</span></span> <span data-ttu-id="039f3-120">預設情況下，類和結構成員（包括嵌套類和結構）具有`private`存取權限。</span><span class="sxs-lookup"><span data-stu-id="039f3-120">Class and struct members,  including nested classes and structs, have `private` access by default.</span></span> <span data-ttu-id="039f3-121">私有巢狀型別無法從包含類型外部訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-121">Private nested types aren't accessible from outside the containing type.</span></span>

<span data-ttu-id="039f3-122">派生類的可訪問性不能大於其基本類型。</span><span class="sxs-lookup"><span data-stu-id="039f3-122">Derived classes can't have greater accessibility than their base types.</span></span> <span data-ttu-id="039f3-123">不能聲明派生自內部類的公共類`B``A`。</span><span class="sxs-lookup"><span data-stu-id="039f3-123">You can't declare a public class `B` that derives from an internal class `A`.</span></span> <span data-ttu-id="039f3-124">如果允許，它會產生`A`公開的效果，因為派生`protected``internal``A`類的所有成員都可以訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-124">If allowed, it would have the effect of making `A` public, because all `protected` or `internal` members of `A` are accessible from the derived class.</span></span>

<span data-ttu-id="039f3-125">可以使用 啟用特定的其他程式集來訪問內部類型`InternalsVisibleToAttribute`。</span><span class="sxs-lookup"><span data-stu-id="039f3-125">You can enable specific other assemblies to access your internal types by using the `InternalsVisibleToAttribute`.</span></span> <span data-ttu-id="039f3-126">有關詳細資訊，請參閱[好友程式集](../../../standard/assembly/friend.md)。</span><span class="sxs-lookup"><span data-stu-id="039f3-126">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="class-and-struct-member-accessibility"></a><span data-ttu-id="039f3-127">類和結構成員可訪問性</span><span class="sxs-lookup"><span data-stu-id="039f3-127">Class and struct member accessibility</span></span>  

<span data-ttu-id="039f3-128">您可使用六種存取類型的任一種，宣告類別成員 (包括巢狀類別和結構)。</span><span class="sxs-lookup"><span data-stu-id="039f3-128">Class members (including nested classes and structs) can be declared with any of the six types of access.</span></span> <span data-ttu-id="039f3-129">不能將結構成員聲明為`protected`，`protected internal`或`private protected`因為結構不支援繼承。</span><span class="sxs-lookup"><span data-stu-id="039f3-129">Struct members can't be declared as `protected`, `protected internal`, or `private protected` because structs don't support inheritance.</span></span>

<span data-ttu-id="039f3-130">通常，成員的可訪問性不大於包含該成員的類型的可訪問性。</span><span class="sxs-lookup"><span data-stu-id="039f3-130">Normally, the accessibility of a member isn't greater than the accessibility of the type that contains it.</span></span> <span data-ttu-id="039f3-131">但是，如果`public`成員實現介面方法或重寫公共基類中定義的虛擬方法，則內部類的成員可以從程式集外部訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-131">However, a `public` member of an internal class might be accessible from outside the assembly if the member implements interface methods or overrides virtual methods that are defined in a public base class.</span></span>

<span data-ttu-id="039f3-132">任何成員欄位、屬性或事件的類型必須至少與成員本身一樣可訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-132">The type of any member field, property, or event must be at least as accessible as the member itself.</span></span> <span data-ttu-id="039f3-133">同樣，任何方法、索引子或委託的返回類型和參數類型必須至少與成員本身一樣可訪問。</span><span class="sxs-lookup"><span data-stu-id="039f3-133">Similarly, the return type and the parameter types of any method, indexer, or delegate must be at least as accessible as the member itself.</span></span> <span data-ttu-id="039f3-134">例如`public`，除非`M``C``C`也是`public`，否則不能有返回類的方法。</span><span class="sxs-lookup"><span data-stu-id="039f3-134">For example, you can't have a `public` method `M` that returns a class `C` unless `C` is also `public`.</span></span> <span data-ttu-id="039f3-135">同樣，如果`protected``A`聲明為`private`，則不能具有類型的`A`屬性。</span><span class="sxs-lookup"><span data-stu-id="039f3-135">Likewise, you can't have a `protected` property of type `A` if `A` is declared as `private`.</span></span>

<span data-ttu-id="039f3-136">使用者定義的運算子必須始終聲明為`public`和`static`。</span><span class="sxs-lookup"><span data-stu-id="039f3-136">User-defined operators must always be declared as `public` and `static`.</span></span> <span data-ttu-id="039f3-137">如需詳細資訊，請參閱[運算子多載](../../language-reference/operators/operator-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="039f3-137">For more information, see [Operator overloading](../../language-reference/operators/operator-overloading.md).</span></span>

<span data-ttu-id="039f3-138">終結者不能具有協助工具修改器。</span><span class="sxs-lookup"><span data-stu-id="039f3-138">Finalizers can't have accessibility modifiers.</span></span>

<span data-ttu-id="039f3-139">要設置`class`或`struct`成員的存取層級，向成員聲明添加相應的關鍵字，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="039f3-139">To set the access level for a `class` or `struct` member, add the appropriate keyword to the member declaration, as shown in the following example.</span></span>

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a><span data-ttu-id="039f3-140">其他類型</span><span class="sxs-lookup"><span data-stu-id="039f3-140">Other types</span></span>

<span data-ttu-id="039f3-141">直接在命名空間中聲明的介面可以是`public`，`internal`並且，就像類和結構一樣，介面預設訪問`internal`。</span><span class="sxs-lookup"><span data-stu-id="039f3-141">Interfaces declared directly within a namespace can be `public` or `internal` and, just like classes and structs, interfaces default to `internal` access.</span></span> <span data-ttu-id="039f3-142">預設情況下，介面`public`成員是因為介面的目的是使其他類型的類型能夠訪問類或結構。</span><span class="sxs-lookup"><span data-stu-id="039f3-142">Interface members are `public` by default because the purpose of an interface is to enable other types to access a class or struct.</span></span> <span data-ttu-id="039f3-143">介面成員聲明可以包括任何訪問修改器。</span><span class="sxs-lookup"><span data-stu-id="039f3-143">Interface member declarations may include any access modifier.</span></span> <span data-ttu-id="039f3-144">這對於靜態方法最有用，用於提供類的所有實現者所需的常見實現。</span><span class="sxs-lookup"><span data-stu-id="039f3-144">This is most useful for static methods to provide common implementations needed by all implementors of a class.</span></span>

<span data-ttu-id="039f3-145">枚舉成員始終`public`為 ，並且不能應用訪問修改器。</span><span class="sxs-lookup"><span data-stu-id="039f3-145">Enumeration members are always `public`, and no access modifiers can be applied.</span></span>

<span data-ttu-id="039f3-146">委派的行為類似類別和結構。</span><span class="sxs-lookup"><span data-stu-id="039f3-146">Delegates behave like classes and structs.</span></span> <span data-ttu-id="039f3-147">預設情況下，它們在命名`internal`空間內直接聲明時具有存取權限，在`private`嵌套時具有存取權限。</span><span class="sxs-lookup"><span data-stu-id="039f3-147">By default, they have `internal` access when declared directly within a namespace, and `private` access when nested.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="039f3-148">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="039f3-148">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="039f3-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="039f3-149">See also</span></span>

- [<span data-ttu-id="039f3-150">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="039f3-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="039f3-151">類別和結構</span><span class="sxs-lookup"><span data-stu-id="039f3-151">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="039f3-152">介面</span><span class="sxs-lookup"><span data-stu-id="039f3-152">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="039f3-153">私人</span><span class="sxs-lookup"><span data-stu-id="039f3-153">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="039f3-154">public</span><span class="sxs-lookup"><span data-stu-id="039f3-154">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="039f3-155">內部</span><span class="sxs-lookup"><span data-stu-id="039f3-155">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="039f3-156">保護</span><span class="sxs-lookup"><span data-stu-id="039f3-156">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="039f3-157">protected internal</span><span class="sxs-lookup"><span data-stu-id="039f3-157">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)
- [<span data-ttu-id="039f3-158">private protected</span><span class="sxs-lookup"><span data-stu-id="039f3-158">private protected</span></span>](../../language-reference/keywords/private-protected.md)
- [<span data-ttu-id="039f3-159">class</span><span class="sxs-lookup"><span data-stu-id="039f3-159">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="039f3-160">struct</span><span class="sxs-lookup"><span data-stu-id="039f3-160">struct</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="039f3-161">介面</span><span class="sxs-lookup"><span data-stu-id="039f3-161">interface</span></span>](../../language-reference/keywords/interface.md)
