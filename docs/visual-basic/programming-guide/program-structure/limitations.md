---
title: 限制
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: f7e19977a011565bb4b1536af5cab195f8a01017
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347360"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="665fe-102">Visual Basic 的限制</span><span class="sxs-lookup"><span data-stu-id="665fe-102">Visual Basic Limitations</span></span>
<span data-ttu-id="665fe-103">舊版 Visual Basic 在程式碼中強制執行界限，例如變數名稱的長度、模組中允許的變數數目，以及模組大小。</span><span class="sxs-lookup"><span data-stu-id="665fe-103">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="665fe-104">在 Visual Basic .NET 中，這些限制已經過寬鬆，讓您更能自由地撰寫和排列程式碼。</span><span class="sxs-lookup"><span data-stu-id="665fe-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="665fe-105">實體限制相依于執行時間記憶體，而不是編譯時期考慮。</span><span class="sxs-lookup"><span data-stu-id="665fe-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="665fe-106">如果您使用謹慎的程式設計實務，並將大型應用程式分割成多個類別和模組，那麼就沒有機會遇到內部 Visual Basic 限制。</span><span class="sxs-lookup"><span data-stu-id="665fe-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="665fe-107">以下是您在極端情況下可能會遇到的一些限制：</span><span class="sxs-lookup"><span data-stu-id="665fe-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
- <span data-ttu-id="665fe-108">**名稱長度。**</span><span class="sxs-lookup"><span data-stu-id="665fe-108">**Name Length.**</span></span> <span data-ttu-id="665fe-109">每個宣告的程式設計項目的名稱都有最大的字元數。</span><span class="sxs-lookup"><span data-stu-id="665fe-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="665fe-110">如果專案名稱是限定的，此最大值會套用至整個限定性字串。</span><span class="sxs-lookup"><span data-stu-id="665fe-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="665fe-111">請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="665fe-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
- <span data-ttu-id="665fe-112">**行長度。**</span><span class="sxs-lookup"><span data-stu-id="665fe-112">**Line Length.**</span></span> <span data-ttu-id="665fe-113">在原始碼的實體行中，最多可有65535個字元。</span><span class="sxs-lookup"><span data-stu-id="665fe-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="665fe-114">如果您使用行接續字元，則邏輯源程式碼可能會較長。</span><span class="sxs-lookup"><span data-stu-id="665fe-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="665fe-115">請參閱[如何：在程式碼中中斷和合併語句](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="665fe-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
- <span data-ttu-id="665fe-116">**陣列維度。**</span><span class="sxs-lookup"><span data-stu-id="665fe-116">**Array Dimensions.**</span></span> <span data-ttu-id="665fe-117">您可以為陣列宣告的維度數目上限為。</span><span class="sxs-lookup"><span data-stu-id="665fe-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="665fe-118">這會限制您可以用來指定陣列元素的索引數目。</span><span class="sxs-lookup"><span data-stu-id="665fe-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="665fe-119">請參閱[Visual Basic 中的陣列維度](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="665fe-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
- <span data-ttu-id="665fe-120">**字串長度。**</span><span class="sxs-lookup"><span data-stu-id="665fe-120">**String Length.**</span></span> <span data-ttu-id="665fe-121">您可以在單一字串中儲存的 Unicode 字元數目上限。</span><span class="sxs-lookup"><span data-stu-id="665fe-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="665fe-122">請參閱[String 資料類型](../../../visual-basic/language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="665fe-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
- <span data-ttu-id="665fe-123">**環境字串長度。**</span><span class="sxs-lookup"><span data-stu-id="665fe-123">**Environment String Length.**</span></span> <span data-ttu-id="665fe-124">做為命令列引數使用的任何環境字串，最多可有32768個字元。</span><span class="sxs-lookup"><span data-stu-id="665fe-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="665fe-125">這是所有平臺的限制。</span><span class="sxs-lookup"><span data-stu-id="665fe-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="665fe-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="665fe-126">See also</span></span>

- [<span data-ttu-id="665fe-127">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="665fe-127">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="665fe-128">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="665fe-128">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
