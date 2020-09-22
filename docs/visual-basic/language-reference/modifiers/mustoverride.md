---
title: New
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: cf73f07b6e13d524281129e3c5d8dceceb90764c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867939"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="d25df-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d25df-102">MustOverride (Visual Basic)</span></span>

<span data-ttu-id="d25df-103">指定屬性或程式不會在此類別中執行，而且必須在衍生類別中覆寫，才能加以使用。</span><span class="sxs-lookup"><span data-stu-id="d25df-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d25df-104">備註</span><span class="sxs-lookup"><span data-stu-id="d25df-104">Remarks</span></span>  

 <span data-ttu-id="d25df-105">您 `MustOverride` 只能在屬性或程式聲明語句中使用。</span><span class="sxs-lookup"><span data-stu-id="d25df-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="d25df-106">指定的屬性或程式 `MustOverride` 必須是類別的成員，而且類別必須標記為 [MustInherit](mustinherit.md)。</span><span class="sxs-lookup"><span data-stu-id="d25df-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d25df-107">規則</span><span class="sxs-lookup"><span data-stu-id="d25df-107">Rules</span></span>  
  
- <span data-ttu-id="d25df-108">**不完整的宣告。**</span><span class="sxs-lookup"><span data-stu-id="d25df-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="d25df-109">當您指定時，不會 `MustOverride` 為屬性或程式提供任何額外的程式程式碼，甚至是 `End Function` 、 `End Property` 或 `End Sub` 語句。</span><span class="sxs-lookup"><span data-stu-id="d25df-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="d25df-110">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="d25df-110">**Combined Modifiers.**</span></span> <span data-ttu-id="d25df-111">您無法 `MustOverride` 在相同的宣告中同時指定和 `NotOverridable` 、 `Overridable` 或 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="d25df-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="d25df-112">**遮蔽和覆寫。**</span><span class="sxs-lookup"><span data-stu-id="d25df-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="d25df-113">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="d25df-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="d25df-114">如需詳細資訊，請參閱 [Visual Basic 中的遮蔽](../../programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="d25df-114">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="d25df-115">**替代條款。**</span><span class="sxs-lookup"><span data-stu-id="d25df-115">**Alternate Terms.**</span></span> <span data-ttu-id="d25df-116">除了在覆寫之外，無法使用的元素有時也稱為 *純虛擬* 元素。</span><span class="sxs-lookup"><span data-stu-id="d25df-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="d25df-117">`MustOverride` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="d25df-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d25df-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d25df-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="d25df-119">Property Statement</span><span class="sxs-lookup"><span data-stu-id="d25df-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="d25df-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d25df-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d25df-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d25df-121">See also</span></span>

- [<span data-ttu-id="d25df-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d25df-122">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="d25df-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="d25df-123">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="d25df-124">覆寫</span><span class="sxs-lookup"><span data-stu-id="d25df-124">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="d25df-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="d25df-125">MustInherit</span></span>](mustinherit.md)
- [<span data-ttu-id="d25df-126">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d25df-126">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="d25df-127">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="d25df-127">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
