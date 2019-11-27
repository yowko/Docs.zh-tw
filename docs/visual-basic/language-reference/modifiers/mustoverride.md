---
title: MustOverride
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
ms.openlocfilehash: dc6a153a604fd0e5cee9d7d46ebcd63294f33628
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351487"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="a2df6-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2df6-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="a2df6-103">指定在這個類別中不會實作為屬性或程式，而且必須在衍生類別中加以覆寫，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="a2df6-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2df6-104">備註</span><span class="sxs-lookup"><span data-stu-id="a2df6-104">Remarks</span></span>  
 <span data-ttu-id="a2df6-105">您只能在屬性或程式宣告語句中使用 `MustOverride`。</span><span class="sxs-lookup"><span data-stu-id="a2df6-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="a2df6-106">指定 `MustOverride` 的屬性或程式必須是類別的成員，且類別必須標記為 [ [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)]。</span><span class="sxs-lookup"><span data-stu-id="a2df6-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a2df6-107">規則</span><span class="sxs-lookup"><span data-stu-id="a2df6-107">Rules</span></span>  
  
- <span data-ttu-id="a2df6-108">**不完整的宣告。**</span><span class="sxs-lookup"><span data-stu-id="a2df6-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="a2df6-109">當您指定 `MustOverride`時，不會為屬性或程式提供任何額外的程式程式碼，甚至是 `End Function`、`End Property`或 `End Sub` 語句。</span><span class="sxs-lookup"><span data-stu-id="a2df6-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="a2df6-110">**合併的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="a2df6-110">**Combined Modifiers.**</span></span> <span data-ttu-id="a2df6-111">您不能在相同的宣告中同時指定 `MustOverride` 與 `NotOverridable`、`Overridable`或 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="a2df6-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="a2df6-112">**遮蔽和覆寫。**</span><span class="sxs-lookup"><span data-stu-id="a2df6-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="a2df6-113">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="a2df6-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="a2df6-114">如需詳細資訊，請參閱[Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="a2df6-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="a2df6-115">**替代詞彙。**</span><span class="sxs-lookup"><span data-stu-id="a2df6-115">**Alternate Terms.**</span></span> <span data-ttu-id="a2df6-116">除非在覆寫中，否則無法使用的元素，有時稱為*純虛擬*元素。</span><span class="sxs-lookup"><span data-stu-id="a2df6-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="a2df6-117">`MustOverride` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="a2df6-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a2df6-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="a2df6-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="a2df6-119">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="a2df6-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="a2df6-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="a2df6-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a2df6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2df6-121">See also</span></span>

- [<span data-ttu-id="a2df6-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="a2df6-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="a2df6-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="a2df6-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="a2df6-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="a2df6-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="a2df6-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="a2df6-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="a2df6-126">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a2df6-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="a2df6-127">Visual Basic 中的陰影</span><span class="sxs-lookup"><span data-stu-id="a2df6-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
