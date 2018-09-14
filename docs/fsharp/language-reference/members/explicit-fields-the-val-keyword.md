---
title: 明確欄位：val 關鍵字 (F#)
description: "深入了解 F # 'val' 關鍵字，用來宣告類別或結構類型中儲存的值，而不會初始化類型的位置。"
ms.date: 05/16/2016
ms.openlocfilehash: 9cd06f7e90192be79490dd0ff67f118cce4339c3
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569995"
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="a23b9-103">明確欄位：val 關鍵字</span><span class="sxs-lookup"><span data-stu-id="a23b9-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="a23b9-104">`val` 關鍵字用來宣告位置以儲存類別中或結構類型中的值，但不初始化。</span><span class="sxs-lookup"><span data-stu-id="a23b9-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="a23b9-105">這種方式宣告的儲存體位置稱為*明確欄位*。</span><span class="sxs-lookup"><span data-stu-id="a23b9-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="a23b9-106">`val` 關鍵字的另一種用法是搭配 `member` 關鍵字來宣告自動實作的屬性。</span><span class="sxs-lookup"><span data-stu-id="a23b9-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="a23b9-107">如需有關自動實作屬性的詳細資訊，請參閱[屬性](properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a23b9-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="a23b9-108">語法</span><span class="sxs-lookup"><span data-stu-id="a23b9-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="a23b9-109">備註</span><span class="sxs-lookup"><span data-stu-id="a23b9-109">Remarks</span></span>

<span data-ttu-id="a23b9-110">在類別或結構類型中定義欄位通常是使用 `let` 繫結。</span><span class="sxs-lookup"><span data-stu-id="a23b9-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="a23b9-111">不過，`let` 繫結必須在類別建構函式中初始化，但不一定總是可行、必要或適合。</span><span class="sxs-lookup"><span data-stu-id="a23b9-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="a23b9-112">當您想要未初始化的欄位時，您可以使用 `val` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a23b9-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="a23b9-113">明確欄位可以是靜態或非靜態。</span><span class="sxs-lookup"><span data-stu-id="a23b9-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="a23b9-114">*存取修飾詞*可以是`public`， `private`，或`internal`。</span><span class="sxs-lookup"><span data-stu-id="a23b9-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="a23b9-115">根據預設，明確欄位是 public。</span><span class="sxs-lookup"><span data-stu-id="a23b9-115">By default, explicit fields are public.</span></span> <span data-ttu-id="a23b9-116">這不同於類別中永遠是 private 的 `let` 繫結。</span><span class="sxs-lookup"><span data-stu-id="a23b9-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="a23b9-117">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58)上具有主要建構函式的類別類型中，明確欄位需要屬性。</span><span class="sxs-lookup"><span data-stu-id="a23b9-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="a23b9-118">這個屬性指定欄位初始化為零。</span><span class="sxs-lookup"><span data-stu-id="a23b9-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="a23b9-119">欄位的類型必須支援零初始化。</span><span class="sxs-lookup"><span data-stu-id="a23b9-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="a23b9-120">下列類型支援零初始化：</span><span class="sxs-lookup"><span data-stu-id="a23b9-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="a23b9-121">具有零值的基本類型。</span><span class="sxs-lookup"><span data-stu-id="a23b9-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="a23b9-122">支援 null 值的類型，可能為正常值、異常值或值的一種表示法。</span><span class="sxs-lookup"><span data-stu-id="a23b9-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="a23b9-123">這包括類別、Tuple、記錄、函式、介面、.NET 參考類型、`unit` 類型，以及差別聯集類型。</span><span class="sxs-lookup"><span data-stu-id="a23b9-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="a23b9-124">.NET 實值類型。</span><span class="sxs-lookup"><span data-stu-id="a23b9-124">A .NET value type.</span></span>

- <span data-ttu-id="a23b9-125">所有欄位都支援預設零值的一種結構。</span><span class="sxs-lookup"><span data-stu-id="a23b9-125">A structure whose fields all support a default zero value.</span></span>

<span data-ttu-id="a23b9-126">例如，稱為 `someField` 的不可變動欄位在 .NET 編譯表示法中有一個名稱為 `someField@` 的支援欄位，您可以使用名為 `someField` 的屬性來存取儲存的值。</span><span class="sxs-lookup"><span data-stu-id="a23b9-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="a23b9-127">對於可變動欄位，.NET 編譯表示法是 .NET 欄位。</span><span class="sxs-lookup"><span data-stu-id="a23b9-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>

>[!WARNING]
<span data-ttu-id="a23b9-128">`Note` .NET Framework 命名空間`System.ComponentModel`包含具有相同名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="a23b9-128">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="a23b9-129">如需此屬性的詳細資訊，請參閱 `System.ComponentModel.DefaultValueAttribute`。</span><span class="sxs-lookup"><span data-stu-id="a23b9-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>

<span data-ttu-id="a23b9-130">下列程式碼示範在具有主要建構函式的類別中使用明確欄位，也示範 `let` 繫結，方便對照。</span><span class="sxs-lookup"><span data-stu-id="a23b9-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="a23b9-131">請注意，`let` 繫結的欄位 `myInt1` 是 private。</span><span class="sxs-lookup"><span data-stu-id="a23b9-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="a23b9-132">從成員方法參考 `let` 繫結欄位 `myInt1` 時，不需要自我識別項 `this`。</span><span class="sxs-lookup"><span data-stu-id="a23b9-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="a23b9-133">但是，當您參考明確欄位 `myInt2` 和 `myString` 時，需要自我識別項。</span><span class="sxs-lookup"><span data-stu-id="a23b9-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="a23b9-134">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="a23b9-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="a23b9-135">下列程式碼示範在沒有主要建構函式的類別中使用明確欄位。</span><span class="sxs-lookup"><span data-stu-id="a23b9-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="a23b9-136">在此例子中，`DefaultValue` 屬性不是必要的，但在類型所定義的建構函式中必須初始化所有欄位。</span><span class="sxs-lookup"><span data-stu-id="a23b9-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="a23b9-137">輸出為 `35 22`。</span><span class="sxs-lookup"><span data-stu-id="a23b9-137">The output is `35 22`.</span></span>

<span data-ttu-id="a23b9-138">下列程式碼示範在結構中使用明確欄位。</span><span class="sxs-lookup"><span data-stu-id="a23b9-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="a23b9-139">因為結構是實值類型，所以自動有預設建構函式將其欄位的值設定為零。</span><span class="sxs-lookup"><span data-stu-id="a23b9-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="a23b9-140">因此，不需要 `DefaultValue` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a23b9-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="a23b9-141">輸出為 `11 xyz`。</span><span class="sxs-lookup"><span data-stu-id="a23b9-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="a23b9-142">平常不適合使用明確欄位。</span><span class="sxs-lookup"><span data-stu-id="a23b9-142">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="a23b9-143">一般而言，可能的話，應該在類別中使用 `let` 繫結，而不是明確欄位。</span><span class="sxs-lookup"><span data-stu-id="a23b9-143">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="a23b9-144">在某些互通性案例中，例如您需要定義結構供平台叫用呼叫原生 API，或在 COM interop 案例中，明確欄位很有用。</span><span class="sxs-lookup"><span data-stu-id="a23b9-144">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="a23b9-145">如需詳細資訊，請參閱 <<c0> [ 外部函式](../functions/external-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="a23b9-145">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="a23b9-146">另一種情況是您使用 F# 程式碼產生器來產生沒有主要建構函式的類別，這時也可能需要明確欄位。</span><span class="sxs-lookup"><span data-stu-id="a23b9-146">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="a23b9-147">對於執行緒靜態變數或類似的建構，明確欄位也很有用。</span><span class="sxs-lookup"><span data-stu-id="a23b9-147">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="a23b9-148">如需詳細資訊，請參閱`System.ThreadStaticAttribute`。</span><span class="sxs-lookup"><span data-stu-id="a23b9-148">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="a23b9-149">當關鍵字 `member val` 一起出現在類型定義中時，這是自動實作屬性的定義。</span><span class="sxs-lookup"><span data-stu-id="a23b9-149">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="a23b9-150">如需詳細資訊，請參閱 <<c0> [ 屬性](properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a23b9-150">For more information, see [Properties](properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a23b9-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a23b9-151">See also</span></span>

- [<span data-ttu-id="a23b9-152">屬性</span><span class="sxs-lookup"><span data-stu-id="a23b9-152">Properties</span></span>](properties.md)
- [<span data-ttu-id="a23b9-153">成員</span><span class="sxs-lookup"><span data-stu-id="a23b9-153">Members</span></span>](index.md)
- [<span data-ttu-id="a23b9-154">類別中的 `let` 繫結</span><span class="sxs-lookup"><span data-stu-id="a23b9-154">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
