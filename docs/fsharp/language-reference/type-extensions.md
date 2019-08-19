---
title: 類型擴充
description: 瞭解類型F#擴充功能如何讓您將新成員加入至先前定義的物件類型。
ms.date: 02/08/2019
ms.openlocfilehash: 502b8636052139b39c800447870c6076a8cd2643
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630196"
---
# <a name="type-extensions"></a><span data-ttu-id="33206-103">類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="33206-103">Type extensions</span></span>

<span data-ttu-id="33206-104">類型延伸模組 (也稱為_augmentations_) 是一系列的功能, 可讓您將新成員加入至先前定義的物件類型。</span><span class="sxs-lookup"><span data-stu-id="33206-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="33206-105">這三項功能包括:</span><span class="sxs-lookup"><span data-stu-id="33206-105">The three features are:</span></span>

* <span data-ttu-id="33206-106">內建類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="33206-106">Intrinsic type extensions</span></span>
* <span data-ttu-id="33206-107">選擇性類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="33206-107">Optional type extensions</span></span>
* <span data-ttu-id="33206-108">擴充方法</span><span class="sxs-lookup"><span data-stu-id="33206-108">Extension methods</span></span>

<span data-ttu-id="33206-109">每個都可以用於不同的案例, 而且有不同的取捨。</span><span class="sxs-lookup"><span data-stu-id="33206-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="33206-110">語法</span><span class="sxs-lookup"><span data-stu-id="33206-110">Syntax</span></span>

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

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="33206-111">內建類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="33206-111">Intrinsic type extensions</span></span>

<span data-ttu-id="33206-112">內建類型延伸模組是擴充使用者定義類型的類型延伸。</span><span class="sxs-lookup"><span data-stu-id="33206-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="33206-113">內建類型延伸模組必須在相同的檔案中 **, 以及**與所擴充之類型相同的命名空間或模組中定義。</span><span class="sxs-lookup"><span data-stu-id="33206-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="33206-114">任何其他定義都會導致它們成為[選擇性的類型延伸](type-extensions.md#optional-type-extensions)。</span><span class="sxs-lookup"><span data-stu-id="33206-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="33206-115">內建類型延伸有時是將功能與類型宣告分開的更清楚方式。</span><span class="sxs-lookup"><span data-stu-id="33206-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="33206-116">下列範例顯示如何定義內建類型延伸模組:</span><span class="sxs-lookup"><span data-stu-id="33206-116">The following example shows how to define an intrinsic type extension:</span></span>

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

<span data-ttu-id="33206-117">使用類型延伸可讓您分隔下列各項:</span><span class="sxs-lookup"><span data-stu-id="33206-117">Using a type extension allows you to separate each of the following:</span></span>

* <span data-ttu-id="33206-118">`Variant`類型的宣告</span><span class="sxs-lookup"><span data-stu-id="33206-118">The declaration of a `Variant` type</span></span>
* <span data-ttu-id="33206-119">根據其「圖形`Variant` 」列印類別的功能</span><span class="sxs-lookup"><span data-stu-id="33206-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
* <span data-ttu-id="33206-120">使用物件樣式`.`標記法來存取列印功能的方式</span><span class="sxs-lookup"><span data-stu-id="33206-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="33206-121">這是將所有專案定義為成員`Variant`的替代方法。</span><span class="sxs-lookup"><span data-stu-id="33206-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="33206-122">雖然它不是原本較好的方法, 但在某些情況下, 它可能是更清楚的功能表示。</span><span class="sxs-lookup"><span data-stu-id="33206-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="33206-123">內建類型延伸模組會編譯為它們所擴充之類型的成員, 而且會在反映的類型檢查時出現在類型上。</span><span class="sxs-lookup"><span data-stu-id="33206-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="33206-124">選擇性類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="33206-124">Optional type extensions</span></span>

<span data-ttu-id="33206-125">選擇性的類型延伸模組是一種延伸模組, 它會出現在要擴充之類型的原始模組、命名空間或元件外部。</span><span class="sxs-lookup"><span data-stu-id="33206-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="33206-126">選擇性類型延伸模組適用于擴充您尚未自行定義的類型。</span><span class="sxs-lookup"><span data-stu-id="33206-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="33206-127">例如：</span><span class="sxs-lookup"><span data-stu-id="33206-127">For example:</span></span>

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

<span data-ttu-id="33206-128">您現在可以存取`RepeatElements` , 就像它是的<xref:System.Collections.Generic.IEnumerable%601>成員一樣, 只要`Extensions`在您工作的範圍中開啟模組即可。</span><span class="sxs-lookup"><span data-stu-id="33206-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="33206-129">當反映進行檢查時, 選擇性擴充功能不會出現在擴充類型上。</span><span class="sxs-lookup"><span data-stu-id="33206-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="33206-130">選擇性擴充功能必須在模組中, 而且只有在包含擴充功能的模組已開啟或在範圍內時, 才會在範圍中。</span><span class="sxs-lookup"><span data-stu-id="33206-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="33206-131">選擇性的延伸模組成員會編譯成靜態成員, 其中會以隱含方式將物件實例當做第一個參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="33206-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="33206-132">不過, 它們的行為就像是實例成員或靜態成員 (根據它們的宣告方式而定)。</span><span class="sxs-lookup"><span data-stu-id="33206-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="33206-133">選擇性的擴充成員也不會對C#或 VB 取用者顯示。</span><span class="sxs-lookup"><span data-stu-id="33206-133">Optional extension members are also not visible to C# or VB consumers.</span></span> <span data-ttu-id="33206-134">它們只能在其他F#程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="33206-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="33206-135">內建和選擇性類型延伸的一般限制</span><span class="sxs-lookup"><span data-stu-id="33206-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="33206-136">在型別變數受條件約束的泛型型別上, 可以宣告型別延伸。</span><span class="sxs-lookup"><span data-stu-id="33206-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="33206-137">其需求是延伸模組宣告的條件約束符合宣告類型的條件約束。</span><span class="sxs-lookup"><span data-stu-id="33206-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="33206-138">不過, 即使在宣告的型別與型別延伸之間有相符的條件約束, 條件約束也可能會受到擴充成員的主體的推斷, 而這項要求在型別參數上會有不同的需求, 而不是宣告的型別。</span><span class="sxs-lookup"><span data-stu-id="33206-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="33206-139">例如：</span><span class="sxs-lookup"><span data-stu-id="33206-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="33206-140">沒有任何方法可以取得此程式碼以使用選擇性的類型延伸模組:</span><span class="sxs-lookup"><span data-stu-id="33206-140">There is no way to get this code to work with an optional type extension:</span></span>

* <span data-ttu-id="33206-141">也就是, `Sum`成員在 (`static member get_Zero`和`static member (+)`) 上`'T`具有與類型延伸所定義之不同的條件約束。</span><span class="sxs-lookup"><span data-stu-id="33206-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
* <span data-ttu-id="33206-142">`Sum`將類型延伸模組修改為具有與相同的條件約束, 將不再符合上`IEnumerable<'T>`定義的條件約束。</span><span class="sxs-lookup"><span data-stu-id="33206-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
* <span data-ttu-id="33206-143">將`member this.Sum`變更`member inline this.Sum`為會提供類型條件約束不相符的錯誤。</span><span class="sxs-lookup"><span data-stu-id="33206-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="33206-144">所需的是「以空格浮點數」的靜態方法, 可以如同擴充類型般呈現。</span><span class="sxs-lookup"><span data-stu-id="33206-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="33206-145">這是必要的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="33206-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="33206-146">擴充方法</span><span class="sxs-lookup"><span data-stu-id="33206-146">Extension methods</span></span>

<span data-ttu-id="33206-147">最後, 擴充方法 (有時稱為「C#樣式延伸成員」) 可以在中F#宣告為類別的靜態成員方法。</span><span class="sxs-lookup"><span data-stu-id="33206-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="33206-148">當您想要在將限制型別變數的泛型型別上定義延伸模組時, 擴充方法很有用。</span><span class="sxs-lookup"><span data-stu-id="33206-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="33206-149">例如：</span><span class="sxs-lookup"><span data-stu-id="33206-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="33206-150">使用時, 此`Sum`程式碼會使其看起來像是在上<xref:System.Collections.Generic.IEnumerable%601>定義, 只要`Extensions`已開啟或在範圍內即可。</span><span class="sxs-lookup"><span data-stu-id="33206-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

## <a name="other-remarks"></a><span data-ttu-id="33206-151">其他備註</span><span class="sxs-lookup"><span data-stu-id="33206-151">Other remarks</span></span>

<span data-ttu-id="33206-152">型別延伸也具有下列屬性:</span><span class="sxs-lookup"><span data-stu-id="33206-152">Type extensions also have the following attributes:</span></span>

* <span data-ttu-id="33206-153">可存取的任何類型都可以擴充。</span><span class="sxs-lookup"><span data-stu-id="33206-153">Any type that can be accessed can be extended.</span></span>
* <span data-ttu-id="33206-154">內建和選擇性類型延伸模組可以定義_任何_成員類型, 而不只是方法。</span><span class="sxs-lookup"><span data-stu-id="33206-154">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="33206-155">例如, 也可以提供延伸模組屬性。</span><span class="sxs-lookup"><span data-stu-id="33206-155">So extension properties are also possible, for example.</span></span>
* <span data-ttu-id="33206-156">[語法](type-extensions.md#syntax)`self-identifier`中的標記代表所叫用之類型的實例, 就像一般成員一樣。</span><span class="sxs-lookup"><span data-stu-id="33206-156">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
* <span data-ttu-id="33206-157">擴充成員可以是靜態或實例成員。</span><span class="sxs-lookup"><span data-stu-id="33206-157">Extended members can be static or instance members.</span></span>
* <span data-ttu-id="33206-158">類型擴充功能上的類型變數必須符合宣告類型的條件約束。</span><span class="sxs-lookup"><span data-stu-id="33206-158">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="33206-159">類型延伸模組也有下列限制:</span><span class="sxs-lookup"><span data-stu-id="33206-159">The following limitations also exist for type extensions:</span></span>

* <span data-ttu-id="33206-160">型別延伸不支援虛擬或抽象方法。</span><span class="sxs-lookup"><span data-stu-id="33206-160">Type extensions do not support virtual or abstract methods.</span></span>
* <span data-ttu-id="33206-161">型別延伸不支援將方法覆寫為 augmentations。</span><span class="sxs-lookup"><span data-stu-id="33206-161">Type extensions do not support override methods as augmentations.</span></span>
* <span data-ttu-id="33206-162">型別延伸不支援以[靜態方式解析的型別參數](./generics/statically-resolved-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="33206-162">Type extensions do not support [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>
* <span data-ttu-id="33206-163">選擇性類型擴充功能不支援以 augmentations 形式的函式。</span><span class="sxs-lookup"><span data-stu-id="33206-163">Optional Type extensions do not support constructors as augmentations.</span></span>
* <span data-ttu-id="33206-164">型別延伸不能定義在[型別縮寫](type-abbreviations.md)上。</span><span class="sxs-lookup"><span data-stu-id="33206-164">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
* <span data-ttu-id="33206-165">類型延伸模組對`byref<'T>`無效 (雖然可以宣告)。</span><span class="sxs-lookup"><span data-stu-id="33206-165">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
* <span data-ttu-id="33206-166">類型延伸模組對屬性而言是不正確 (雖然可以宣告)。</span><span class="sxs-lookup"><span data-stu-id="33206-166">Type extensions are not valid for attributes (though they can be declared).</span></span>
* <span data-ttu-id="33206-167">您可以定義多載相同名稱之其他方法的延伸模組, 但F#如果有不明確的呼叫, 則編譯器會提供非擴充方法的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="33206-167">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="33206-168">最後, 如果一個類型有多個內建類型延伸模組, 則所有成員都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="33206-168">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="33206-169">對於選擇性的類型擴充, 不同類型延伸模組中相同類型的成員可以具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="33206-169">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="33206-170">只有當用戶端程式代碼開啟兩個不同的範圍來定義相同的成員名稱時, 才會發生模糊錯誤。</span><span class="sxs-lookup"><span data-stu-id="33206-170">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="33206-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33206-171">See also</span></span>

- [<span data-ttu-id="33206-172">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="33206-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="33206-173">成員</span><span class="sxs-lookup"><span data-stu-id="33206-173">Members</span></span>](./members/index.md)
