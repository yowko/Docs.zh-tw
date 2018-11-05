---
title: 存取控制 (F#)
description: 了解如何控制存取權等型別、 方法和函式，在 F# 程式設計語言的程式設計項目。
ms.date: 05/16/2016
ms.openlocfilehash: 66a260d326acf07391e3775e5a7853654b4feee4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43803970"
---
# <a name="access-control"></a><span data-ttu-id="28477-103">存取控制</span><span class="sxs-lookup"><span data-stu-id="28477-103">Access Control</span></span>

<span data-ttu-id="28477-104">*存取控制*指宣告哪些用戶端可以使用特定程式項目，例如類型、 方法和函式。</span><span class="sxs-lookup"><span data-stu-id="28477-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="28477-105">存取控制的基本概念</span><span class="sxs-lookup"><span data-stu-id="28477-105">Basics of Access Control</span></span>

<span data-ttu-id="28477-106">在 F# 中，存取控制規範`public`， `internal`，和`private`可以套用至模組、 類型、 方法、 值的定義，函式、 屬性和明確欄位。</span><span class="sxs-lookup"><span data-stu-id="28477-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="28477-107">`public` 指出所有呼叫端可以存取實體。</span><span class="sxs-lookup"><span data-stu-id="28477-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="28477-108">`internal` 表示實體，可以存取只能從相同的組件。</span><span class="sxs-lookup"><span data-stu-id="28477-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="28477-109">`private` 表示實體，可以存取只能從封入類型或模組。</span><span class="sxs-lookup"><span data-stu-id="28477-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

>[!NOTE]
<span data-ttu-id="28477-110">存取規範`protected`未使用在 F# 中，雖然它是可接受的如果您正在使用中支援的語言撰寫的類型`protected`存取。</span><span class="sxs-lookup"><span data-stu-id="28477-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="28477-111">因此，如果您覆寫受保護的方法，您的方法仍然只能在類別和其下階中存取。</span><span class="sxs-lookup"><span data-stu-id="28477-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="28477-112">一般情況下，規範放，除非在實體的名稱前面`mutable`或`inline`使用規範時，會在存取控制規範之後。</span><span class="sxs-lookup"><span data-stu-id="28477-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="28477-113">如果沒有存取規範，則預設值是`public`，除了`let`型別，其一律為繫結`private`為型別。</span><span class="sxs-lookup"><span data-stu-id="28477-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="28477-114">F# 中的簽章提供另一個機制來控制存取權 F# 程式項目。</span><span class="sxs-lookup"><span data-stu-id="28477-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="28477-115">簽章並不需要存取控制。</span><span class="sxs-lookup"><span data-stu-id="28477-115">Signatures are not required for access control.</span></span> <span data-ttu-id="28477-116">如需詳細資訊，請參閱[簽章](signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="28477-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="28477-117">存取控制規則</span><span class="sxs-lookup"><span data-stu-id="28477-117">Rules for Access Control</span></span>

<span data-ttu-id="28477-118">存取控制受限於下列規則：</span><span class="sxs-lookup"><span data-stu-id="28477-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="28477-119">繼承的宣告 (也就是使用`inherit`指定類別的基底類別)、 介面宣告 （也就，指定類別實作的介面），和擷取成員一律具有相同的存取範圍，為封入類型。</span><span class="sxs-lookup"><span data-stu-id="28477-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="28477-120">因此，存取控制規範不能使用這些建構。</span><span class="sxs-lookup"><span data-stu-id="28477-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="28477-121">差別等位中的個別案例的存取範圍取決於已區分的聯集本身的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="28477-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="28477-122">也就是特定聯集是不比聯集本身存取。</span><span class="sxs-lookup"><span data-stu-id="28477-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="28477-123">協助工具的記錄類型的個別欄位不能取決於記錄本身的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="28477-123">Accessibility for individual fields of a record type cannot is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="28477-124">也就是特定的記錄標籤是不比記錄本身存取。</span><span class="sxs-lookup"><span data-stu-id="28477-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="28477-125">範例</span><span class="sxs-lookup"><span data-stu-id="28477-125">Example</span></span>

<span data-ttu-id="28477-126">下列程式碼說明如何使用存取控制的規範。</span><span class="sxs-lookup"><span data-stu-id="28477-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="28477-127">在專案中，有兩個檔案`Module1.fs`和`Module2.fs`。</span><span class="sxs-lookup"><span data-stu-id="28477-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="28477-128">每個檔案是以隱含方式的模組。</span><span class="sxs-lookup"><span data-stu-id="28477-128">Each file is implicitly a module.</span></span> <span data-ttu-id="28477-129">因此，有兩個模組，`Module1`和`Module2`。</span><span class="sxs-lookup"><span data-stu-id="28477-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="28477-130">私用類型和一個內部型別會定義在`Module1`。</span><span class="sxs-lookup"><span data-stu-id="28477-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="28477-131">無法從存取私用類型`Module2`，但是內部型別。</span><span class="sxs-lookup"><span data-stu-id="28477-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="28477-132">下列程式碼測試中建立型別的存取範圍`Module1.fs`。</span><span class="sxs-lookup"><span data-stu-id="28477-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="28477-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28477-133">See also</span></span>

- [<span data-ttu-id="28477-134">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="28477-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="28477-135">簽章</span><span class="sxs-lookup"><span data-stu-id="28477-135">Signatures</span></span>](signatures.md)
