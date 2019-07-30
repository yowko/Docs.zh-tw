---
title: 存取控制
description: 瞭解如何以程式F#設計語言控制程式設計專案 (例如類型、方法和函式) 的存取。
ms.date: 05/16/2016
ms.openlocfilehash: ed77a09cf87aabf9a4134276e89e84aa42abd3c3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629967"
---
# <a name="access-control"></a><span data-ttu-id="8c26b-103">存取控制</span><span class="sxs-lookup"><span data-stu-id="8c26b-103">Access Control</span></span>

<span data-ttu-id="8c26b-104">*存取控制*是指宣告哪些用戶端可以使用特定的程式元素, 例如類型、方法和函式。</span><span class="sxs-lookup"><span data-stu-id="8c26b-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="8c26b-105">存取控制的基本概念</span><span class="sxs-lookup"><span data-stu-id="8c26b-105">Basics of Access Control</span></span>

<span data-ttu-id="8c26b-106">在F#中, 存取控制`public`規範、 `internal`和`private`可以套用至模組、類型、方法、值定義、函數、屬性和明確欄位。</span><span class="sxs-lookup"><span data-stu-id="8c26b-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="8c26b-107">`public`表示實體可由所有呼叫者存取。</span><span class="sxs-lookup"><span data-stu-id="8c26b-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="8c26b-108">`internal`表示實體只能從相同的元件存取。</span><span class="sxs-lookup"><span data-stu-id="8c26b-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="8c26b-109">`private`表示實體只能從封入類型或模組存取。</span><span class="sxs-lookup"><span data-stu-id="8c26b-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="8c26b-110">存取規範`protected`不會用於中F#, 但如果您使用的類型是以支援`protected`存取的語言撰寫, 則此為可接受的。</span><span class="sxs-lookup"><span data-stu-id="8c26b-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="8c26b-111">因此, 如果您覆寫受保護的方法, 您的方法只會在類別和其子代內保持可存取狀態。</span><span class="sxs-lookup"><span data-stu-id="8c26b-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="8c26b-112">一般來說, 規範會放在機構名稱的前方, 但使用`mutable`或`inline`規範時 (出現在存取控制規範之後) 除外。</span><span class="sxs-lookup"><span data-stu-id="8c26b-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="8c26b-113">如果未使用存取規範, 則預設值為`public`, `let`但類型中的系結一律`private`會是類型。</span><span class="sxs-lookup"><span data-stu-id="8c26b-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="8c26b-114">中F#的簽章提供另一個機制來F#控制程式元素的存取。</span><span class="sxs-lookup"><span data-stu-id="8c26b-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="8c26b-115">存取控制不需要簽章。</span><span class="sxs-lookup"><span data-stu-id="8c26b-115">Signatures are not required for access control.</span></span> <span data-ttu-id="8c26b-116">如需詳細資訊，請參閱[簽章](signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="8c26b-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="8c26b-117">存取控制的規則</span><span class="sxs-lookup"><span data-stu-id="8c26b-117">Rules for Access Control</span></span>

<span data-ttu-id="8c26b-118">存取控制受限於下列規則:</span><span class="sxs-lookup"><span data-stu-id="8c26b-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="8c26b-119">繼承宣告 (也就是使用`inherit`來指定類別的基類)、介面宣告 (也就是指定類別實作為介面), 而抽象成員一律具有與封入類型相同的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="8c26b-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="8c26b-120">因此, 您無法在這些結構上使用存取控制規範。</span><span class="sxs-lookup"><span data-stu-id="8c26b-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="8c26b-121">區分等位中個別案例的協助工具是由區分聯集本身的存取範圍所決定。</span><span class="sxs-lookup"><span data-stu-id="8c26b-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="8c26b-122">也就是說, 特定聯集的大小寫不會比等位本身更容易存取。</span><span class="sxs-lookup"><span data-stu-id="8c26b-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="8c26b-123">記錄類型之個別欄位的協助工具不能由記錄本身的存取範圍決定。</span><span class="sxs-lookup"><span data-stu-id="8c26b-123">Accessibility for individual fields of a record type cannot is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="8c26b-124">也就是說, 特定記錄標籤的存取權不如記錄本身。</span><span class="sxs-lookup"><span data-stu-id="8c26b-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="8c26b-125">範例</span><span class="sxs-lookup"><span data-stu-id="8c26b-125">Example</span></span>

<span data-ttu-id="8c26b-126">下列程式碼說明如何使用存取控制規範。</span><span class="sxs-lookup"><span data-stu-id="8c26b-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="8c26b-127">專案中有兩個檔案: `Module1.fs`和。 `Module2.fs`</span><span class="sxs-lookup"><span data-stu-id="8c26b-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="8c26b-128">每個檔案都是隱含的模組。</span><span class="sxs-lookup"><span data-stu-id="8c26b-128">Each file is implicitly a module.</span></span> <span data-ttu-id="8c26b-129">因此, 有兩個模組: `Module1`和`Module2`。</span><span class="sxs-lookup"><span data-stu-id="8c26b-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="8c26b-130">私用型別和內部型別定義于`Module1`中。</span><span class="sxs-lookup"><span data-stu-id="8c26b-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="8c26b-131">無法從存取私用`Module2`型別, 但內部型別可以。</span><span class="sxs-lookup"><span data-stu-id="8c26b-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="8c26b-132">下列程式碼會測試在中`Module1.fs`建立之類型的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="8c26b-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="8c26b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c26b-133">See also</span></span>

- [<span data-ttu-id="8c26b-134">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="8c26b-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8c26b-135">簽章</span><span class="sxs-lookup"><span data-stu-id="8c26b-135">Signatures</span></span>](signatures.md)
