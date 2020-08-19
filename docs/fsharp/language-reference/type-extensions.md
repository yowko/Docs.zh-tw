---
title: 類型擴充
description: '瞭解 F # 類型延伸模組如何讓您將新成員加入至先前定義的物件類型。'
ms.date: 02/05/2020
ms.openlocfilehash: 8fdb2d5e527643b23d24a6118e8cef6b11f1a546
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559124"
---
# <a name="type-extensions"></a><span data-ttu-id="966e8-103">類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="966e8-103">Type extensions</span></span>

<span data-ttu-id="966e8-104">類型延伸 (也稱為 _增強指定_) 是一系列的功能，可讓您將新成員加入至先前定義的物件類型。</span><span class="sxs-lookup"><span data-stu-id="966e8-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="966e8-105">這三項功能包括：</span><span class="sxs-lookup"><span data-stu-id="966e8-105">The three features are:</span></span>

- <span data-ttu-id="966e8-106">內建類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="966e8-106">Intrinsic type extensions</span></span>
- <span data-ttu-id="966e8-107">選擇性類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="966e8-107">Optional type extensions</span></span>
- <span data-ttu-id="966e8-108">擴充方法</span><span class="sxs-lookup"><span data-stu-id="966e8-108">Extension methods</span></span>

<span data-ttu-id="966e8-109">每個都可以在不同的案例中使用，而且有不同的取捨。</span><span class="sxs-lookup"><span data-stu-id="966e8-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="966e8-110">語法</span><span class="sxs-lookup"><span data-stu-id="966e8-110">Syntax</span></span>

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
    [<Extension>]
    static member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="966e8-111">內建類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="966e8-111">Intrinsic type extensions</span></span>

<span data-ttu-id="966e8-112">內建類型延伸模組是延伸使用者定義型別的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="966e8-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="966e8-113">內建類型延伸模組必須定義在相同的檔案中 **，以及** 在其所擴充之類型的相同命名空間或模組中。</span><span class="sxs-lookup"><span data-stu-id="966e8-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="966e8-114">任何其他定義都會導致它們成為 [選用的類型延伸](type-extensions.md#optional-type-extensions)模組。</span><span class="sxs-lookup"><span data-stu-id="966e8-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="966e8-115">內建類型延伸模組有時可讓您以更清楚的方式來分隔類型宣告中的功能。</span><span class="sxs-lookup"><span data-stu-id="966e8-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="966e8-116">下列範例示範如何定義內建類型延伸：</span><span class="sxs-lookup"><span data-stu-id="966e8-116">The following example shows how to define an intrinsic type extension:</span></span>

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

<span data-ttu-id="966e8-117">使用類型擴充功能可讓您分隔下列各項：</span><span class="sxs-lookup"><span data-stu-id="966e8-117">Using a type extension allows you to separate each of the following:</span></span>

- <span data-ttu-id="966e8-118">型別的宣告 `Variant`</span><span class="sxs-lookup"><span data-stu-id="966e8-118">The declaration of a `Variant` type</span></span>
- <span data-ttu-id="966e8-119">根據其「圖形」來列印類別的功能 `Variant`</span><span class="sxs-lookup"><span data-stu-id="966e8-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
- <span data-ttu-id="966e8-120">使用物件樣式表示法存取列印功能的方式 `.`</span><span class="sxs-lookup"><span data-stu-id="966e8-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="966e8-121">這是將所有專案定義為成員的替代方案 `Variant` 。</span><span class="sxs-lookup"><span data-stu-id="966e8-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="966e8-122">雖然它並非原本就更好的方法，但是在某些情況下，它可以是更清楚的功能表示。</span><span class="sxs-lookup"><span data-stu-id="966e8-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="966e8-123">內建類型延伸模組會編譯為它們所擴充之類型的成員，並且在反映檢查型別時出現在類型上。</span><span class="sxs-lookup"><span data-stu-id="966e8-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="966e8-124">選擇性類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="966e8-124">Optional type extensions</span></span>

<span data-ttu-id="966e8-125">選擇性類型延伸模組是在要擴充之類型的原始模組、命名空間或元件之外出現的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="966e8-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="966e8-126">選擇性類型延伸模組適用于擴充您自己未定義的類型。</span><span class="sxs-lookup"><span data-stu-id="966e8-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="966e8-127">例如：</span><span class="sxs-lookup"><span data-stu-id="966e8-127">For example:</span></span>

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

<span data-ttu-id="966e8-128">您現在可以存取 `RepeatElements` 相同的成員，只要 <xref:System.Collections.Generic.IEnumerable%601> `Extensions` 模組是在您所使用的範圍中開啟即可。</span><span class="sxs-lookup"><span data-stu-id="966e8-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="966e8-129">由反映檢查時，選擇性的延伸模組不會出現在擴充類型上。</span><span class="sxs-lookup"><span data-stu-id="966e8-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="966e8-130">選用的延伸模組必須在模組中，而且只有在包含擴充功能的模組是開啟或在範圍內時，才會在範圍內。</span><span class="sxs-lookup"><span data-stu-id="966e8-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="966e8-131">選擇性的擴充成員會編譯成靜態成員，而靜態成員會以隱含方式將物件實例傳遞為第一個參數。</span><span class="sxs-lookup"><span data-stu-id="966e8-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="966e8-132">不過，它們的作用就像是實例成員或靜態成員（根據其宣告方式）。</span><span class="sxs-lookup"><span data-stu-id="966e8-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="966e8-133">C # 或 Visual Basic 取用者也看不到選用的擴充成員。</span><span class="sxs-lookup"><span data-stu-id="966e8-133">Optional extension members are also not visible to C# or Visual Basic consumers.</span></span> <span data-ttu-id="966e8-134">它們只能在其他 F # 程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="966e8-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="966e8-135">內建和選擇性類型延伸的一般限制</span><span class="sxs-lookup"><span data-stu-id="966e8-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="966e8-136">您可以在類型變數受到條件約束的泛型型別上宣告類型延伸。</span><span class="sxs-lookup"><span data-stu-id="966e8-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="966e8-137">需求是延伸宣告的條件約束符合宣告型別的條件約束。</span><span class="sxs-lookup"><span data-stu-id="966e8-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="966e8-138">但是，即使在宣告的型別和型別延伸之間符合條件約束，也有可能是因為在類型參數上強加不同需求的擴充成員主體所推斷的條件約束，而不是宣告的型別。</span><span class="sxs-lookup"><span data-stu-id="966e8-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="966e8-139">例如：</span><span class="sxs-lookup"><span data-stu-id="966e8-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="966e8-140">沒有任何方法可讓此程式碼使用選擇性的類型延伸模組：</span><span class="sxs-lookup"><span data-stu-id="966e8-140">There is no way to get this code to work with an optional type extension:</span></span>

- <span data-ttu-id="966e8-141">同樣地， `Sum` 成員在 (上具有不同的條件約束 `'T` `static member get_Zero` ，且) 與類型延伸模組所定義的不同 `static member (+)` 。</span><span class="sxs-lookup"><span data-stu-id="966e8-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
- <span data-ttu-id="966e8-142">將類型延伸修改為具有相同的條件約束， `Sum` 將不再符合中的定義條件約束 `IEnumerable<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="966e8-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
- <span data-ttu-id="966e8-143">`member this.Sum`將變更為 `member inline this.Sum` 會提供類型條件約束不相符的錯誤。</span><span class="sxs-lookup"><span data-stu-id="966e8-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="966e8-144">您需要的是「float in space」的靜態方法，而且可以像是延伸型別一樣呈現。</span><span class="sxs-lookup"><span data-stu-id="966e8-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="966e8-145">這就是需要擴充方法的地方。</span><span class="sxs-lookup"><span data-stu-id="966e8-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="966e8-146">擴充方法</span><span class="sxs-lookup"><span data-stu-id="966e8-146">Extension methods</span></span>

<span data-ttu-id="966e8-147">最後，擴充方法 (有時稱為「c # 樣式延伸成員」 ) 可以在 F # 中宣告為類別上的靜態成員方法。</span><span class="sxs-lookup"><span data-stu-id="966e8-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="966e8-148">當您想要在會限制型別變數的泛型型別上定義延伸時，擴充方法會很有用。</span><span class="sxs-lookup"><span data-stu-id="966e8-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="966e8-149">例如：</span><span class="sxs-lookup"><span data-stu-id="966e8-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Collections.Generic
open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="966e8-150">使用時，此程式碼會使其顯示為 `Sum` 在上定義的 <xref:System.Collections.Generic.IEnumerable%601> ，只要已 `Extensions` 開啟或在範圍內即可。</span><span class="sxs-lookup"><span data-stu-id="966e8-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

<span data-ttu-id="966e8-151">為了讓擴充功能可供 VB.NET 程式碼使用， `ExtensionAttribute` 元件層級需要額外的程式碼：</span><span class="sxs-lookup"><span data-stu-id="966e8-151">For the extension to be available to VB.NET code, an extra `ExtensionAttribute` is required at the assembly level:</span></span>

```fsharp
module AssemblyInfo
open System.Runtime.CompilerServices
[<assembly:Extension>]
do ()
```

## <a name="other-remarks"></a><span data-ttu-id="966e8-152">其他備註</span><span class="sxs-lookup"><span data-stu-id="966e8-152">Other remarks</span></span>

<span data-ttu-id="966e8-153">類型延伸也有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="966e8-153">Type extensions also have the following attributes:</span></span>

- <span data-ttu-id="966e8-154">您可以擴充任何可以存取的類型。</span><span class="sxs-lookup"><span data-stu-id="966e8-154">Any type that can be accessed can be extended.</span></span>
- <span data-ttu-id="966e8-155">內建和選擇性類型延伸模組可以定義 _任何_ 成員類型，而不只是方法。</span><span class="sxs-lookup"><span data-stu-id="966e8-155">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="966e8-156">例如，擴充屬性也是可行的。</span><span class="sxs-lookup"><span data-stu-id="966e8-156">So extension properties are also possible, for example.</span></span>
- <span data-ttu-id="966e8-157">`self-identifier`[語法](type-extensions.md#syntax)中的標記代表所叫用之型別的實例，就像一般成員一樣。</span><span class="sxs-lookup"><span data-stu-id="966e8-157">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
- <span data-ttu-id="966e8-158">擴充成員可以是靜態或實例成員。</span><span class="sxs-lookup"><span data-stu-id="966e8-158">Extended members can be static or instance members.</span></span>
- <span data-ttu-id="966e8-159">類型延伸的型別變數必須符合宣告型別的條件約束。</span><span class="sxs-lookup"><span data-stu-id="966e8-159">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="966e8-160">類型延伸也有下列限制：</span><span class="sxs-lookup"><span data-stu-id="966e8-160">The following limitations also exist for type extensions:</span></span>

- <span data-ttu-id="966e8-161">類型延伸模組不支援虛擬或抽象方法。</span><span class="sxs-lookup"><span data-stu-id="966e8-161">Type extensions do not support virtual or abstract methods.</span></span>
- <span data-ttu-id="966e8-162">類型延伸模組不支援以增強指定覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="966e8-162">Type extensions do not support override methods as augmentations.</span></span>
- <span data-ttu-id="966e8-163">類型延伸模組不支援 [靜態解析的型別參數](./generics/statically-resolved-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="966e8-163">Type extensions do not support [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>
- <span data-ttu-id="966e8-164">選擇性類型延伸模組不支援做為增強指定的函式。</span><span class="sxs-lookup"><span data-stu-id="966e8-164">Optional Type extensions do not support constructors as augmentations.</span></span>
- <span data-ttu-id="966e8-165">類型縮寫不能定義為類型 [縮寫](type-abbreviations.md)。</span><span class="sxs-lookup"><span data-stu-id="966e8-165">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
- <span data-ttu-id="966e8-166">類型延伸模組對 (而言是不正確， `byref<'T>` 不過它們可以) 宣告。</span><span class="sxs-lookup"><span data-stu-id="966e8-166">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
- <span data-ttu-id="966e8-167">類型延伸模組對屬性而言無效 (但可以) 宣告。</span><span class="sxs-lookup"><span data-stu-id="966e8-167">Type extensions are not valid for attributes (though they can be declared).</span></span>
- <span data-ttu-id="966e8-168">您可以定義多載相同名稱之其他方法的擴充功能，但 F # 編譯器會在有不明確的呼叫時，將喜好設定提供給非擴充方法。</span><span class="sxs-lookup"><span data-stu-id="966e8-168">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="966e8-169">最後，如果有多個類型的內建類型延伸，則所有成員都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="966e8-169">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="966e8-170">對於選擇性的類型延伸，相同類型之不同類型延伸中的成員可以有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="966e8-170">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="966e8-171">只有當用戶端程式代碼開啟兩個定義相同成員名稱的不同範圍時，才會發生不明確的錯誤。</span><span class="sxs-lookup"><span data-stu-id="966e8-171">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="966e8-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="966e8-172">See also</span></span>

- [<span data-ttu-id="966e8-173">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="966e8-173">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="966e8-174">成員</span><span class="sxs-lookup"><span data-stu-id="966e8-174">Members</span></span>](./members/index.md)
