---
title: Visual Basic 中的條件式編譯
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 1bee64568ff92468e29226a395f7e5335387e256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945577"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="57fa2-102">Visual Basic 中的條件式編譯</span><span class="sxs-lookup"><span data-stu-id="57fa2-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="57fa2-103">在*條件式編譯*中, 程式中的特定程式碼區塊會選擇性地進行編譯, 而有些則會被忽略。</span><span class="sxs-lookup"><span data-stu-id="57fa2-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="57fa2-104">例如, 您可能會想要撰寫可比較不同方法與相同程式設計工作之速度的偵錯工具, 或者您可能想要將多個語言的應用程式當地語系化。</span><span class="sxs-lookup"><span data-stu-id="57fa2-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="57fa2-105">條件式編譯語句是設計用來在編譯時期執行, 而不是在執行時間執行。</span><span class="sxs-lookup"><span data-stu-id="57fa2-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="57fa2-106">您可以使用指示詞來表示要有`#If...Then...#Else`條件地編譯的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="57fa2-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="57fa2-107">例如, 若要從相同的原始程式碼建立相同應用程式的法文和德文版, 您可以使用預先定義的常數`#If...Then` `FrenchVersion`和`GermanVersion`, 在語句中內嵌平臺特定的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="57fa2-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="57fa2-108">下列範例示範如何:</span><span class="sxs-lookup"><span data-stu-id="57fa2-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="57fa2-109">如果您在編譯時期將`FrenchVersion`條件式編譯常數的值設為`True` , 則會編譯法文版本的條件式程式碼。</span><span class="sxs-lookup"><span data-stu-id="57fa2-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="57fa2-110">如果您將`GermanVersion`常數的值設為`True`, 則編譯器會使用德文版。</span><span class="sxs-lookup"><span data-stu-id="57fa2-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="57fa2-111">如果兩者都未設定`True`為, 則最後一個`Else`區塊中的程式碼會執行。</span><span class="sxs-lookup"><span data-stu-id="57fa2-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57fa2-112">如果程式碼不是最新分支的一部分, 則在編輯程式碼和使用條件式編譯指示詞時, 自動完成將無法運作。</span><span class="sxs-lookup"><span data-stu-id="57fa2-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="57fa2-113">宣告條件式編譯常數</span><span class="sxs-lookup"><span data-stu-id="57fa2-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="57fa2-114">您可以透過下列三種方式之一來設定條件式編譯常數:</span><span class="sxs-lookup"><span data-stu-id="57fa2-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="57fa2-115">在 [**專案設計**工具] 中</span><span class="sxs-lookup"><span data-stu-id="57fa2-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="57fa2-116">使用命令列編譯器時, 在命令列中</span><span class="sxs-lookup"><span data-stu-id="57fa2-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="57fa2-117">在您的程式碼中</span><span class="sxs-lookup"><span data-stu-id="57fa2-117">In your code</span></span>  
  
 <span data-ttu-id="57fa2-118">條件式編譯常數具有特殊範圍, 而且無法從標準程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="57fa2-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="57fa2-119">條件式編譯常數的範圍取決於其設定方式。</span><span class="sxs-lookup"><span data-stu-id="57fa2-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="57fa2-120">下表列出使用上述三種方式宣告的常數範圍。</span><span class="sxs-lookup"><span data-stu-id="57fa2-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="57fa2-121">如何設定常數</span><span class="sxs-lookup"><span data-stu-id="57fa2-121">How constant is set</span></span>|<span data-ttu-id="57fa2-122">常數的範圍</span><span class="sxs-lookup"><span data-stu-id="57fa2-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="57fa2-123">**專案設計工具**</span><span class="sxs-lookup"><span data-stu-id="57fa2-123">**Project Designer**</span></span>|<span data-ttu-id="57fa2-124">專案中所有檔案的公用</span><span class="sxs-lookup"><span data-stu-id="57fa2-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="57fa2-125">命令列</span><span class="sxs-lookup"><span data-stu-id="57fa2-125">Command line</span></span>|<span data-ttu-id="57fa2-126">所有傳遞至命令列編譯器的檔案都是公用的</span><span class="sxs-lookup"><span data-stu-id="57fa2-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="57fa2-127">`#Const`程式碼中的語句</span><span class="sxs-lookup"><span data-stu-id="57fa2-127">`#Const` statement in code</span></span>|<span data-ttu-id="57fa2-128">私用到其宣告所在的檔案</span><span class="sxs-lookup"><span data-stu-id="57fa2-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="57fa2-129">在專案設計工具中設定常數</span><span class="sxs-lookup"><span data-stu-id="57fa2-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="57fa2-130">-在建立可執行檔之前, 請遵循[管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)中提供的步驟, 在 [**專案設計**工具] 中設定常數。</span><span class="sxs-lookup"><span data-stu-id="57fa2-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="57fa2-131">若要在命令列設定常數</span><span class="sxs-lookup"><span data-stu-id="57fa2-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="57fa2-132">-使用 **/d**參數輸入條件式編譯常數, 如下列範例所示:</span><span class="sxs-lookup"><span data-stu-id="57fa2-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="57fa2-133">**/D**參數和第一個常數之間不需要有空格。</span><span class="sxs-lookup"><span data-stu-id="57fa2-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="57fa2-134">如需詳細資訊, 請參閱[/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)。</span><span class="sxs-lookup"><span data-stu-id="57fa2-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="57fa2-135">命令列宣告會覆寫在 [**專案設計**工具] 中輸入的宣告, 但不會將它們清除。</span><span class="sxs-lookup"><span data-stu-id="57fa2-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="57fa2-136">在 [**專案設計**工具] 中設定的引數會在後續的編譯中繼續生效。</span><span class="sxs-lookup"><span data-stu-id="57fa2-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="57fa2-137">在程式碼本身撰寫常數時, 並沒有任何嚴格的位置規則, 因為其範圍是宣告它們的整個模組。</span><span class="sxs-lookup"><span data-stu-id="57fa2-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="57fa2-138">若要在程式碼中設定常數</span><span class="sxs-lookup"><span data-stu-id="57fa2-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="57fa2-139">-將常數放在使用它們之模組的宣告區塊中。</span><span class="sxs-lookup"><span data-stu-id="57fa2-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="57fa2-140">這有助於讓您的程式碼井然有序且更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="57fa2-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="57fa2-141">相關主題</span><span class="sxs-lookup"><span data-stu-id="57fa2-141">Related Topics</span></span>  
  
|<span data-ttu-id="57fa2-142">標題</span><span class="sxs-lookup"><span data-stu-id="57fa2-142">Title</span></span>|<span data-ttu-id="57fa2-143">描述</span><span class="sxs-lookup"><span data-stu-id="57fa2-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="57fa2-144">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="57fa2-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="57fa2-145">提供讓您的程式碼易於閱讀和維護的建議。</span><span class="sxs-lookup"><span data-stu-id="57fa2-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="57fa2-146">參考資料</span><span class="sxs-lookup"><span data-stu-id="57fa2-146">Reference</span></span>  
 [<span data-ttu-id="57fa2-147">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="57fa2-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="57fa2-148">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="57fa2-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="57fa2-149">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57fa2-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
