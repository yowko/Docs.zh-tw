---
title: MustOverride (Visual Basic)
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
ms.openlocfilehash: 0ddd7d0d2a57afc02aa7483ba5e83b65c48af534
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822813"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="3629a-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3629a-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="3629a-103">指定屬性或程序不這個類別中實作，而且必須覆寫衍生類別中才可以使用。</span><span class="sxs-lookup"><span data-stu-id="3629a-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3629a-104">備註</span><span class="sxs-lookup"><span data-stu-id="3629a-104">Remarks</span></span>  
 <span data-ttu-id="3629a-105">您只能在屬性或程序宣告陳述式中使用 `MustOverride`。</span><span class="sxs-lookup"><span data-stu-id="3629a-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="3629a-106">屬性或程序，指定`MustOverride`必須是類別的成員，且該類別必須標示[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。</span><span class="sxs-lookup"><span data-stu-id="3629a-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3629a-107">規則</span><span class="sxs-lookup"><span data-stu-id="3629a-107">Rules</span></span>  
  
-   <span data-ttu-id="3629a-108">**不完整的宣告。**</span><span class="sxs-lookup"><span data-stu-id="3629a-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="3629a-109">當您指定`MustOverride`，您未提供任何額外的數行程式碼的屬性或程序中，不甚至`End Function`， `End Property`，或`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3629a-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="3629a-110">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="3629a-110">**Combined Modifiers.**</span></span> <span data-ttu-id="3629a-111">您無法指定`MustOverride`連同`NotOverridable`， `Overridable`，或`Shared`相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="3629a-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="3629a-112">**遮蔽和覆寫。**</span><span class="sxs-lookup"><span data-stu-id="3629a-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="3629a-113">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="3629a-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="3629a-114">如需詳細資訊，請參閱 < [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="3629a-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="3629a-115">**替代的字詞。**</span><span class="sxs-lookup"><span data-stu-id="3629a-115">**Alternate Terms.**</span></span> <span data-ttu-id="3629a-116">不使用以外，覆寫中的項目有時稱為*純虛擬*項目。</span><span class="sxs-lookup"><span data-stu-id="3629a-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="3629a-117">`MustOverride` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="3629a-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3629a-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="3629a-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="3629a-119">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="3629a-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="3629a-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="3629a-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3629a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3629a-121">See also</span></span>

- [<span data-ttu-id="3629a-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="3629a-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="3629a-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="3629a-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="3629a-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="3629a-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="3629a-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="3629a-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="3629a-126">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3629a-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="3629a-127">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="3629a-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
