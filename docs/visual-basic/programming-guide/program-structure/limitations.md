---
title: "Visual Basic 的限制 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- limits
- limitations, Visual Basic
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a3bd551ade2f0c55cd943cfbd353b09dfede4063
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-limitations"></a><span data-ttu-id="f3b1e-102">Visual Basic 的限制</span><span class="sxs-lookup"><span data-stu-id="f3b1e-102">Visual Basic Limitations</span></span>
<span data-ttu-id="f3b1e-103">舊版的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]強制執行中程式碼，例如變數名稱的長度界限中的模組，以及模組大小所允許的變數數目。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-103">Earlier versions of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="f3b1e-104">在[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]，這些限制已經放寬，讓您撰寫及排列您的程式碼更自由。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-104">In [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="f3b1e-105">實體限制會更依賴於執行階段的記憶體比在編譯時期考量。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="f3b1e-106">如果您使用審慎的程式設計作法，並將大型應用程式分割成多個類別和模組，則很極少機會遇到內部[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]限制。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] limitation.</span></span>  
  
 <span data-ttu-id="f3b1e-107">以下是在極端情況下可能會遇到一些限制︰</span><span class="sxs-lookup"><span data-stu-id="f3b1e-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="f3b1e-108">**名稱長度。**</span><span class="sxs-lookup"><span data-stu-id="f3b1e-108">**Name Length.**</span></span> <span data-ttu-id="f3b1e-109">沒有最大的每個宣告的程式設計項目名稱的字元數。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="f3b1e-110">如果限定的項目名稱，這個最大值會套用到整個限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="f3b1e-111">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="f3b1e-112">**行的長度。**</span><span class="sxs-lookup"><span data-stu-id="f3b1e-112">**Line Length.**</span></span> <span data-ttu-id="f3b1e-113">則實體一行程式碼中的 65535 個字元的上限。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="f3b1e-114">邏輯來源一行程式碼會更長，如果您使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="f3b1e-115">請參閱[How to︰ 中斷和合併程式碼中的陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="f3b1e-116">**陣列維度。**</span><span class="sxs-lookup"><span data-stu-id="f3b1e-116">**Array Dimensions.**</span></span> <span data-ttu-id="f3b1e-117">沒有您可以宣告陣列維度的數目上限。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="f3b1e-118">這會限制多少可用來指定陣列元素的索引。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="f3b1e-119">請參閱[陣列 Visual Basic 中的維度](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="f3b1e-120">**字串長度。**</span><span class="sxs-lookup"><span data-stu-id="f3b1e-120">**String Length.**</span></span> <span data-ttu-id="f3b1e-121">沒有您可以儲存在單一字串中的 Unicode 字元的數目上限。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="f3b1e-122">請參閱[字串資料型別](../../../visual-basic/language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="f3b1e-123">**環境字串長度。**</span><span class="sxs-lookup"><span data-stu-id="f3b1e-123">**Environment String Length.**</span></span> <span data-ttu-id="f3b1e-124">沒有 32768 個字元的任何環境字串做為命令列引數的最大值。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="f3b1e-125">這是在所有平台上的限制。</span><span class="sxs-lookup"><span data-stu-id="f3b1e-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b1e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3b1e-126">See Also</span></span>  
 <span data-ttu-id="f3b1e-127">[程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="f3b1e-127">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="f3b1e-128"> [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)</span><span class="sxs-lookup"><span data-stu-id="f3b1e-128"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)</span></span>
