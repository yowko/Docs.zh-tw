---
title: 類型擴充 (F#)
description: '了解如何 F # 型別延伸模組可讓您將新成員加入先前定義的物件類型。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 3399778799fbf0f8eee56e332135656150918a60
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="type-extensions"></a><span data-ttu-id="59a43-103">類型擴充</span><span class="sxs-lookup"><span data-stu-id="59a43-103">Type Extensions</span></span>

<span data-ttu-id="59a43-104">類型擴充功能可讓您將新成員加入至先前定義的物件類型。</span><span class="sxs-lookup"><span data-stu-id="59a43-104">Type extensions let you add new members to a previously defined object type.</span></span>

## <a name="syntax"></a><span data-ttu-id="59a43-105">語法</span><span class="sxs-lookup"><span data-stu-id="59a43-105">Syntax</span></span>

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a><span data-ttu-id="59a43-106">備註</span><span class="sxs-lookup"><span data-stu-id="59a43-106">Remarks</span></span>
<span data-ttu-id="59a43-107">有兩種形式的類型擴充功能具有稍有不同的語法和行為。</span><span class="sxs-lookup"><span data-stu-id="59a43-107">There are two forms of type extensions that have slightly different syntax and behavior.</span></span> <span data-ttu-id="59a43-108">*內建擴充*擴充功能會出現相同的命名空間或模組中，在相同原始程式檔，和相同的組件 （DLL 或可執行檔），為要擴充的類型。</span><span class="sxs-lookup"><span data-stu-id="59a43-108">An *intrinsic extension* is an extension that appears in the same namespace or module, in the same source file, and in the same assembly (DLL or executable file) as the type being extended.</span></span> <span data-ttu-id="59a43-109">*選擇性擴充功能*是出現原始的模組、 命名空間或要擴充之類型的組件外部的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="59a43-109">An *optional extension* is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span> <span data-ttu-id="59a43-110">類型會檢查透過反映，但選擇性擴充功能不這麼做時，內建的擴充功能會出現在型別。</span><span class="sxs-lookup"><span data-stu-id="59a43-110">Intrinsic extensions appear on the type when the type is examined by reflection, but optional extensions do not.</span></span> <span data-ttu-id="59a43-111">選擇性擴充功能必須在模組中，而且它們才會進入範圍時，其中包含延伸模組已開啟。</span><span class="sxs-lookup"><span data-stu-id="59a43-111">Optional extensions must be in modules, and they are only in scope when the module that contains the extension is open.</span></span>

<span data-ttu-id="59a43-112">在先前的語法， *typename*表示要擴充的型別。</span><span class="sxs-lookup"><span data-stu-id="59a43-112">In the previous syntax, *typename* represents the type that is being extended.</span></span> <span data-ttu-id="59a43-113">可以存取任何型別可以擴充，但型別名稱必須是實際的型別名稱，而不是類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="59a43-113">Any type that can be accessed can be extended, but the type name must be an actual type name, not a type abbreviation.</span></span> <span data-ttu-id="59a43-114">一種類型的擴充功能中，您可以定義多個成員。</span><span class="sxs-lookup"><span data-stu-id="59a43-114">You can define multiple members in one type extension.</span></span> <span data-ttu-id="59a43-115">*自我識別項*代表叫用的如同一般成員物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="59a43-115">The *self-identifier* represents the instance of the object being invoked, just as in ordinary members.</span></span>

<span data-ttu-id="59a43-116">`end`關鍵字是選擇性的輕量型語法。</span><span class="sxs-lookup"><span data-stu-id="59a43-116">The `end` keyword is optional in lightweight syntax.</span></span>

<span data-ttu-id="59a43-117">就像其他類別類型上的成員可以使用類型擴充功能中定義的成員。</span><span class="sxs-lookup"><span data-stu-id="59a43-117">Members defined in type extensions can be used just like other members on a class type.</span></span> <span data-ttu-id="59a43-118">類似其他成員，它們可以是靜態或執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="59a43-118">Like other members, they can be static or instance members.</span></span> <span data-ttu-id="59a43-119">這些方法也稱為的*擴充方法*; 屬性稱為*擴充功能屬性*，依此類推。</span><span class="sxs-lookup"><span data-stu-id="59a43-119">These methods are also known as *extension methods*; properties are known as *extension properties*, and so on.</span></span> <span data-ttu-id="59a43-120">選擇性擴充成員會編譯成靜態成員的物件執行個體被當做隱含的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="59a43-120">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="59a43-121">不過，它們會如同執行個體成員或靜態成員，根據宣告的方式。</span><span class="sxs-lookup"><span data-stu-id="59a43-121">However, they act as if they were instance members or static members according to how they are declared.</span></span> <span data-ttu-id="59a43-122">隱含擴充成員隨附做為型別的成員，而且可以無限制使用。</span><span class="sxs-lookup"><span data-stu-id="59a43-122">Implicit extension members are included as members of the type and can be used without restriction.</span></span>

<span data-ttu-id="59a43-123">擴充方法不能為虛擬或抽象方法。</span><span class="sxs-lookup"><span data-stu-id="59a43-123">Extension methods cannot be virtual or abstract methods.</span></span> <span data-ttu-id="59a43-124">它們可以多載其他方法的名稱相同，但該編譯器會產生模稜兩可的呼叫在非擴充方法的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="59a43-124">They can overload other methods of the same name, but the compiler gives preference to non-extension methods in the case of an ambiguous call.</span></span>

<span data-ttu-id="59a43-125">如果一種類型的多個內建型別延伸存在，所有成員必須都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="59a43-125">If multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="59a43-126">針對選擇性型別擴充功能，為相同類型的不同類型擴充功能中的成員可以有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="59a43-126">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="59a43-127">只有當用戶端程式碼會開啟兩個不同的領域，定義了相同的成員名稱，則會發生模稜兩可的錯誤。</span><span class="sxs-lookup"><span data-stu-id="59a43-127">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

<span data-ttu-id="59a43-128">在下列範例中，模組中的類型具有內建型別延伸。</span><span class="sxs-lookup"><span data-stu-id="59a43-128">In the following example, a type in a module has an intrinsic type extension.</span></span> <span data-ttu-id="59a43-129">外部模組的用戶端程式碼，類型擴充功能會顯示為一般成員中所有各方面的類型。</span><span class="sxs-lookup"><span data-stu-id="59a43-129">To client code outside the module, the type extension appears as a regular member of the type in all respects.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

<span data-ttu-id="59a43-130">您可以使用內建類型擴充功能來分隔成區段類型的定義。</span><span class="sxs-lookup"><span data-stu-id="59a43-130">You can use intrinsic type extensions to separate the definition of a type into sections.</span></span> <span data-ttu-id="59a43-131">這可以是用於管理大型的類型定義，例如，將編譯器產生的程式碼和撰寫程式碼分開，或將群組在一起由不同的人所建立，或不同功能相關聯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="59a43-131">This can be useful in managing large type definitions, for example, to keep compiler-generated code and authored code separate or to group together code created by different people or associated with different functionality.</span></span>

<span data-ttu-id="59a43-132">在下列範例中，選擇性型別延伸能擴充`System.Int32`擴充方法的型別`FromString`呼叫靜態成員`Parse`。</span><span class="sxs-lookup"><span data-stu-id="59a43-132">In the following example, an optional type extension extends the `System.Int32` type with an extension method `FromString` that calls the static member `Parse`.</span></span> <span data-ttu-id="59a43-133">`testFromString`方法將示範就像任何執行個體成員一樣，會呼叫新的成員。</span><span class="sxs-lookup"><span data-stu-id="59a43-133">The `testFromString` method demonstrates that the new member is called just like any instance member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

<span data-ttu-id="59a43-134">新的執行個體成員會出現的任何其他方法一樣`Int32`IntelliSense，但只包含延伸模組的模組開啟或其他在範圍中時的型別。</span><span class="sxs-lookup"><span data-stu-id="59a43-134">The new instance member will appear like any other method of the `Int32` type in IntelliSense, but only when the module that contains the extension is open or otherwise in scope.</span></span>

## <a name="generic-extension-methods"></a><span data-ttu-id="59a43-135">泛型擴充方法</span><span class="sxs-lookup"><span data-stu-id="59a43-135">Generic Extension Methods</span></span>
<span data-ttu-id="59a43-136">F # 3.1 之前, 的 F # 編譯器並不支援使用 C#-樣式的泛型型別變數、 陣列類型、 元組型別或 F # 函式類型做為 「 這個 」 參數的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="59a43-136">Before F# 3.1, the F# compiler didn't support the use of C#-style extension methods with a generic type variable, array type, tuple type, or an F# function type as the "this" parameter.</span></span> <span data-ttu-id="59a43-137">F # 3.1 支援使用這些延伸模組成員。</span><span class="sxs-lookup"><span data-stu-id="59a43-137">F# 3.1 supports the use of these extension members.</span></span>

<span data-ttu-id="59a43-138">比方說，F # 3.1 程式碼中，您可以使用擴充方法具有簽章，類似於 C# 中的下列語法：</span><span class="sxs-lookup"><span data-stu-id="59a43-138">For example, in F# 3.1 code, you can use extension methods with signatures that resemble the following syntax in C#:</span></span>

```csharp
static member Method<T>(this T input, T other)
```

<span data-ttu-id="59a43-139">泛型型別參數受到限制時，這種方式就特別有用。</span><span class="sxs-lookup"><span data-stu-id="59a43-139">This approach is particularly useful when the generic type parameter is constrained.</span></span> <span data-ttu-id="59a43-140">此外，您現在可以宣告如下 F # 程式碼中的擴充成員，並定義其他且語意豐富的擴充方法的集合。</span><span class="sxs-lookup"><span data-stu-id="59a43-140">Further, you can now declare extension members like this in F# code and define an additional, semantically rich set of extension methods.</span></span> <span data-ttu-id="59a43-141">在 F # 中，您通常定義擴充成員如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="59a43-141">In F#, you usually define extension members as the following example shows:</span></span>

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

<span data-ttu-id="59a43-142">不過，若是泛型類型，型別變數可能不限制。</span><span class="sxs-lookup"><span data-stu-id="59a43-142">However, for a generic type, the type variable may not be constrained.</span></span> <span data-ttu-id="59a43-143">您現在可以宣告 C#-F # 若要解決這項限制中的樣式擴充成員。</span><span class="sxs-lookup"><span data-stu-id="59a43-143">You can now declare a C#-style extension member in F# to work around this limitation.</span></span> <span data-ttu-id="59a43-144">當您合併這類宣告與 F # 的內嵌功能時，您可以擴充成員呈現泛型演算法。</span><span class="sxs-lookup"><span data-stu-id="59a43-144">When you combine this kind of declaration with the inline feature of F#, you can present generic algorithms as extension members.</span></span>

<span data-ttu-id="59a43-145">請考慮下列宣告：</span><span class="sxs-lookup"><span data-stu-id="59a43-145">Consider the following declaration:</span></span>

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="59a43-146">藉由使用此宣告，您可以撰寫類似下面的範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="59a43-146">By using this declaration, you can write code that resembles the following sample.</span></span>

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

<span data-ttu-id="59a43-147">這個程式碼，在相同的泛型算術程式碼會套用到兩種類型的清單沒有多載中，定義單一擴充功能的成員。</span><span class="sxs-lookup"><span data-stu-id="59a43-147">In this code, the same generic arithmetic code is applied to lists of two types without overloading, by defining a single extension member.</span></span>


## <a name="see-also"></a><span data-ttu-id="59a43-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59a43-148">See Also</span></span>
[<span data-ttu-id="59a43-149">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="59a43-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="59a43-150">成員</span><span class="sxs-lookup"><span data-stu-id="59a43-150">Members</span></span>](members/index.md)
