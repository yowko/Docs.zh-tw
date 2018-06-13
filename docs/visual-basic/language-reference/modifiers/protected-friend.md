---
title: Protected 的 Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/18/2018
ms.locfileid: "34306537"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="77bd1-102">Protected 的 Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77bd1-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="77bd1-103">`Protected Friend`關鍵字的組合都是成員的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="77bd1-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="77bd1-104">它會同時授與[Friend](friend.md)存取和[保護](protected.md)上宣告的項目，這樣就可從相同組件，從其自己的類別和衍生類別中的任何位置存取的存取。</span><span class="sxs-lookup"><span data-stu-id="77bd1-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="77bd1-105">您可以指定`Protected Friend`只成員上的類別; 無法套用`Protected Friend`結構的成員因為結構無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="77bd1-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="77bd1-106">在 Visual Studio 中，選取 F1 說明上`protected friend`提供任何說明[保護](protected.md)或[friend](friend.md)。</span><span class="sxs-lookup"><span data-stu-id="77bd1-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="77bd1-107">IDE 會挑選單一語彙基元，在資料指標，而不是複合字。</span><span class="sxs-lookup"><span data-stu-id="77bd1-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="77bd1-108">規則</span><span class="sxs-lookup"><span data-stu-id="77bd1-108">Rules</span></span>

- <span data-ttu-id="77bd1-109">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="77bd1-109">**Declaration Context.**</span></span> <span data-ttu-id="77bd1-110">您可以使用`Protected Friend`只能在類別層級。</span><span class="sxs-lookup"><span data-stu-id="77bd1-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="77bd1-111">這表示宣告內容`Protected`項目必須是類別，且不能原始程式檔、 命名空間、 介面、 模組、 結構或程序。</span><span class="sxs-lookup"><span data-stu-id="77bd1-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 


## <a name="see-also"></a><span data-ttu-id="77bd1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77bd1-112">See Also</span></span>

[<span data-ttu-id="77bd1-113">Public</span><span class="sxs-lookup"><span data-stu-id="77bd1-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="77bd1-114">Protected</span><span class="sxs-lookup"><span data-stu-id="77bd1-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="77bd1-115">[Friend](friend.md) </span><span class="sxs-lookup"><span data-stu-id="77bd1-115">[Friend](friend.md) </span></span>  
[<span data-ttu-id="77bd1-116">Private</span><span class="sxs-lookup"><span data-stu-id="77bd1-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="77bd1-117">[受保護的私用](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="77bd1-117">[Private Protected](./private-protected.md) </span></span>  
[<span data-ttu-id="77bd1-118">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="77bd1-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="77bd1-119">程序</span><span class="sxs-lookup"><span data-stu-id="77bd1-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="77bd1-120">結構</span><span class="sxs-lookup"><span data-stu-id="77bd1-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="77bd1-121">物件和類別</span><span class="sxs-lookup"><span data-stu-id="77bd1-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
