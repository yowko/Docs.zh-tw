---
title: 受保護的 Friend （Visual Basic）
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: d3592feaece1d5ce85ee6e2657d8a2715c4097a3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524782"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="e50bf-102">受保護的 Friend （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e50bf-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="e50bf-103">`Protected Friend` 關鍵字組合是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="e50bf-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="e50bf-104">它會在宣告的元素上授[Friend](friend.md)存取和[受保護](protected.md)的存取，因此可以從相同元件中的任何位置、從其本身的類別，以及從衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="e50bf-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="e50bf-105">您只能在類別的成員上指定 `Protected Friend`;您無法將 `Protected Friend` 套用到結構的成員，因為無法繼承結構。</span><span class="sxs-lookup"><span data-stu-id="e50bf-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="e50bf-106">在 Visual Studio 中，選取 [F1 說明] [`protected friend`] 可提供[受保護](protected.md)或[friend](friend.md)的協助。</span><span class="sxs-lookup"><span data-stu-id="e50bf-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="e50bf-107">IDE 會挑選游標下的單一 token，而不是複合字組。</span><span class="sxs-lookup"><span data-stu-id="e50bf-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="e50bf-108">規則</span><span class="sxs-lookup"><span data-stu-id="e50bf-108">Rules</span></span>

<span data-ttu-id="e50bf-109">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="e50bf-109">**Declaration Context.**</span></span> <span data-ttu-id="e50bf-110">您只能在類別層級使用 `Protected Friend`。</span><span class="sxs-lookup"><span data-stu-id="e50bf-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="e50bf-111">這表示 `Protected` 元素的宣告內容必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。</span><span class="sxs-lookup"><span data-stu-id="e50bf-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="e50bf-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e50bf-112">See also</span></span>

- [<span data-ttu-id="e50bf-113">Public</span><span class="sxs-lookup"><span data-stu-id="e50bf-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="e50bf-114">Protected</span><span class="sxs-lookup"><span data-stu-id="e50bf-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="e50bf-115">Friend</span><span class="sxs-lookup"><span data-stu-id="e50bf-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="e50bf-116">Private</span><span class="sxs-lookup"><span data-stu-id="e50bf-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="e50bf-117">Private Protected</span><span class="sxs-lookup"><span data-stu-id="e50bf-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="e50bf-118">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="e50bf-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="e50bf-119">程序</span><span class="sxs-lookup"><span data-stu-id="e50bf-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="e50bf-120">結構</span><span class="sxs-lookup"><span data-stu-id="e50bf-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="e50bf-121">物件和類別</span><span class="sxs-lookup"><span data-stu-id="e50bf-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
