---
title: Overloads
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 44823b409cfa81dc889aabacf101fac90bf851e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351415"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="51587-102">Overloads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51587-102">Overloads (Visual Basic)</span></span>

<span data-ttu-id="51587-103">指定屬性或程序會重新宣告一或多個同名的現有屬性或程序。</span><span class="sxs-lookup"><span data-stu-id="51587-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>

## <a name="remarks"></a><span data-ttu-id="51587-104">備註</span><span class="sxs-lookup"><span data-stu-id="51587-104">Remarks</span></span>

<span data-ttu-id="51587-105">多*載是針對*相同範圍內的指定屬性或程式名稱提供一個以上定義的作法。</span><span class="sxs-lookup"><span data-stu-id="51587-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="51587-106">以不同的簽章重新宣告屬性或程式，有時稱為*依*簽章隱藏。</span><span class="sxs-lookup"><span data-stu-id="51587-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>

## <a name="rules"></a><span data-ttu-id="51587-107">規則</span><span class="sxs-lookup"><span data-stu-id="51587-107">Rules</span></span>

- <span data-ttu-id="51587-108">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="51587-108">**Declaration Context.**</span></span> <span data-ttu-id="51587-109">您只能在屬性或程式宣告語句中使用 `Overloads`。</span><span class="sxs-lookup"><span data-stu-id="51587-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="51587-110">**合併的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="51587-110">**Combined Modifiers.**</span></span> <span data-ttu-id="51587-111">您不能在相同的程式宣告中同時指定 `Overloads` 與[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) 。</span><span class="sxs-lookup"><span data-stu-id="51587-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>

- <span data-ttu-id="51587-112">**必要的差異。**</span><span class="sxs-lookup"><span data-stu-id="51587-112">**Required Differences.**</span></span> <span data-ttu-id="51587-113">此*宣告中的*簽章必須與它多載之每個屬性或程式的簽章不同。</span><span class="sxs-lookup"><span data-stu-id="51587-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="51587-114">簽章包含屬性或程序名稱，以及下列項目：</span><span class="sxs-lookup"><span data-stu-id="51587-114">The signature comprises the property or procedure name together with the following:</span></span>

  - <span data-ttu-id="51587-115">參數的數目</span><span class="sxs-lookup"><span data-stu-id="51587-115">the number of parameters</span></span>

  - <span data-ttu-id="51587-116">參數的順序</span><span class="sxs-lookup"><span data-stu-id="51587-116">the order of the parameters</span></span>

  - <span data-ttu-id="51587-117">參數的資料類型</span><span class="sxs-lookup"><span data-stu-id="51587-117">the data types of the parameters</span></span>

  - <span data-ttu-id="51587-118">類型參數的數目 (適用於泛型程序)</span><span class="sxs-lookup"><span data-stu-id="51587-118">the number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="51587-119">傳回型別 (僅適用於轉換運算子程序)</span><span class="sxs-lookup"><span data-stu-id="51587-119">the return type (only for a conversion operator procedure)</span></span>

  <span data-ttu-id="51587-120">所有多載必須有相同的名稱，但每個多載的名稱在一或多個上述方面中必須和其他多載不同。</span><span class="sxs-lookup"><span data-stu-id="51587-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="51587-121">這可讓編譯器在程式碼呼叫屬性或程序時可識別要使用的版本。</span><span class="sxs-lookup"><span data-stu-id="51587-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>

- <span data-ttu-id="51587-122">**不允許的差異。**</span><span class="sxs-lookup"><span data-stu-id="51587-122">**Disallowed Differences.**</span></span> <span data-ttu-id="51587-123">變更下列一或多個項目，對於多載屬性或程序是無效的，因為它們屬於簽章：</span><span class="sxs-lookup"><span data-stu-id="51587-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>

  - <span data-ttu-id="51587-124">是否傳回值 (適用於程序)</span><span class="sxs-lookup"><span data-stu-id="51587-124">whether or not it returns a value (for a procedure)</span></span>

  - <span data-ttu-id="51587-125">傳回值的資料類型 (除了轉換運算子之外)</span><span class="sxs-lookup"><span data-stu-id="51587-125">the data type of the return value (except for a conversion operator)</span></span>

  - <span data-ttu-id="51587-126">參數或型別參數的名稱</span><span class="sxs-lookup"><span data-stu-id="51587-126">the names of the parameters or type parameters</span></span>

  - <span data-ttu-id="51587-127">類型參數上的條件約束 (適用於泛型程序)</span><span class="sxs-lookup"><span data-stu-id="51587-127">the constraints on the type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="51587-128">參數修飾詞關鍵字 (例如 `ByRef` 或 `Optional`)</span><span class="sxs-lookup"><span data-stu-id="51587-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>

  - <span data-ttu-id="51587-129">屬性或程序修飾詞關鍵字 (例如 `Public` 或 `Shared`)</span><span class="sxs-lookup"><span data-stu-id="51587-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>

- <span data-ttu-id="51587-130">**選擇性的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="51587-130">**Optional Modifier.**</span></span> <span data-ttu-id="51587-131">當您在同一個類別中定義多個多載屬性或程式時，不需要使用 `Overloads` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="51587-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="51587-132">不過，如果您在其中一個宣告中使用 `Overloads`，您必須在全部的宣告中使用它。</span><span class="sxs-lookup"><span data-stu-id="51587-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>

- <span data-ttu-id="51587-133">**遮蔽和多載。**</span><span class="sxs-lookup"><span data-stu-id="51587-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="51587-134">`Overloads` 也可以用來在基類中遮蔽現有的成員或一組多載成員。</span><span class="sxs-lookup"><span data-stu-id="51587-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="51587-135">以此方式使用 `Overloads` 時，即表示您會宣告同名的屬性或方法和相同的參數清單作為基底類別成員，而且您並未提供 `Shadows` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="51587-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>

<span data-ttu-id="51587-136">如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C#。</span><span class="sxs-lookup"><span data-stu-id="51587-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="51587-137">`Overloads` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="51587-137">The `Overloads` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="51587-138">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="51587-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="51587-139">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="51587-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)

- [<span data-ttu-id="51587-140">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="51587-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="51587-141">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="51587-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="51587-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="51587-142">See also</span></span>

- [<span data-ttu-id="51587-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="51587-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="51587-144">程序多載化</span><span class="sxs-lookup"><span data-stu-id="51587-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="51587-145">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="51587-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="51587-146">運算子程序</span><span class="sxs-lookup"><span data-stu-id="51587-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="51587-147">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="51587-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
