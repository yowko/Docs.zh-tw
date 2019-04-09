---
title: 受保護的 Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 331c63dc290d4096e8158f265ee869b47743a273
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151771"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="4d0a2-102">受保護的 Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d0a2-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="4d0a2-103">`Protected Friend` 關鍵字組合是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="4d0a2-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="4d0a2-104">它會授與這兩[Friend](friend.md)存取並[受保護](protected.md)上宣告的項目，使其可從相同的組件，從他們自己的類別，以及從衍生類別中的任何位置存取的存取。</span><span class="sxs-lookup"><span data-stu-id="4d0a2-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="4d0a2-105">您可以指定`Protected Friend`只能在類別; 的成員上不能套用`Protected Friend`的結構成員因為結構無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="4d0a2-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="4d0a2-106">在 Visual Studio 中，選取 上的 F1 說明`protected friend`提供的其中一個 說明[保護](protected.md)或是[friend](friend.md)。</span><span class="sxs-lookup"><span data-stu-id="4d0a2-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="4d0a2-107">IDE 會挑選單一語彙基元，在資料指標，而不是複合字。</span><span class="sxs-lookup"><span data-stu-id="4d0a2-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="4d0a2-108">規則</span><span class="sxs-lookup"><span data-stu-id="4d0a2-108">Rules</span></span>

- **<span data-ttu-id="4d0a2-109">宣告內容。</span><span class="sxs-lookup"><span data-stu-id="4d0a2-109">Declaration Context.</span></span>** <span data-ttu-id="4d0a2-110">您可以使用`Protected Friend`只能在類別層級。</span><span class="sxs-lookup"><span data-stu-id="4d0a2-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="4d0a2-111">這表示的宣告內容`Protected`項目必須是類別，，而且不能是原始程式檔、 命名空間、 介面、 模組、 結構或程序。</span><span class="sxs-lookup"><span data-stu-id="4d0a2-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 

## <a name="see-also"></a><span data-ttu-id="4d0a2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d0a2-112">See also</span></span>

- [<span data-ttu-id="4d0a2-113">Public</span><span class="sxs-lookup"><span data-stu-id="4d0a2-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="4d0a2-114">Protected</span><span class="sxs-lookup"><span data-stu-id="4d0a2-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="4d0a2-115">Friend</span><span class="sxs-lookup"><span data-stu-id="4d0a2-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="4d0a2-116">Private</span><span class="sxs-lookup"><span data-stu-id="4d0a2-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="4d0a2-117">受保護的私用</span><span class="sxs-lookup"><span data-stu-id="4d0a2-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="4d0a2-118">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="4d0a2-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="4d0a2-119">程序</span><span class="sxs-lookup"><span data-stu-id="4d0a2-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="4d0a2-120">結構</span><span class="sxs-lookup"><span data-stu-id="4d0a2-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="4d0a2-121">物件和類別</span><span class="sxs-lookup"><span data-stu-id="4d0a2-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
