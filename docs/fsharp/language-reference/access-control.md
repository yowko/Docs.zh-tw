---
title: "存取控制 (F#)"
description: "了解如何控制對等型別、 方法和函式，F # 程式語言中的程式設計項目。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 955b06fe-d1cd-431d-8db6-93e83b697453
ms.openlocfilehash: a02e20a585a0456577901f2762a0eeb0e3ecd2f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="access-control"></a><span data-ttu-id="27b01-104">存取控制</span><span class="sxs-lookup"><span data-stu-id="27b01-104">Access Control</span></span>

<span data-ttu-id="27b01-105">*存取控制*指的是哪些用戶端可以使用特定程式項目，例如類型、 方法和函式的宣告。</span><span class="sxs-lookup"><span data-stu-id="27b01-105">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>


## <a name="basics-of-access-control"></a><span data-ttu-id="27b01-106">存取控制的基本概念</span><span class="sxs-lookup"><span data-stu-id="27b01-106">Basics of Access Control</span></span>
<span data-ttu-id="27b01-107">F # 中的存取控制規範`public`， `internal`，和`private`可以套用至模組、 類型、 方法、 值定義、 函式、 屬性和明確欄位。</span><span class="sxs-lookup"><span data-stu-id="27b01-107">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>


- <span data-ttu-id="27b01-108">`public`表示所有呼叫端都可以存取實體。</span><span class="sxs-lookup"><span data-stu-id="27b01-108">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="27b01-109">`internal`表示實體，可以存取只能從相同組件。</span><span class="sxs-lookup"><span data-stu-id="27b01-109">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="27b01-110">`private`表示實體，可以存取只能從封入類型或模組。</span><span class="sxs-lookup"><span data-stu-id="27b01-110">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>


>[!NOTE] 
<span data-ttu-id="27b01-111">存取規範`protected`不使用在 F # 中，雖然它是可接受的如果您使用以支援語言所撰寫的型別`protected`存取。</span><span class="sxs-lookup"><span data-stu-id="27b01-111">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="27b01-112">因此，如果您覆寫的受保護的方法，您的方法仍然只能在類別和其下階中存取。</span><span class="sxs-lookup"><span data-stu-id="27b01-112">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="27b01-113">一般情況下，除非為實體的名稱前面放規範`mutable`或`inline`使用規範，而這會在存取控制規範之後。</span><span class="sxs-lookup"><span data-stu-id="27b01-113">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="27b01-114">如果使用沒有存取規範，則預設值是`public`，除了`let`永遠是的型別，繫結`private`型別。</span><span class="sxs-lookup"><span data-stu-id="27b01-114">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="27b01-115">F # 中的簽章提供另一個機制來控制 F # 程式項目的存取。</span><span class="sxs-lookup"><span data-stu-id="27b01-115">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="27b01-116">簽章並不需要存取控制。</span><span class="sxs-lookup"><span data-stu-id="27b01-116">Signatures are not required for access control.</span></span> <span data-ttu-id="27b01-117">如需詳細資訊，請參閱[簽章](signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="27b01-117">For more information, see [Signatures](signatures.md).</span></span>


## <a name="rules-for-access-control"></a><span data-ttu-id="27b01-118">存取控制規則</span><span class="sxs-lookup"><span data-stu-id="27b01-118">Rules for Access Control</span></span>
<span data-ttu-id="27b01-119">存取控制受限於下列規則：</span><span class="sxs-lookup"><span data-stu-id="27b01-119">Access control is subject to the following rules:</span></span>


- <span data-ttu-id="27b01-120">繼承宣告 (也就是使用`inherit`指定類別的基底類別)，介面宣告 （也就，指定類別實作的介面），以及抽象成員一定與封入類型相同的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="27b01-120">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="27b01-121">因此，存取控制規範不能在這些建構函式。</span><span class="sxs-lookup"><span data-stu-id="27b01-121">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="27b01-122">差別等位中的個別案例不能有個別等位型別從其本身存取控制項修飾詞。</span><span class="sxs-lookup"><span data-stu-id="27b01-122">Individual cases in a discriminated union cannot have their own access control modifiers separate from the union type.</span></span>

- <span data-ttu-id="27b01-123">記錄類型的個別欄位不能有不同的記錄類型自己存取控制修飾詞。</span><span class="sxs-lookup"><span data-stu-id="27b01-123">Individual fields of a record type cannot have their own access control modifiers separate from the record type.</span></span>


## <a name="example"></a><span data-ttu-id="27b01-124">範例</span><span class="sxs-lookup"><span data-stu-id="27b01-124">Example</span></span>
<span data-ttu-id="27b01-125">下列程式碼說明如何使用存取控制規範。</span><span class="sxs-lookup"><span data-stu-id="27b01-125">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="27b01-126">在專案中，有兩個檔案`Module1.fs`和`Module2.fs`。</span><span class="sxs-lookup"><span data-stu-id="27b01-126">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="27b01-127">每個檔案是以隱含方式的模組。</span><span class="sxs-lookup"><span data-stu-id="27b01-127">Each file is implicitly a module.</span></span> <span data-ttu-id="27b01-128">因此，有兩個模組，`Module1`和`Module2`。</span><span class="sxs-lookup"><span data-stu-id="27b01-128">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="27b01-129">私用類型和內部類型會定義在`Module1`。</span><span class="sxs-lookup"><span data-stu-id="27b01-129">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="27b01-130">無法從存取私用類型`Module2`，但可以內部型別。</span><span class="sxs-lookup"><span data-stu-id="27b01-130">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
<span data-ttu-id="27b01-131">下列程式碼測試中建立的類型的存取範圍`Module1.fs`。</span><span class="sxs-lookup"><span data-stu-id="27b01-131">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a><span data-ttu-id="27b01-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27b01-132">See Also</span></span>
[<span data-ttu-id="27b01-133">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="27b01-133">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="27b01-134">簽章</span><span class="sxs-lookup"><span data-stu-id="27b01-134">Signatures</span></span>](signatures.md)
