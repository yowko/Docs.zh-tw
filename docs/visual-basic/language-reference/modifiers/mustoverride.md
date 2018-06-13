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
ms.openlocfilehash: 5dabd90d29bc41d017436876af24a67fa87e8e17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599866"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="569d1-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="569d1-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="569d1-103">指定屬性或程序不此類別中實作，而且必須覆寫衍生類別中才可以使用。</span><span class="sxs-lookup"><span data-stu-id="569d1-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="569d1-104">備註</span><span class="sxs-lookup"><span data-stu-id="569d1-104">Remarks</span></span>  
 <span data-ttu-id="569d1-105">您只能在屬性或程序宣告陳述式中使用 `MustOverride`。</span><span class="sxs-lookup"><span data-stu-id="569d1-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="569d1-106">屬性或程序，指定`MustOverride`必須是類別的成員，且該類別必須標示[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。</span><span class="sxs-lookup"><span data-stu-id="569d1-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="569d1-107">規則</span><span class="sxs-lookup"><span data-stu-id="569d1-107">Rules</span></span>  
  
-   <span data-ttu-id="569d1-108">**不完整的宣告。**</span><span class="sxs-lookup"><span data-stu-id="569d1-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="569d1-109">當您指定`MustOverride`，您沒有不提供任何額外的數行程式碼的屬性或程序，即使`End Function`， `End Property`，或`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="569d1-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="569d1-110">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="569d1-110">**Combined Modifiers.**</span></span> <span data-ttu-id="569d1-111">您無法指定`MustOverride`搭配`NotOverridable`， `Overridable`，或`Shared`相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="569d1-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="569d1-112">**遮蔽和覆寫。**</span><span class="sxs-lookup"><span data-stu-id="569d1-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="569d1-113">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="569d1-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="569d1-114">如需詳細資訊，請參閱[Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="569d1-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="569d1-115">**其他條款。**</span><span class="sxs-lookup"><span data-stu-id="569d1-115">**Alternate Terms.**</span></span> <span data-ttu-id="569d1-116">無法覆寫中使用以外的項目有時稱為*純虛擬*項目。</span><span class="sxs-lookup"><span data-stu-id="569d1-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="569d1-117">`MustOverride` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="569d1-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="569d1-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="569d1-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="569d1-119">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="569d1-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="569d1-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="569d1-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="569d1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="569d1-121">See Also</span></span>  
 [<span data-ttu-id="569d1-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="569d1-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="569d1-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="569d1-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="569d1-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="569d1-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="569d1-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="569d1-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="569d1-126">關鍵字</span><span class="sxs-lookup"><span data-stu-id="569d1-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="569d1-127">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="569d1-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
