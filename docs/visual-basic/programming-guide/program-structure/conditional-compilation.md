---
title: Visual Basic 中的條件式編譯
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 828edf2e5491394f5ac802b5c9babfb3df359e59
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967843"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="0fa31-102">Visual Basic 中的條件式編譯</span><span class="sxs-lookup"><span data-stu-id="0fa31-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="0fa31-103">在 *條件式編譯*，而忽略其他特定的程式中的程式碼區塊會選擇性地編譯。</span><span class="sxs-lookup"><span data-stu-id="0fa31-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="0fa31-104">例如，您可能想要撰寫偵錯陳述式，比較不同的方法相同的程式設計工作，或您的速度可能會想要將應用程式在多國語言的當地語系化。</span><span class="sxs-lookup"><span data-stu-id="0fa31-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="0fa31-105">條件式編譯陳述式被設計為在編譯期間，不是在執行階段執行。</span><span class="sxs-lookup"><span data-stu-id="0fa31-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="0fa31-106">表示有條件地編譯的程式碼區塊`#If...Then...#Else`指示詞。</span><span class="sxs-lookup"><span data-stu-id="0fa31-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="0fa31-107">比方說，若要建立法文及德文語言版本相同的應用程式，從相同來源的程式碼，您將內嵌平台特定程式碼區段中的`#If...Then`陳述式使用預先定義的常數`FrenchVersion`和`GermanVersion`。</span><span class="sxs-lookup"><span data-stu-id="0fa31-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="0fa31-108">下列範例示範如何：</span><span class="sxs-lookup"><span data-stu-id="0fa31-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="0fa31-109">如果您設定的值`FrenchVersion`條件式編譯常數，以`True`在編譯時期，法文版的條件式程式碼會編譯。</span><span class="sxs-lookup"><span data-stu-id="0fa31-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="0fa31-110">如果您設定的值`GermanVersion`常數`True`，編譯器會使用德文版。</span><span class="sxs-lookup"><span data-stu-id="0fa31-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="0fa31-111">如果沒有設定任何`True`，在過去的程式碼`Else`封鎖執行。</span><span class="sxs-lookup"><span data-stu-id="0fa31-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fa31-112">Not 函式時編輯程式碼，並使用條件式編譯指示詞，如果程式碼不是最新分支的一部分，將會自動完成。</span><span class="sxs-lookup"><span data-stu-id="0fa31-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="0fa31-113">宣告條件式編譯常數</span><span class="sxs-lookup"><span data-stu-id="0fa31-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="0fa31-114">您可以使用三種方式之一來設定條件式編譯常數：</span><span class="sxs-lookup"><span data-stu-id="0fa31-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
-   <span data-ttu-id="0fa31-115">在 **專案設計工具**</span><span class="sxs-lookup"><span data-stu-id="0fa31-115">In the **Project Designer**</span></span>  
  
-   <span data-ttu-id="0fa31-116">在命令列使用命令列編譯器時</span><span class="sxs-lookup"><span data-stu-id="0fa31-116">At the command line when using the command-line compiler</span></span>  
  
-   <span data-ttu-id="0fa31-117">在您的程式碼</span><span class="sxs-lookup"><span data-stu-id="0fa31-117">In your code</span></span>  
  
 <span data-ttu-id="0fa31-118">條件式編譯常數有特殊的範圍，並不能從標準的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="0fa31-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="0fa31-119">條件式編譯常數的範圍是取決於它的設定方式。</span><span class="sxs-lookup"><span data-stu-id="0fa31-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="0fa31-120">下表列出使用每個先前所述的三種方式宣告的常數的範圍。</span><span class="sxs-lookup"><span data-stu-id="0fa31-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="0fa31-121">如何設定常數</span><span class="sxs-lookup"><span data-stu-id="0fa31-121">How constant is set</span></span>|<span data-ttu-id="0fa31-122">常數的範圍</span><span class="sxs-lookup"><span data-stu-id="0fa31-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="0fa31-123">**專案設計工具**</span><span class="sxs-lookup"><span data-stu-id="0fa31-123">**Project Designer**</span></span>|<span data-ttu-id="0fa31-124">公用專案中的所有檔案</span><span class="sxs-lookup"><span data-stu-id="0fa31-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="0fa31-125">命令列</span><span class="sxs-lookup"><span data-stu-id="0fa31-125">Command line</span></span>|<span data-ttu-id="0fa31-126">公開的所有檔案傳遞至命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="0fa31-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="0fa31-127">`#Const` 在程式碼中的陳述式</span><span class="sxs-lookup"><span data-stu-id="0fa31-127">`#Const` statement in code</span></span>|<span data-ttu-id="0fa31-128">私人雲端擴充到宣告它的檔案</span><span class="sxs-lookup"><span data-stu-id="0fa31-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="0fa31-129">若要設定 專案設計工具中的常數</span><span class="sxs-lookup"><span data-stu-id="0fa31-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="0fa31-130">之前建立可執行檔，請在中設定常數**專案設計工具**依照所提供的步驟[管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)。</span><span class="sxs-lookup"><span data-stu-id="0fa31-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="0fa31-131">若要在命令列設定常數</span><span class="sxs-lookup"><span data-stu-id="0fa31-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="0fa31-132">-使用 **/d**切換到輸入條件式編譯常數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0fa31-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="0fa31-133">不不需要之間任何空間 **/d**交換器與第一個常數。</span><span class="sxs-lookup"><span data-stu-id="0fa31-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="0fa31-134">如需詳細資訊，請參閱 < [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)。</span><span class="sxs-lookup"><span data-stu-id="0fa31-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="0fa31-135">命令列宣告覆寫輸入中的宣告**專案設計工具**，但不是會將它們清除。</span><span class="sxs-lookup"><span data-stu-id="0fa31-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="0fa31-136">在 設定引數**專案設計工具**對後續編譯仍然有效。</span><span class="sxs-lookup"><span data-stu-id="0fa31-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="0fa31-137">當撰寫程式碼本身中的常數，沒有嚴格的規則，對於其放置的功能，因為它們的範圍是整個模組在宣告。</span><span class="sxs-lookup"><span data-stu-id="0fa31-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="0fa31-138">若要設定您的程式碼中的常數</span><span class="sxs-lookup"><span data-stu-id="0fa31-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="0fa31-139">-將放在其中使用的模組宣告區塊中的常數。</span><span class="sxs-lookup"><span data-stu-id="0fa31-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="0fa31-140">如此一來，可協助組織更容易閱讀，確保您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0fa31-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="0fa31-141">相關主題</span><span class="sxs-lookup"><span data-stu-id="0fa31-141">Related Topics</span></span>  
  
|<span data-ttu-id="0fa31-142">標題</span><span class="sxs-lookup"><span data-stu-id="0fa31-142">Title</span></span>|<span data-ttu-id="0fa31-143">描述</span><span class="sxs-lookup"><span data-stu-id="0fa31-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="0fa31-144">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="0fa31-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="0fa31-145">提供讓您輕鬆地閱讀和維護的程式碼的建議。</span><span class="sxs-lookup"><span data-stu-id="0fa31-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="0fa31-146">參考資料</span><span class="sxs-lookup"><span data-stu-id="0fa31-146">Reference</span></span>  
 [<span data-ttu-id="0fa31-147">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="0fa31-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="0fa31-148">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="0fa31-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="0fa31-149">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fa31-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
