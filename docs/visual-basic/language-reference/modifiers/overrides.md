---
title: 覆寫
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 657f838b2959a5b6a7cef5ff18295a4ada709e9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392024"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="e54d6-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e54d6-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="e54d6-103">指定屬性或程序會覆寫繼承自基底類別的同名屬性或程序。</span><span class="sxs-lookup"><span data-stu-id="e54d6-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="e54d6-104">規則</span><span class="sxs-lookup"><span data-stu-id="e54d6-104">Rules</span></span>

- <span data-ttu-id="e54d6-105">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="e54d6-105">**Declaration Context.**</span></span> <span data-ttu-id="e54d6-106">您 `Overrides` 只能在屬性或程式宣告語句中使用。</span><span class="sxs-lookup"><span data-stu-id="e54d6-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="e54d6-107">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="e54d6-107">**Combined Modifiers.**</span></span> <span data-ttu-id="e54d6-108">您不能在 `Overrides` `Shadows` 相同的宣告中搭配或一起指定 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="e54d6-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="e54d6-109">因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="e54d6-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="e54d6-110">**相符簽章。**</span><span class="sxs-lookup"><span data-stu-id="e54d6-110">**Matching Signatures.**</span></span> <span data-ttu-id="e54d6-111">這個宣告的簽章必須與它所覆寫之屬性或*程式的簽*章完全相符。</span><span class="sxs-lookup"><span data-stu-id="e54d6-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="e54d6-112">這表示的參數清單必須有相同數目的參數、相同的順序及相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e54d6-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="e54d6-113">除了簽章，覆寫宣告也必須完全符合下列各項：</span><span class="sxs-lookup"><span data-stu-id="e54d6-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="e54d6-114">存取層級</span><span class="sxs-lookup"><span data-stu-id="e54d6-114">The access level</span></span>

  - <span data-ttu-id="e54d6-115">傳回類型 (如果有的話)</span><span class="sxs-lookup"><span data-stu-id="e54d6-115">The return type, if any</span></span>

- <span data-ttu-id="e54d6-116">**泛型簽章。**</span><span class="sxs-lookup"><span data-stu-id="e54d6-116">**Generic Signatures.**</span></span> <span data-ttu-id="e54d6-117">在泛型程序中，簽章包含類型參數的個數。</span><span class="sxs-lookup"><span data-stu-id="e54d6-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="e54d6-118">因此，覆寫宣告在這方面也必須符合基底類別版本。</span><span class="sxs-lookup"><span data-stu-id="e54d6-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="e54d6-119">**其他符合。**</span><span class="sxs-lookup"><span data-stu-id="e54d6-119">**Additional Matching.**</span></span> <span data-ttu-id="e54d6-120">除了符合簽章的基底類別版本，此宣告在下列方面也必須符合它：</span><span class="sxs-lookup"><span data-stu-id="e54d6-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="e54d6-121">存取層級修飾詞（例如[Public](public.md)）</span><span class="sxs-lookup"><span data-stu-id="e54d6-121">Access-level modifier (such as [Public](public.md))</span></span>

  - <span data-ttu-id="e54d6-122">每個參數的傳遞機制（[ByVal](byval.md)或[ByRef](byref.md)）</span><span class="sxs-lookup"><span data-stu-id="e54d6-122">Passing mechanism of each parameter ([ByVal](byval.md) or [ByRef](byref.md))</span></span>

  - <span data-ttu-id="e54d6-123">泛型程序的每個類型參數的條件約束清單</span><span class="sxs-lookup"><span data-stu-id="e54d6-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="e54d6-124">**遮蔽和覆寫。**</span><span class="sxs-lookup"><span data-stu-id="e54d6-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="e54d6-125">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="e54d6-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="e54d6-126">如需詳細資訊，請參閱[Visual Basic 中的陰影](../../programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="e54d6-126">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="e54d6-127">如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C#。</span><span class="sxs-lookup"><span data-stu-id="e54d6-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="e54d6-128">`Overrides` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="e54d6-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="e54d6-129">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="e54d6-129">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="e54d6-130">Property Statement</span><span class="sxs-lookup"><span data-stu-id="e54d6-130">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="e54d6-131">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="e54d6-131">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="e54d6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e54d6-132">See also</span></span>

- [<span data-ttu-id="e54d6-133">New</span><span class="sxs-lookup"><span data-stu-id="e54d6-133">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="e54d6-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e54d6-134">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="e54d6-135">Overrides</span><span class="sxs-lookup"><span data-stu-id="e54d6-135">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="e54d6-136">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e54d6-136">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="e54d6-137">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="e54d6-137">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="e54d6-138">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e54d6-138">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="e54d6-139">Type List</span><span class="sxs-lookup"><span data-stu-id="e54d6-139">Type List</span></span>](../statements/type-list.md)
