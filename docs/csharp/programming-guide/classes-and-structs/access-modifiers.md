---
title: 存取修飾詞 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: b415bf143e7da46b3ecd2c0828a3f8151878435a
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971672"
---
# <a name="access-modifiers-c-programming-guide"></a><span data-ttu-id="e553f-102">存取修飾詞 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e553f-102">Access Modifiers (C# Programming Guide)</span></span>
<span data-ttu-id="e553f-103">所有類型和類型成員都具有存取範圍層級，以控制是否可以從組件中的其他程式碼或其他組件中使用它們。</span><span class="sxs-lookup"><span data-stu-id="e553f-103">All types and type members have an accessibility level, which controls whether they can be used from other code in your assembly or other assemblies.</span></span> <span data-ttu-id="e553f-104">您可以使用下列存取修飾詞，以在宣告類型或成員時指定其存取範圍：</span><span class="sxs-lookup"><span data-stu-id="e553f-104">You can use the following access modifiers to specify the accessibility of a type or member when you declare it:</span></span>  
  
 [<span data-ttu-id="e553f-105">public</span><span class="sxs-lookup"><span data-stu-id="e553f-105">public</span></span>](../../language-reference/keywords/public.md)  
 <span data-ttu-id="e553f-106">類型或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="e553f-106">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> 
  
 [<span data-ttu-id="e553f-107">private</span><span class="sxs-lookup"><span data-stu-id="e553f-107">private</span></span>](../../language-reference/keywords/private.md)  
 <span data-ttu-id="e553f-108">類型或成員只能由相同類別或結構中的程式碼進行存取。</span><span class="sxs-lookup"><span data-stu-id="e553f-108">The type or member can be accessed only by code in the same class or struct.</span></span>  
  
 [<span data-ttu-id="e553f-109">protected</span><span class="sxs-lookup"><span data-stu-id="e553f-109">protected</span></span>](../../language-reference/keywords/protected.md)  
 <span data-ttu-id="e553f-110">類型或成員只可由相同類別或衍生自該類別之類別中的程式碼進行存取。</span><span class="sxs-lookup"><span data-stu-id="e553f-110">The type or member can be accessed only by code in the same class, or in a class that is derived from that class.</span></span>  
 [<span data-ttu-id="e553f-111">internal</span><span class="sxs-lookup"><span data-stu-id="e553f-111">internal</span></span>](../../language-reference/keywords/internal.md)  
 <span data-ttu-id="e553f-112">類型或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e553f-112">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>  
  
 <span data-ttu-id="e553f-113">[protected internal](../../language-reference/keywords/protected-internal.md) 類型或成員可由宣告程式碼的組件內之任一程式碼存取，或是從另一個組件中的衍生類別內存取。</span><span class="sxs-lookup"><span data-stu-id="e553f-113">[protected internal](../../language-reference/keywords/protected-internal.md) The type or member can be accessed by any code in the assembly in which it is declared, or from within a derived class in another assembly.</span></span> 

 <span data-ttu-id="e553f-114">[private protected](../../language-reference/keywords/private-protected.md) 類型或成員只可從其宣告組件內存取，或是從衍生自該類別之相同類別或類型的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="e553f-114">[private protected](../../language-reference/keywords/private-protected.md) The type or member can be accessed only within its declaring assembly, by code in the same class or in a type that is derived from that class.</span></span>
  
 <span data-ttu-id="e553f-115">下列範例示範如何指定類型和成員的存取修飾詞︰</span><span class="sxs-lookup"><span data-stu-id="e553f-115">The following examples demonstrate how to specify access modifiers on a type and member:</span></span>  
  
 [!code-csharp[csProgGuideObjects#72](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#72)]  
  
 <span data-ttu-id="e553f-116">並非所有存取修飾詞都可以供所有類型或成員在所有內容中使用；而且，在某些情況下，類型成員的存取範圍會受限於其包含類型的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="e553f-116">Not all access modifiers can be used by all types or members in all contexts, and in some cases the accessibility of a type member is constrained by the accessibility of its containing type.</span></span> <span data-ttu-id="e553f-117">下列各節提供存取範圍的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e553f-117">The following sections provide more details about accessibility.</span></span>  
  
## <a name="class-and-struct-accessibility"></a><span data-ttu-id="e553f-118">類別和結構存取範圍</span><span class="sxs-lookup"><span data-stu-id="e553f-118">Class and Struct Accessibility</span></span>  
 <span data-ttu-id="e553f-119">直接在命名空間內宣告的類別和結構 (換句話說，未巢狀在其他類別或結構內) 可以是 public 或 internal。</span><span class="sxs-lookup"><span data-stu-id="e553f-119">Classes and structs that are declared directly within a namespace (in other words, that are not nested within other classes or structs) can be either public or internal.</span></span> <span data-ttu-id="e553f-120">如果未指定任何存取修飾詞，則 internal 是預設值。</span><span class="sxs-lookup"><span data-stu-id="e553f-120">Internal is the default if no access modifier is specified.</span></span>  
  
 <span data-ttu-id="e553f-121">結構成員 (包括巢狀類別和結構) 可以宣告為 public、internal 或 private。</span><span class="sxs-lookup"><span data-stu-id="e553f-121">Struct members, including nested classes and structs, can be declared as public, internal, or private.</span></span> <span data-ttu-id="e553f-122">類別成員，包含巢狀類別和結構，可為 public、protected internal、protected、internal、private protected 或 private。</span><span class="sxs-lookup"><span data-stu-id="e553f-122">Class members, including nested classes and structs, can be public, protected internal, protected, internal, private protected or private.</span></span> <span data-ttu-id="e553f-123">類別成員和結構成員 (包括巢狀類別和結構) 的存取層級預設為 private。</span><span class="sxs-lookup"><span data-stu-id="e553f-123">The access level for class members and struct members, including nested classes and structs, is private by default.</span></span> <span data-ttu-id="e553f-124">無法從包含類型外部存取私用巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="e553f-124">Private nested types are not accessible from outside the containing type.</span></span>  
  
 <span data-ttu-id="e553f-125">衍生類別的存取範圍不能大於其基底類型。</span><span class="sxs-lookup"><span data-stu-id="e553f-125">Derived classes cannot have greater accessibility than their base types.</span></span> <span data-ttu-id="e553f-126">換句話說，您不能有衍生自內部類別 `A` 的公用類別 `B`。</span><span class="sxs-lookup"><span data-stu-id="e553f-126">In other words, you cannot have a public class `B` that derives from an internal class `A`.</span></span> <span data-ttu-id="e553f-127">因為 `A` 的所有 protected 或 internal 成員都可以從衍生類別進行存取，所以如果允許這樣做，則會有將 `A` 設為 public 的效果。</span><span class="sxs-lookup"><span data-stu-id="e553f-127">If this were allowed, it would have the effect of making `A` public, because all protected or internal members of `A` are accessible from the derived class.</span></span>  
  
 <span data-ttu-id="e553f-128">您可以使用 InternalsVisibleToAttribute 來啟用特定其他組件存取您的內部類型。</span><span class="sxs-lookup"><span data-stu-id="e553f-128">You can enable specific other assemblies to access your internal types by using the InternalsVisibleToAttribute.</span></span> <span data-ttu-id="e553f-129">如需詳細資訊，請參閱 [Friend Assemblies](../../../standard/assembly/friend.md) (Friend 組件)。</span><span class="sxs-lookup"><span data-stu-id="e553f-129">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
## <a name="class-and-struct-member-accessibility"></a><span data-ttu-id="e553f-130">類別和結構成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="e553f-130">Class and Struct Member Accessibility</span></span>  
 <span data-ttu-id="e553f-131">您可使用六種存取類型的任一種，宣告類別成員 (包括巢狀類別和結構)。</span><span class="sxs-lookup"><span data-stu-id="e553f-131">Class members (including nested classes and structs) can be declared with any of the six types of access.</span></span> <span data-ttu-id="e553f-132">因為結構不支援繼承，所以無法將結構成員宣告為 protected。</span><span class="sxs-lookup"><span data-stu-id="e553f-132">Struct members cannot be declared as protected because structs do not support inheritance.</span></span>  
  
 <span data-ttu-id="e553f-133">一般而言，成員存取範圍不會大於包含它之類型的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="e553f-133">Normally, the accessibility of a member is not greater than the accessibility of the type that contains it.</span></span> <span data-ttu-id="e553f-134">不過，如果成員實作介面方法，或覆寫公用基底類別中所定義的虛擬方法，則可以從組件外部存取內部類別的公用成員。</span><span class="sxs-lookup"><span data-stu-id="e553f-134">However, a public member of an internal class might be accessible from outside the assembly if the member implements interface methods or overrides virtual methods that are defined in a public base class.</span></span>  
  
 <span data-ttu-id="e553f-135">為欄位、屬性或事件之任何成員的類型必須至少與成員本身一樣可進行存取。</span><span class="sxs-lookup"><span data-stu-id="e553f-135">The type of any member that is a field, property, or event must be at least as accessible as the member itself.</span></span> <span data-ttu-id="e553f-136">同樣地，傳回型別以及本身為方法、索引子或委派之任何成員的參數類型都必須至少像該成員本身一樣可供存取。</span><span class="sxs-lookup"><span data-stu-id="e553f-136">Similarly, the return type and the parameter types of any member that is a method, indexer, or delegate must be at least as accessible as the member itself.</span></span> <span data-ttu-id="e553f-137">例如，除非 `C` 也是公用的，否則您無法有傳回 `C` 類別的公用方法 `M`。</span><span class="sxs-lookup"><span data-stu-id="e553f-137">For example, you cannot have a public method `M` that returns a class `C` unless `C` is also public.</span></span> <span data-ttu-id="e553f-138">同樣地，如果將 `A` 宣告為 private，則您不能有 `A` 類型的 protected 屬性。</span><span class="sxs-lookup"><span data-stu-id="e553f-138">Likewise, you cannot have a protected property of type `A` if `A` is declared as private.</span></span>  
  
 <span data-ttu-id="e553f-139">使用者定義的運算子必須一律宣告為 public 和 static。</span><span class="sxs-lookup"><span data-stu-id="e553f-139">User-defined operators must always be declared as public and static.</span></span> <span data-ttu-id="e553f-140">如需詳細資訊，請參閱[運算子多載](../../language-reference/operators/operator-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="e553f-140">For more information, see [Operator overloading](../../language-reference/operators/operator-overloading.md).</span></span>  
  
 <span data-ttu-id="e553f-141">完成項不能有存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="e553f-141">Finalizers cannot have accessibility modifiers.</span></span>  
  
 <span data-ttu-id="e553f-142">若要設定類別或結構成員的存取層級，請在成員宣告中新增適當的關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e553f-142">To set the access level for a class or struct member, add the appropriate keyword to the member declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideObjects#73](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#73)]  
  
> [!NOTE]
> <span data-ttu-id="e553f-143">protected internal 存取範圍層級表示「protected 或 internal」，而非「protected 和 internal」。</span><span class="sxs-lookup"><span data-stu-id="e553f-143">The protected internal accessibility level means protected OR internal, not protected AND internal.</span></span> <span data-ttu-id="e553f-144">換句話說，可以從相同組件的任何類別 (包括衍生類別) 中存取 protected internal 成員。</span><span class="sxs-lookup"><span data-stu-id="e553f-144">In other words, a protected internal member can be accessed from any class in the same assembly, including derived classes.</span></span> <span data-ttu-id="e553f-145">若要僅限於相同組件中衍生類別的存取範圍，請將類別本身宣告為 internal，並將它的成員宣告為 protected。</span><span class="sxs-lookup"><span data-stu-id="e553f-145">To limit accessibility to only derived classes in the same assembly, declare the class itself internal, and declare its members as protected.</span></span> <span data-ttu-id="e553f-146">此外，從 C# 7.2 開始，您可使用 private protected 存取修飾詞來達到相同的結果，而無須將包含的類別設為 internal。</span><span class="sxs-lookup"><span data-stu-id="e553f-146">Also, starting with C# 7.2, you can use the private protected access modifier to achieve the same result without need to make the containing class internal.</span></span>  
  
## <a name="other-types"></a><span data-ttu-id="e553f-147">其他類型</span><span class="sxs-lookup"><span data-stu-id="e553f-147">Other Types</span></span>  
 <span data-ttu-id="e553f-148">直接在命名空間內宣告的介面可以宣告為 public 或 internal；而且，就像類別和結構，介面預設為內部存取。</span><span class="sxs-lookup"><span data-stu-id="e553f-148">Interfaces declared directly within a namespace can be declared as public or internal and, just like classes and structs, interfaces default to internal access.</span></span> <span data-ttu-id="e553f-149">介面成員一律都是 public，因為介面的目的是要讓其他類型存取類別或結構。</span><span class="sxs-lookup"><span data-stu-id="e553f-149">Interface members are always public because the purpose of an interface is to enable other types to access a class or struct.</span></span> <span data-ttu-id="e553f-150">沒有存取修飾詞可以套用至介面成員。</span><span class="sxs-lookup"><span data-stu-id="e553f-150">No access modifiers can be applied to interface members.</span></span>  
  
 <span data-ttu-id="e553f-151">列舉成員一律為 public，因此無法套用任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="e553f-151">Enumeration members are always public, and no access modifiers can be applied.</span></span>  
  
 <span data-ttu-id="e553f-152">委派的行為類似類別和結構。</span><span class="sxs-lookup"><span data-stu-id="e553f-152">Delegates behave like classes and structs.</span></span> <span data-ttu-id="e553f-153">根據預設，它們在直接在命名空間內宣告時會具有 internal 存取，而且在巢狀時會具有 private 存取。</span><span class="sxs-lookup"><span data-stu-id="e553f-153">By default, they have internal access when declared directly within a namespace, and private access when nested.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e553f-154">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e553f-154">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e553f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e553f-155">See also</span></span>

- [<span data-ttu-id="e553f-156">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e553f-156">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e553f-157">類別和結構</span><span class="sxs-lookup"><span data-stu-id="e553f-157">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e553f-158">介面</span><span class="sxs-lookup"><span data-stu-id="e553f-158">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="e553f-159">private</span><span class="sxs-lookup"><span data-stu-id="e553f-159">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="e553f-160">public</span><span class="sxs-lookup"><span data-stu-id="e553f-160">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="e553f-161">internal</span><span class="sxs-lookup"><span data-stu-id="e553f-161">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="e553f-162">protected</span><span class="sxs-lookup"><span data-stu-id="e553f-162">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="e553f-163">protected internal</span><span class="sxs-lookup"><span data-stu-id="e553f-163">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)
- [<span data-ttu-id="e553f-164">private protected</span><span class="sxs-lookup"><span data-stu-id="e553f-164">private protected</span></span>](../../language-reference/keywords/private-protected.md)
- [<span data-ttu-id="e553f-165">class</span><span class="sxs-lookup"><span data-stu-id="e553f-165">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="e553f-166">struct</span><span class="sxs-lookup"><span data-stu-id="e553f-166">struct</span></span>](../../language-reference/keywords/struct.md)
- [<span data-ttu-id="e553f-167">interface</span><span class="sxs-lookup"><span data-stu-id="e553f-167">interface</span></span>](../../language-reference/keywords/interface.md)
