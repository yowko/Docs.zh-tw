---
title: "存取修飾詞 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 38b259b4d85d54467cd15cd49e5987f6198e8d99
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="access-modifiers-c-programming-guide"></a><span data-ttu-id="e20ba-102">存取修飾詞 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e20ba-102">Access Modifiers (C# Programming Guide)</span></span>
<span data-ttu-id="e20ba-103">所有類型和類型成員都具有存取範圍層級，以控制是否可以從組件中的其他程式碼或其他組件中使用它們。</span><span class="sxs-lookup"><span data-stu-id="e20ba-103">All types and type members have an accessibility level, which controls whether they can be used from other code in your assembly or other assemblies.</span></span> <span data-ttu-id="e20ba-104">您可以使用下列存取修飾詞，以在宣告類型或成員時指定其存取範圍：</span><span class="sxs-lookup"><span data-stu-id="e20ba-104">You can use the following access modifiers to specify the accessibility of a type or member when you declare it:</span></span>  
  
 [<span data-ttu-id="e20ba-105">public</span><span class="sxs-lookup"><span data-stu-id="e20ba-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 <span data-ttu-id="e20ba-106">類型或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="e20ba-106">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>  
  
 [<span data-ttu-id="e20ba-107">private</span><span class="sxs-lookup"><span data-stu-id="e20ba-107">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 <span data-ttu-id="e20ba-108">類型或成員只能由相同類別或結構中的程式碼進行存取。</span><span class="sxs-lookup"><span data-stu-id="e20ba-108">The type or member can be accessed only by code in the same class or struct.</span></span>  
  
 [<span data-ttu-id="e20ba-109">protected</span><span class="sxs-lookup"><span data-stu-id="e20ba-109">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 <span data-ttu-id="e20ba-110">類型或成員只能由相同類別或結構中或衍生自該類別之類別中的程式碼進行存取。</span><span class="sxs-lookup"><span data-stu-id="e20ba-110">The type or member can be accessed only by code in the same class or struct, or in a class that is derived from that class.</span></span>  
  
 [<span data-ttu-id="e20ba-111">internal</span><span class="sxs-lookup"><span data-stu-id="e20ba-111">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="e20ba-112">類型或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e20ba-112">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>  
  
 `protected internal`  
 <span data-ttu-id="e20ba-113">類型或成員可以由宣告它的組件中的任何程式碼或從其他組件中的衍生類別進行存取。</span><span class="sxs-lookup"><span data-stu-id="e20ba-113">The type or member can be accessed by any code in the assembly in which it is declared, or from within a derived class in another assembly.</span></span> <span data-ttu-id="e20ba-114">從其他組件中的存取必須在衍生自宣告 protected internal 項目之類別的類別宣告中進行，而且必須透過衍生類別類型的執行個體進行。</span><span class="sxs-lookup"><span data-stu-id="e20ba-114">Access from another assembly must take place within a class declaration that derives from the class in which the protected internal element is declared, and it must take place through an instance of the derived class type.</span></span>  
  
 <span data-ttu-id="e20ba-115">下列範例示範如何指定類型和成員的存取修飾詞︰</span><span class="sxs-lookup"><span data-stu-id="e20ba-115">The following examples demonstrate how to specify access modifiers on a type and member:</span></span>  
  
 <span data-ttu-id="e20ba-116">[!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e20ba-116">[!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]</span></span>  
  
 <span data-ttu-id="e20ba-117">並非所有存取修飾詞都可以供所有類型或成員在所有內容中使用；而且，在某些情況下，類型成員的存取範圍會受限於其包含類型的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="e20ba-117">Not all access modifiers can be used by all types or members in all contexts, and in some cases the accessibility of a type member is constrained by the accessibility of its containing type.</span></span> <span data-ttu-id="e20ba-118">下列各節提供存取範圍的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e20ba-118">The following sections provide more details about accessibility.</span></span>  
  
## <a name="class-and-struct-accessibility"></a><span data-ttu-id="e20ba-119">類別和結構存取範圍</span><span class="sxs-lookup"><span data-stu-id="e20ba-119">Class and Struct Accessibility</span></span>  
 <span data-ttu-id="e20ba-120">直接在命名空間內宣告的類別和結構 (換句話說，未巢狀在其他類別或結構內) 可以是 public 或 internal。</span><span class="sxs-lookup"><span data-stu-id="e20ba-120">Classes and structs that are declared directly within a namespace (in other words, that are not nested within other classes or structs) can be either public or internal.</span></span> <span data-ttu-id="e20ba-121">如果未指定任何存取修飾詞，則 internal 是預設值。</span><span class="sxs-lookup"><span data-stu-id="e20ba-121">Internal is the default if no access modifier is specified.</span></span>  
  
 <span data-ttu-id="e20ba-122">結構成員 (包括巢狀類別和結構) 可以宣告為 public、internal 或 private。</span><span class="sxs-lookup"><span data-stu-id="e20ba-122">Struct members, including nested classes and structs, can be declared as public, internal, or private.</span></span> <span data-ttu-id="e20ba-123">類別成員 (包括巢狀類別和結構) 可以是 public、protected internal、protected、internal 或 private。</span><span class="sxs-lookup"><span data-stu-id="e20ba-123">Class members, including nested classes and structs, can be public, protected internal, protected, internal, or private.</span></span> <span data-ttu-id="e20ba-124">類別成員和結構成員 (包括巢狀類別和結構) 的存取層級預設為 private。</span><span class="sxs-lookup"><span data-stu-id="e20ba-124">The access level for class members and struct members, including nested classes and structs, is private by default.</span></span> <span data-ttu-id="e20ba-125">無法從包含類型外部存取私用巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="e20ba-125">Private nested types are not accessible from outside the containing type.</span></span>  
  
 <span data-ttu-id="e20ba-126">衍生類別的存取範圍不能大於其基底類型。</span><span class="sxs-lookup"><span data-stu-id="e20ba-126">Derived classes cannot have greater accessibility than their base types.</span></span> <span data-ttu-id="e20ba-127">換句話說，您不能有衍生自內部類別 `A` 的公用類別 `B`。</span><span class="sxs-lookup"><span data-stu-id="e20ba-127">In other words, you cannot have a public class `B` that derives from an internal class `A`.</span></span> <span data-ttu-id="e20ba-128">因為 `A` 的所有 protected 或 internal 成員都可以從衍生類別進行存取，所以如果允許這樣做，則會有將 `A` 設為 public 的效果。</span><span class="sxs-lookup"><span data-stu-id="e20ba-128">If this were allowed, it would have the effect of making `A` public, because all protected or internal members of `A` are accessible from the derived class.</span></span>  
  
 <span data-ttu-id="e20ba-129">您可以使用 InternalsVisibleToAttribute 來啟用特定其他組件存取您的內部類型。</span><span class="sxs-lookup"><span data-stu-id="e20ba-129">You can enable specific other assemblies to access your internal types by using the InternalsVisibleToAttribute.</span></span> <span data-ttu-id="e20ba-130">如需詳細資訊，請參閱 [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055) (Friend 組件)。</span><span class="sxs-lookup"><span data-stu-id="e20ba-130">For more information, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
## <a name="class-and-struct-member-accessibility"></a><span data-ttu-id="e20ba-131">類別和結構成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="e20ba-131">Class and Struct Member Accessibility</span></span>  
 <span data-ttu-id="e20ba-132">類別成員 (包括巢狀類別和結構) 可以使用五種存取類型的任一種進行宣告。</span><span class="sxs-lookup"><span data-stu-id="e20ba-132">Class members (including nested classes and structs) can be declared with any of the five types of access.</span></span> <span data-ttu-id="e20ba-133">因為結構不支援繼承，所以無法將結構成員宣告為 protected。</span><span class="sxs-lookup"><span data-stu-id="e20ba-133">Struct members cannot be declared as protected because structs do not support inheritance.</span></span>  
  
 <span data-ttu-id="e20ba-134">一般而言，成員存取範圍不會大於包含它之類型的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="e20ba-134">Normally, the accessibility of a member is not greater than the accessibility of the type that contains it.</span></span> <span data-ttu-id="e20ba-135">不過，如果成員實作介面方法，或覆寫公用基底類別中所定義的虛擬方法，則可以從組件外部存取內部類別的公用成員。</span><span class="sxs-lookup"><span data-stu-id="e20ba-135">However, a public member of an internal class might be accessible from outside the assembly if the member implements interface methods or overrides virtual methods that are defined in a public base class.</span></span>  
  
 <span data-ttu-id="e20ba-136">為欄位、屬性或事件之任何成員的類型必須至少與成員本身一樣可進行存取。</span><span class="sxs-lookup"><span data-stu-id="e20ba-136">The type of any member that is a field, property, or event must be at least as accessible as the member itself.</span></span> <span data-ttu-id="e20ba-137">同樣地，傳回型別以及本身為方法、索引子或委派之任何成員的參數類型都必須至少像該成員本身一樣可供存取。</span><span class="sxs-lookup"><span data-stu-id="e20ba-137">Similarly, the return type and the parameter types of any member that is a method, indexer, or delegate must be at least as accessible as the member itself.</span></span> <span data-ttu-id="e20ba-138">例如，除非 `C` 也是公用的，否則您無法有傳回 `C` 類別的公用方法 `M`。</span><span class="sxs-lookup"><span data-stu-id="e20ba-138">For example, you cannot have a public method `M` that returns a class `C` unless `C` is also public.</span></span> <span data-ttu-id="e20ba-139">同樣地，如果將 `A` 宣告為 private，則您不能有 `A` 類型的 protected 屬性。</span><span class="sxs-lookup"><span data-stu-id="e20ba-139">Likewise, you cannot have a protected property of type `A` if `A` is declared as private.</span></span>  
  
 <span data-ttu-id="e20ba-140">使用者定義的運算子一律必須宣告為 public。</span><span class="sxs-lookup"><span data-stu-id="e20ba-140">User-defined operators must always be declared as public.</span></span> <span data-ttu-id="e20ba-141">如需詳細資訊，請參閱 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)。</span><span class="sxs-lookup"><span data-stu-id="e20ba-141">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
 <span data-ttu-id="e20ba-142">完成項不能有存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="e20ba-142">Finalizers cannot have accessibility modifiers.</span></span>  
  
 <span data-ttu-id="e20ba-143">若要設定類別或結構成員的存取層級，請在成員宣告中新增適當的關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e20ba-143">To set the access level for a class or struct member, add the appropriate keyword to the member declaration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="e20ba-144">[!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e20ba-144">[!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e20ba-145">protected internal 存取範圍層級表示「protected 或 internal」，而非「protected 和 internal」。</span><span class="sxs-lookup"><span data-stu-id="e20ba-145">The protected internal accessibility level means protected OR internal, not protected AND internal.</span></span> <span data-ttu-id="e20ba-146">換句話說，可以從相同組件的任何類別 (包括衍生類別) 中存取 protected internal 成員。</span><span class="sxs-lookup"><span data-stu-id="e20ba-146">In other words, a protected internal member can be accessed from any class in the same assembly, including derived classes.</span></span> <span data-ttu-id="e20ba-147">若要僅限於相同組件中衍生類別的存取範圍，請將類別本身宣告為 internal，並將它的成員宣告為 protected。</span><span class="sxs-lookup"><span data-stu-id="e20ba-147">To limit accessibility to only derived classes in the same assembly, declare the class itself internal, and declare its members as protected.</span></span>  
  
## <a name="other-types"></a><span data-ttu-id="e20ba-148">其他類型</span><span class="sxs-lookup"><span data-stu-id="e20ba-148">Other Types</span></span>  
 <span data-ttu-id="e20ba-149">直接在命名空間內宣告的介面可以宣告為 public 或 internal；而且，就像類別和結構，介面預設為內部存取。</span><span class="sxs-lookup"><span data-stu-id="e20ba-149">Interfaces declared directly within a namespace can be declared as public or internal and, just like classes and structs, interfaces default to internal access.</span></span> <span data-ttu-id="e20ba-150">介面成員一律都是 public，因為介面的目的是要讓其他類型存取類別或結構。</span><span class="sxs-lookup"><span data-stu-id="e20ba-150">Interface members are always public because the purpose of an interface is to enable other types to access a class or struct.</span></span> <span data-ttu-id="e20ba-151">沒有存取修飾詞可以套用至介面成員。</span><span class="sxs-lookup"><span data-stu-id="e20ba-151">No access modifiers can be applied to interface members.</span></span>  
  
 <span data-ttu-id="e20ba-152">列舉成員一律為 public，因此無法套用任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="e20ba-152">Enumeration members are always public, and no access modifiers can be applied.</span></span>  
  
 <span data-ttu-id="e20ba-153">委派的行為類似類別和結構。</span><span class="sxs-lookup"><span data-stu-id="e20ba-153">Delegates behave like classes and structs.</span></span> <span data-ttu-id="e20ba-154">根據預設，它們在直接在命名空間內宣告時會具有 internal 存取，而且在巢狀時會具有 private 存取。</span><span class="sxs-lookup"><span data-stu-id="e20ba-154">By default, they have internal access when declared directly within a namespace, and private access when nested.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e20ba-155">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e20ba-155">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e20ba-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e20ba-156">See Also</span></span>  
 <span data-ttu-id="e20ba-157">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e20ba-157">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e20ba-158">[類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="e20ba-158">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="e20ba-159">[介面](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="e20ba-159">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 <span data-ttu-id="e20ba-160">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="e20ba-160">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="e20ba-161">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="e20ba-161">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="e20ba-162">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="e20ba-162">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="e20ba-163">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="e20ba-163">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 <span data-ttu-id="e20ba-164">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="e20ba-164">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="e20ba-165">[struct](../../../csharp/language-reference/keywords/struct.md) </span><span class="sxs-lookup"><span data-stu-id="e20ba-165">[struct](../../../csharp/language-reference/keywords/struct.md) </span></span>  
 [<span data-ttu-id="e20ba-166">interface</span><span class="sxs-lookup"><span data-stu-id="e20ba-166">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)

