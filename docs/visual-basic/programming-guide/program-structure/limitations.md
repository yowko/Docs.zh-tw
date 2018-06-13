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
ms.openlocfilehash: 57378c3aa18a5cc108c10e8654e55803f3cf9052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649925"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="74394-102">Visual Basic 的限制</span><span class="sxs-lookup"><span data-stu-id="74394-102">Visual Basic Limitations</span></span>
<span data-ttu-id="74394-103">舊版的 Visual Basic 會強制界限的程式碼，例如變數名稱的模組和模組大小中允許的變數數目的長度。</span><span class="sxs-lookup"><span data-stu-id="74394-103">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="74394-104">在 Visual Basic.NET 中，這些限制有已經放寬，讓您更自由撰寫及排列您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="74394-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="74394-105">實體限制會更依賴於執行階段的記憶體比編譯時期的考量。</span><span class="sxs-lookup"><span data-stu-id="74394-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="74394-106">如果您使用審慎的程式設計作法，並將大型應用程式分割成多個類別和模組時，就很少機會遇到內部的 Visual Basic 限制。</span><span class="sxs-lookup"><span data-stu-id="74394-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="74394-107">在極端情況下可能會遇到一些限制如下：</span><span class="sxs-lookup"><span data-stu-id="74394-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="74394-108">**名稱長度。**</span><span class="sxs-lookup"><span data-stu-id="74394-108">**Name Length.**</span></span> <span data-ttu-id="74394-109">沒有最大的每個宣告的程式設計項目名稱的字元數。</span><span class="sxs-lookup"><span data-stu-id="74394-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="74394-110">如果限定的項目名稱，這個最大值會套用到整個限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="74394-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="74394-111">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="74394-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="74394-112">**行長度。**</span><span class="sxs-lookup"><span data-stu-id="74394-112">**Line Length.**</span></span> <span data-ttu-id="74394-113">沒有最多 65535 個字元的實體來源的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="74394-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="74394-114">一行程式碼邏輯來源可以是較長，如果您使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="74394-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="74394-115">請參閱[How to： 中斷和合併陳述式中的程式碼](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="74394-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="74394-116">**陣列維度。**</span><span class="sxs-lookup"><span data-stu-id="74394-116">**Array Dimensions.**</span></span> <span data-ttu-id="74394-117">沒有您可以宣告為陣列的維度數目上限。</span><span class="sxs-lookup"><span data-stu-id="74394-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="74394-118">這會限制多少索引可用來指定陣列項目。</span><span class="sxs-lookup"><span data-stu-id="74394-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="74394-119">請參閱[陣列 Visual Basic 中的維度](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="74394-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="74394-120">**字串長度。**</span><span class="sxs-lookup"><span data-stu-id="74394-120">**String Length.**</span></span> <span data-ttu-id="74394-121">沒有您可以儲存在單一字串中的 Unicode 字元的數目上限。</span><span class="sxs-lookup"><span data-stu-id="74394-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="74394-122">請參閱[字串資料型別](../../../visual-basic/language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="74394-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="74394-123">**環境字串長度。**</span><span class="sxs-lookup"><span data-stu-id="74394-123">**Environment String Length.**</span></span> <span data-ttu-id="74394-124">沒有 32768 字元做為命令列引數的任何環境字串的最大值。</span><span class="sxs-lookup"><span data-stu-id="74394-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="74394-125">這是在所有平台上的限制。</span><span class="sxs-lookup"><span data-stu-id="74394-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74394-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74394-126">See Also</span></span>  
 [<span data-ttu-id="74394-127">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="74394-127">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="74394-128">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="74394-128">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
