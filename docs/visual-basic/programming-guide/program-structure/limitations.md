---
title: Visual Basic 的限制
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 10f67c02d25ec275d1c3e98197d51c25aa250c19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955502"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="1a08e-102">Visual Basic 的限制</span><span class="sxs-lookup"><span data-stu-id="1a08e-102">Visual Basic Limitations</span></span>
<span data-ttu-id="1a08e-103">舊版的 Visual Basic 會強制執行中程式碼，例如變數名稱，變數中的模組，以及模組大小所允許的數目的長度的界限。</span><span class="sxs-lookup"><span data-stu-id="1a08e-103">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="1a08e-104">在 Visual Basic.NET 中，這些限制已經被放寬，讓您更充分的自由撰寫及排列您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a08e-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="1a08e-105">實體的限制會更依賴於執行階段的記憶體，比在編譯時期的考量。</span><span class="sxs-lookup"><span data-stu-id="1a08e-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="1a08e-106">如果您使用容錯度加倍的程式設計作法，並分成多個類別和模組中的大型應用程式時，就很少機會遇到內部的 Visual Basic 限制。</span><span class="sxs-lookup"><span data-stu-id="1a08e-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="1a08e-107">以下是在極端情況下可能會遇到一些限制：</span><span class="sxs-lookup"><span data-stu-id="1a08e-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
- <span data-ttu-id="1a08e-108">**名稱長度。**</span><span class="sxs-lookup"><span data-stu-id="1a08e-108">**Name Length.**</span></span> <span data-ttu-id="1a08e-109">沒有最大的每個宣告的程式設計項目名稱的字元數。</span><span class="sxs-lookup"><span data-stu-id="1a08e-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="1a08e-110">如果為限定的項目名稱，這個最大值會套用到整個限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="1a08e-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="1a08e-111">請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="1a08e-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
- <span data-ttu-id="1a08e-112">**行長度。**</span><span class="sxs-lookup"><span data-stu-id="1a08e-112">**Line Length.**</span></span> <span data-ttu-id="1a08e-113">沒有實體的來源程式碼行中的 65535 個字元的最大值。</span><span class="sxs-lookup"><span data-stu-id="1a08e-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="1a08e-114">如果您使用行接續字元的長度時，能邏輯的原始程式碼行。</span><span class="sxs-lookup"><span data-stu-id="1a08e-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="1a08e-115">請參閱[如何：中斷和合併程式碼中的陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="1a08e-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
- <span data-ttu-id="1a08e-116">**陣列維度。**</span><span class="sxs-lookup"><span data-stu-id="1a08e-116">**Array Dimensions.**</span></span> <span data-ttu-id="1a08e-117">沒有您可以宣告為陣列的維度數目上限。</span><span class="sxs-lookup"><span data-stu-id="1a08e-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="1a08e-118">這會限制您可以使用指定的陣列元素的幾個索引。</span><span class="sxs-lookup"><span data-stu-id="1a08e-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="1a08e-119">請參閱[Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="1a08e-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
- <span data-ttu-id="1a08e-120">**字串長度。**</span><span class="sxs-lookup"><span data-stu-id="1a08e-120">**String Length.**</span></span> <span data-ttu-id="1a08e-121">沒有您可以儲存在單一字串的 Unicode 字元的數目上限。</span><span class="sxs-lookup"><span data-stu-id="1a08e-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="1a08e-122">請參閱[字串資料類型](../../../visual-basic/language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="1a08e-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
- <span data-ttu-id="1a08e-123">**環境字串長度。**</span><span class="sxs-lookup"><span data-stu-id="1a08e-123">**Environment String Length.**</span></span> <span data-ttu-id="1a08e-124">沒有任何做為命令列引數的環境字串 32768 個字元的最大值。</span><span class="sxs-lookup"><span data-stu-id="1a08e-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="1a08e-125">這是在所有平台上的限制。</span><span class="sxs-lookup"><span data-stu-id="1a08e-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a08e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a08e-126">See also</span></span>

- [<span data-ttu-id="1a08e-127">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="1a08e-127">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="1a08e-128">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="1a08e-128">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
