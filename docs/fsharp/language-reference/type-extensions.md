---
title: 類型擴充
description: 了解如何F#類型擴充功能可讓您將新成員加入先前定義的物件類型。
ms.date: 07/20/2018
ms.openlocfilehash: 9c0c6247eb5b94e9f42377859026ba7b466eb2e4
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614046"
---
# <a name="type-extensions"></a><span data-ttu-id="9927c-103">類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="9927c-103">Type extensions</span></span>

<span data-ttu-id="9927c-104">輸入擴充功能 (也稱為_增強指定_) 是一系列的功能，可讓您將新成員新增至先前定義的物件類型。</span><span class="sxs-lookup"><span data-stu-id="9927c-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="9927c-105">三個功能如下：</span><span class="sxs-lookup"><span data-stu-id="9927c-105">The three features are:</span></span>

* <span data-ttu-id="9927c-106">內建類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="9927c-106">Intrinsic type extensions</span></span>
* <span data-ttu-id="9927c-107">選擇性類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="9927c-107">Optional type extensions</span></span>
* <span data-ttu-id="9927c-108">擴充方法</span><span class="sxs-lookup"><span data-stu-id="9927c-108">Extension methods</span></span>

<span data-ttu-id="9927c-109">每個可用於不同的案例，並有不同的優缺點。</span><span class="sxs-lookup"><span data-stu-id="9927c-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="9927c-110">語法</span><span class="sxs-lookup"><span data-stu-id="9927c-110">Syntax</span></span>

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="9927c-111">內建類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="9927c-111">Intrinsic type extensions</span></span>

<span data-ttu-id="9927c-112">內建類型擴充功能是擴充的使用者定義型別類型擴充功能。</span><span class="sxs-lookup"><span data-stu-id="9927c-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="9927c-113">內建類型擴充功能必須定義在相同的檔案**和**在相同的命名空間或模組做為其延伸的類型。</span><span class="sxs-lookup"><span data-stu-id="9927c-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="9927c-114">任何其他定義將會導致它們正在[選擇性類型擴充](type-extensions.md#optional-type-extensions)。</span><span class="sxs-lookup"><span data-stu-id="9927c-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="9927c-115">內建類型擴充有時候是簡潔的方式，將功能分開的型別宣告。</span><span class="sxs-lookup"><span data-stu-id="9927c-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="9927c-116">下列範例示範如何定義內建類型擴充功能：</span><span class="sxs-lookup"><span data-stu-id="9927c-116">The following example shows how to define an intrinsic type extension:</span></span>

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

<span data-ttu-id="9927c-117">使用類型擴充功能，可讓您將下列各項：</span><span class="sxs-lookup"><span data-stu-id="9927c-117">Using a type extension allows you to separate each of the following:</span></span>

* <span data-ttu-id="9927c-118">Deklarace`Variant`類型</span><span class="sxs-lookup"><span data-stu-id="9927c-118">The declaration of a `Variant` type</span></span>
* <span data-ttu-id="9927c-119">若要列印的功能`Variant`根據其 「 圖形 」 類別</span><span class="sxs-lookup"><span data-stu-id="9927c-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
* <span data-ttu-id="9927c-120">若要存取物件樣式的列印功能的方式`.`-標記法</span><span class="sxs-lookup"><span data-stu-id="9927c-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="9927c-121">這是定義為成員的所有項目上的替代`Variant`。</span><span class="sxs-lookup"><span data-stu-id="9927c-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="9927c-122">雖然不是原本就更好的方法，它可能會更簡潔的功能，在某些情況下表示。</span><span class="sxs-lookup"><span data-stu-id="9927c-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="9927c-123">內建類型擴充會編譯為型別的擴充，而反映檢查類型時，會出現在類型上的成員。</span><span class="sxs-lookup"><span data-stu-id="9927c-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="9927c-124">選擇性類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="9927c-124">Optional type extensions</span></span>

<span data-ttu-id="9927c-125">選擇性類型擴充會出現原始模組、 命名空間或要擴充型別的組件外部的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="9927c-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="9927c-126">選擇性類型擴充可用於擴充您還沒有定義您自己的類型。</span><span class="sxs-lookup"><span data-stu-id="9927c-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="9927c-127">例如: </span><span class="sxs-lookup"><span data-stu-id="9927c-127">For example:</span></span>

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

<span data-ttu-id="9927c-128">您現在可以存取`RepeatElements`好像是隸屬<xref:System.Collections.Generic.IEnumerable%601>只要`Extensions`模組會開啟您在範圍中。</span><span class="sxs-lookup"><span data-stu-id="9927c-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="9927c-129">擴充的型別，當反映檢查上沒有出現選擇性擴充功能。</span><span class="sxs-lookup"><span data-stu-id="9927c-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="9927c-130">選擇性擴充功能必須在模組中，而且時，它們只能在範圍中包含的延伸模組的模組已開啟，或不在範圍內。</span><span class="sxs-lookup"><span data-stu-id="9927c-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="9927c-131">選擇性擴充成員會編譯成靜態成員的物件執行個體隱含傳遞做為第一個參數。</span><span class="sxs-lookup"><span data-stu-id="9927c-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="9927c-132">不過，它們就像它們是執行個體成員或靜態成員，根據這些宣告的方式。</span><span class="sxs-lookup"><span data-stu-id="9927c-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="9927c-133">內建函式和選擇性類型擴充功能的一般限制</span><span class="sxs-lookup"><span data-stu-id="9927c-133">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="9927c-134">很可能限於型別變數是泛型型別上宣告的型別延伸模組。</span><span class="sxs-lookup"><span data-stu-id="9927c-134">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="9927c-135">這個需求是延伸模組宣告的條件約束符合宣告的型別條件約束。</span><span class="sxs-lookup"><span data-stu-id="9927c-135">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="9927c-136">不過，即使宣告的型別和型別延伸模組之間比對條件約束，就可以加諸的宣告型別與型別參數上的不同需求擴充成員的主體所推斷的條件約束。</span><span class="sxs-lookup"><span data-stu-id="9927c-136">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="9927c-137">例如: </span><span class="sxs-lookup"><span data-stu-id="9927c-137">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="9927c-138">沒有任何方法可以取得此程式碼以使用選擇性類型擴充功能：</span><span class="sxs-lookup"><span data-stu-id="9927c-138">There is no way to get this code to work with an optional type extension:</span></span>

* <span data-ttu-id="9927c-139">現況`Sum`成員有不同的條件約束`'T`(`static member get_Zero`和`static member (+)`) 比類型擴充功能的定義。</span><span class="sxs-lookup"><span data-stu-id="9927c-139">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
* <span data-ttu-id="9927c-140">修改類型擴充功能，能夠以相同的條件約束`Sum`就不再符合定義的條件約束上`IEnumerable<'T>`。</span><span class="sxs-lookup"><span data-stu-id="9927c-140">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
* <span data-ttu-id="9927c-141">進行變更的成員，才能`member inline Sum`將會不相符類型條件約束發生錯誤</span><span class="sxs-lookup"><span data-stu-id="9927c-141">Making changing the member to `member inline Sum` will give an error that type constraints are mismatched</span></span>

<span data-ttu-id="9927c-142">預期是 「 浮動在空間 」，可以呈現，彷彿它們所擴充類型的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="9927c-142">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="9927c-143">這是其中的擴充方法會變得必要。</span><span class="sxs-lookup"><span data-stu-id="9927c-143">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="9927c-144">擴充方法</span><span class="sxs-lookup"><span data-stu-id="9927c-144">Extension methods</span></span>

<span data-ttu-id="9927c-145">最後，擴充方法 (有時稱為 「C#樣式擴充成員 」) 可以宣告在F#如同類別的靜態成員方法。</span><span class="sxs-lookup"><span data-stu-id="9927c-145">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="9927c-146">擴充方法可用於當您想要將會限制型別變數的泛型型別上定義擴充功能。</span><span class="sxs-lookup"><span data-stu-id="9927c-146">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="9927c-147">例如: </span><span class="sxs-lookup"><span data-stu-id="9927c-147">For example:</span></span>

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="9927c-148">使用時，此程式碼會讓它看起來好像`Sum`上定義<xref:System.Collections.Generic.IEnumerable%601>，只要`Extensions`已開啟，或在範圍內。</span><span class="sxs-lookup"><span data-stu-id="9927c-148">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

## <a name="other-remarks"></a><span data-ttu-id="9927c-149">其他備註</span><span class="sxs-lookup"><span data-stu-id="9927c-149">Other remarks</span></span>

<span data-ttu-id="9927c-150">類型延伸模組也會有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="9927c-150">Type extensions also have the following attributes:</span></span>

* <span data-ttu-id="9927c-151">任何可以存取的型別可加以擴充。</span><span class="sxs-lookup"><span data-stu-id="9927c-151">Any type that can be accessed can be extended.</span></span>
* <span data-ttu-id="9927c-152">內建函式和選擇性類型擴充功能可以定義_任何_成員型別，不只是方法。</span><span class="sxs-lookup"><span data-stu-id="9927c-152">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="9927c-153">讓擴充功能屬性也是可行的例如。</span><span class="sxs-lookup"><span data-stu-id="9927c-153">So extension properties are also possible, for example.</span></span>
* <span data-ttu-id="9927c-154">`self-identifier`權杖[語法](type-extensions.md#syntax)表示叫用，就像一般成員類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9927c-154">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
* <span data-ttu-id="9927c-155">擴充的成員可以是靜態或執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="9927c-155">Extended members can be static or instance members.</span></span>
* <span data-ttu-id="9927c-156">類型擴充功能上的型別變數必須符合宣告的型別條件的約束。</span><span class="sxs-lookup"><span data-stu-id="9927c-156">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="9927c-157">型別擴充功能也有下列限制：</span><span class="sxs-lookup"><span data-stu-id="9927c-157">The following limitations also exist for type extensions:</span></span>

* <span data-ttu-id="9927c-158">類型擴充功能不支援虛擬或抽象方法。</span><span class="sxs-lookup"><span data-stu-id="9927c-158">Type extensions do not support virtual or abstract methods.</span></span>
* <span data-ttu-id="9927c-159">類型擴充功能的增強指定為不支援覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="9927c-159">Type extensions do not support override methods as augmentations.</span></span>
* <span data-ttu-id="9927c-160">不支援類型擴充功能[以靜態方式解析的類型參數](generics/statically-resolved-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9927c-160">Type extensions do not support [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>
* <span data-ttu-id="9927c-161">選擇性類型擴充功能的增強指定為不支援的建構函式。</span><span class="sxs-lookup"><span data-stu-id="9927c-161">Optional Type extensions do not support constructors as augmentations.</span></span>
* <span data-ttu-id="9927c-162">類型擴充功能不能定義於[類型縮寫](type-abbreviations.md)。</span><span class="sxs-lookup"><span data-stu-id="9927c-162">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
* <span data-ttu-id="9927c-163">類型擴充功能不一定適用於`byref<'T>`（不過它們可以宣告）。</span><span class="sxs-lookup"><span data-stu-id="9927c-163">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
* <span data-ttu-id="9927c-164">類型擴充功能不適用於屬性 （不過它們可以宣告）。</span><span class="sxs-lookup"><span data-stu-id="9927c-164">Type extensions are not valid for attributes (though they can be declared).</span></span>
* <span data-ttu-id="9927c-165">您可以定義多載相同名稱的其他方法的擴充功能，但F#如果有模稜兩可的呼叫，編譯器會產生非擴充方法的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="9927c-165">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="9927c-166">最後，如果多個內建類型擴充功能有一種類型，所有成員必須都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9927c-166">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="9927c-167">對於選擇性類型擴充成相同類型的不同類型擴充中的成員可以有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="9927c-167">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="9927c-168">只有當用戶端程式碼會開啟兩個不同的領域，定義了相同成員名稱，則會發生模稜兩可錯誤。</span><span class="sxs-lookup"><span data-stu-id="9927c-168">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="9927c-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9927c-169">See also</span></span>

- [<span data-ttu-id="9927c-170">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="9927c-170">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9927c-171">成員</span><span class="sxs-lookup"><span data-stu-id="9927c-171">Members</span></span>](members/index.md)