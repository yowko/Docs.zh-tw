---
title: "Visual Basic 中的條件式編譯"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 559380dc9baceb2fba4dca782e83f335f1bcd92d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="16c2c-102">Visual Basic 中的條件式編譯</span><span class="sxs-lookup"><span data-stu-id="16c2c-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="16c2c-103">在*條件式編譯*，而忽略其他的特定程式中的程式碼區塊會選擇性地編譯。</span><span class="sxs-lookup"><span data-stu-id="16c2c-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="16c2c-104">例如，您可能想要撰寫偵錯陳述式比較不同的方法相同的程式設計工作，或您的速度可能會想要當地語系化為多種語言的應用程式。</span><span class="sxs-lookup"><span data-stu-id="16c2c-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="16c2c-105">條件式編譯陳述式被設計為在編譯時期，不在執行階段期間執行。</span><span class="sxs-lookup"><span data-stu-id="16c2c-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="16c2c-106">代表使用有條件地編譯的程式碼區塊`#If...Then...#Else`指示詞。</span><span class="sxs-lookup"><span data-stu-id="16c2c-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="16c2c-107">例如，若要建立法文及德文語言相同的應用程式，從相同的版本的原始程式碼，內嵌平台專屬的程式碼區段中`#If...Then`陳述式中使用預先定義的常數`FrenchVersion`和`GermanVersion`。</span><span class="sxs-lookup"><span data-stu-id="16c2c-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="16c2c-108">下列範例會示範如何：</span><span class="sxs-lookup"><span data-stu-id="16c2c-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 <span data-ttu-id="16c2c-109">如果您設定的值`FrenchVersion`條件式編譯常數`True`法文版的條件式程式碼會在編譯時期，編譯。</span><span class="sxs-lookup"><span data-stu-id="16c2c-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="16c2c-110">如果您設定的值`GermanVersion`常數`True`，編譯器會使用德文版。</span><span class="sxs-lookup"><span data-stu-id="16c2c-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="16c2c-111">如果皆未設定`True`，過去的程式碼`Else`封鎖執行。</span><span class="sxs-lookup"><span data-stu-id="16c2c-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16c2c-112">Not 函式時編輯程式碼，並使用條件式編譯指示詞，如果程式碼不是最新分支的一部分，將會自動完成。</span><span class="sxs-lookup"><span data-stu-id="16c2c-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="16c2c-113">宣告條件式編譯常數</span><span class="sxs-lookup"><span data-stu-id="16c2c-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="16c2c-114">您可以使用三種方式之一來設定條件式編譯常數：</span><span class="sxs-lookup"><span data-stu-id="16c2c-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
-   <span data-ttu-id="16c2c-115">在**專案設計工具**</span><span class="sxs-lookup"><span data-stu-id="16c2c-115">In the **Project Designer**</span></span>  
  
-   <span data-ttu-id="16c2c-116">在命令列時使用命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="16c2c-116">At the command line when using the command-line compiler</span></span>  
  
-   <span data-ttu-id="16c2c-117">在您的程式碼</span><span class="sxs-lookup"><span data-stu-id="16c2c-117">In your code</span></span>  
  
 <span data-ttu-id="16c2c-118">條件式編譯常數有特殊的範圍，且無法從標準的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="16c2c-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="16c2c-119">條件式編譯常數的範圍會相依於它的設定方式。</span><span class="sxs-lookup"><span data-stu-id="16c2c-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="16c2c-120">下表列出常數宣告使用上述的三種方式的每個的範圍。</span><span class="sxs-lookup"><span data-stu-id="16c2c-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="16c2c-121">如何設定常數</span><span class="sxs-lookup"><span data-stu-id="16c2c-121">How constant is set</span></span>|<span data-ttu-id="16c2c-122">常數的範圍</span><span class="sxs-lookup"><span data-stu-id="16c2c-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="16c2c-123">**專案設計工具**</span><span class="sxs-lookup"><span data-stu-id="16c2c-123">**Project Designer**</span></span>|<span data-ttu-id="16c2c-124">在專案中的所有檔案公開</span><span class="sxs-lookup"><span data-stu-id="16c2c-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="16c2c-125">命令列</span><span class="sxs-lookup"><span data-stu-id="16c2c-125">Command line</span></span>|<span data-ttu-id="16c2c-126">所有檔案公開傳遞至命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="16c2c-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="16c2c-127">`#Const`在程式碼中的陳述式</span><span class="sxs-lookup"><span data-stu-id="16c2c-127">`#Const` statement in code</span></span>|<span data-ttu-id="16c2c-128">私用宣告它的檔案</span><span class="sxs-lookup"><span data-stu-id="16c2c-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="16c2c-129">若要設定專案設計工具中的常數</span><span class="sxs-lookup"><span data-stu-id="16c2c-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="16c2c-130">-建立之前可執行檔，在中設定常數**專案設計工具**遵循中提供的步驟[管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)。</span><span class="sxs-lookup"><span data-stu-id="16c2c-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="16c2c-131">若要在命令列設定常數</span><span class="sxs-lookup"><span data-stu-id="16c2c-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="16c2c-132">-使用**/d**切換到輸入條件式編譯常數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="16c2c-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="16c2c-133">不不需要之間任何空間**/d**交換器與第一個常數。</span><span class="sxs-lookup"><span data-stu-id="16c2c-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="16c2c-134">如需詳細資訊，請參閱[/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)。</span><span class="sxs-lookup"><span data-stu-id="16c2c-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="16c2c-135">命令列宣告覆寫中輸入宣告**專案設計工具**，但不是會清除它們。</span><span class="sxs-lookup"><span data-stu-id="16c2c-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="16c2c-136">設定的引數**專案設計工具**對後續編譯仍然有效。</span><span class="sxs-lookup"><span data-stu-id="16c2c-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="16c2c-137">常數寫入時在程式碼本身，沒有嚴格規則對於它們的位置，因為其範圍是整個模組宣告它們。</span><span class="sxs-lookup"><span data-stu-id="16c2c-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="16c2c-138">若要在程式碼中設定常數</span><span class="sxs-lookup"><span data-stu-id="16c2c-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="16c2c-139">-將宣告區塊中使用的模組中的常數。</span><span class="sxs-lookup"><span data-stu-id="16c2c-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="16c2c-140">這可協助組織更容易閱讀，保持您程式碼。</span><span class="sxs-lookup"><span data-stu-id="16c2c-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="16c2c-141">相關主題</span><span class="sxs-lookup"><span data-stu-id="16c2c-141">Related Topics</span></span>  
  
|<span data-ttu-id="16c2c-142">標題</span><span class="sxs-lookup"><span data-stu-id="16c2c-142">Title</span></span>|<span data-ttu-id="16c2c-143">說明</span><span class="sxs-lookup"><span data-stu-id="16c2c-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="16c2c-144">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="16c2c-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="16c2c-145">提供讓您輕鬆地閱讀和維護的程式碼的建議。</span><span class="sxs-lookup"><span data-stu-id="16c2c-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="16c2c-146">參考資料</span><span class="sxs-lookup"><span data-stu-id="16c2c-146">Reference</span></span>  
 [<span data-ttu-id="16c2c-147">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="16c2c-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="16c2c-148">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="16c2c-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="16c2c-149">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16c2c-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
