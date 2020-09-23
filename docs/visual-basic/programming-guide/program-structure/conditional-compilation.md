---
title: 條件式編譯
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: e59296882edc018259816c73b6ae861b3b296783
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098965"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="4f426-102">Visual Basic 中的條件式編譯</span><span class="sxs-lookup"><span data-stu-id="4f426-102">Conditional Compilation in Visual Basic</span></span>

<span data-ttu-id="4f426-103">在 *條件式編譯*中，程式中的特定程式碼區塊會選擇性地編譯，而其他區塊則會被忽略。</span><span class="sxs-lookup"><span data-stu-id="4f426-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="4f426-104">例如，您可能想要撰寫偵錯工具來比較不同方法與相同程式設計工作的速度，或您可能想要將多個語言的應用程式當地語系化。</span><span class="sxs-lookup"><span data-stu-id="4f426-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="4f426-105">條件式編譯語句是設計成在編譯期間執行，而不是在執行時間執行。</span><span class="sxs-lookup"><span data-stu-id="4f426-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="4f426-106">您可以使用指示詞來表示要有條件地編譯的程式碼區塊 `#If...Then...#Else` 。</span><span class="sxs-lookup"><span data-stu-id="4f426-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="4f426-107">例如，若要從相同的原始程式碼建立相同應用程式的法文和德文語言版本，您可以 `#If...Then` 使用預先定義的常數和，在語句中內嵌平臺特定的程式碼區段 `FrenchVersion` `GermanVersion` 。</span><span class="sxs-lookup"><span data-stu-id="4f426-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="4f426-108">下列範例示範如何：</span><span class="sxs-lookup"><span data-stu-id="4f426-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="4f426-109">如果您在 `FrenchVersion` 編譯時期將條件式編譯常數的值設定為 `True` ，則會編譯法文版本的條件式程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f426-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="4f426-110">如果您將常數的值設定 `GermanVersion` 為 `True` ，則編譯器會使用德文版。</span><span class="sxs-lookup"><span data-stu-id="4f426-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="4f426-111">如果兩個都未設定為，則會 `True` 執行最後一個區塊中的程式碼 `Else` 。</span><span class="sxs-lookup"><span data-stu-id="4f426-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f426-112">如果程式碼不是最新分支的一部分，則在編輯程式碼和使用條件式編譯指示詞時，自動完成功能將無法運作。</span><span class="sxs-lookup"><span data-stu-id="4f426-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="4f426-113">宣告條件式編譯常數</span><span class="sxs-lookup"><span data-stu-id="4f426-113">Declaring Conditional Compilation Constants</span></span>  

 <span data-ttu-id="4f426-114">您可以透過下列三種方式之一來設定條件式編譯常數：</span><span class="sxs-lookup"><span data-stu-id="4f426-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="4f426-115">在**專案設計**工具中</span><span class="sxs-lookup"><span data-stu-id="4f426-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="4f426-116">使用命令列編譯器時的命令列</span><span class="sxs-lookup"><span data-stu-id="4f426-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="4f426-117">在您的程式碼中</span><span class="sxs-lookup"><span data-stu-id="4f426-117">In your code</span></span>  
  
 <span data-ttu-id="4f426-118">條件式編譯常數具有特殊範圍，無法從標準程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="4f426-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="4f426-119">條件式編譯常數的範圍取決於其設定方式。</span><span class="sxs-lookup"><span data-stu-id="4f426-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="4f426-120">下表列出使用上述三種方法宣告的常數範圍。</span><span class="sxs-lookup"><span data-stu-id="4f426-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="4f426-121">常數的設定方式</span><span class="sxs-lookup"><span data-stu-id="4f426-121">How constant is set</span></span>|<span data-ttu-id="4f426-122">常數的範圍</span><span class="sxs-lookup"><span data-stu-id="4f426-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="4f426-123">**專案設計工具**</span><span class="sxs-lookup"><span data-stu-id="4f426-123">**Project Designer**</span></span>|<span data-ttu-id="4f426-124">公用至專案中的所有檔案</span><span class="sxs-lookup"><span data-stu-id="4f426-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="4f426-125">命令列</span><span class="sxs-lookup"><span data-stu-id="4f426-125">Command line</span></span>|<span data-ttu-id="4f426-126">公用至傳遞至命令列編譯器的所有檔案</span><span class="sxs-lookup"><span data-stu-id="4f426-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="4f426-127">`#Const` 程式碼中的語句</span><span class="sxs-lookup"><span data-stu-id="4f426-127">`#Const` statement in code</span></span>|<span data-ttu-id="4f426-128">私用至其宣告所在的檔案</span><span class="sxs-lookup"><span data-stu-id="4f426-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="4f426-129">在專案設計工具中設定常數</span><span class="sxs-lookup"><span data-stu-id="4f426-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="4f426-130">-在建立可執行檔之前，請遵循[管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)中提供的步驟，在**專案設計**工具中設定常數。</span><span class="sxs-lookup"><span data-stu-id="4f426-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="4f426-131">若要在命令列設定常數</span><span class="sxs-lookup"><span data-stu-id="4f426-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="4f426-132">-使用 **-d** 參數來輸入條件式編譯常數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4f426-132">-   Use the **-d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="4f426-133">**-D**參數和第一個常數之間不需要空格。</span><span class="sxs-lookup"><span data-stu-id="4f426-133">No space is required between the **-d** switch and the first constant.</span></span> <span data-ttu-id="4f426-134">如需詳細資訊，請參閱 [-定義 (Visual Basic) ](../../reference/command-line-compiler/define.md)。</span><span class="sxs-lookup"><span data-stu-id="4f426-134">For more information, see [-define (Visual Basic)](../../reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="4f426-135">命令列宣告會覆寫在 [ **專案設計**工具] 中輸入的宣告，但不會將它們清除。</span><span class="sxs-lookup"><span data-stu-id="4f426-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="4f426-136">在 [ **專案設計** 工具] 中設定的引數在後續的編譯中仍有效。</span><span class="sxs-lookup"><span data-stu-id="4f426-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="4f426-137">撰寫程式碼本身的常數時，不會有嚴格的規則來放置它們，因為其範圍是宣告它們的整個模組。</span><span class="sxs-lookup"><span data-stu-id="4f426-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="4f426-138">若要在您的程式碼中設定常數</span><span class="sxs-lookup"><span data-stu-id="4f426-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="4f426-139">-將常數放在其所使用之模組的宣告區塊中。</span><span class="sxs-lookup"><span data-stu-id="4f426-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="4f426-140">這有助於讓您的程式碼井然有序且更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="4f426-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="4f426-141">[相關主題]</span><span class="sxs-lookup"><span data-stu-id="4f426-141">Related Topics</span></span>  
  
|<span data-ttu-id="4f426-142">Title</span><span class="sxs-lookup"><span data-stu-id="4f426-142">Title</span></span>|<span data-ttu-id="4f426-143">描述</span><span class="sxs-lookup"><span data-stu-id="4f426-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="4f426-144">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="4f426-144">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)|<span data-ttu-id="4f426-145">提供讓您的程式碼更容易讀取和維護的建議。</span><span class="sxs-lookup"><span data-stu-id="4f426-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="4f426-146">參考</span><span class="sxs-lookup"><span data-stu-id="4f426-146">Reference</span></span>  

 [<span data-ttu-id="4f426-147">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="4f426-147">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="4f426-148">#If .。。Then ... #Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="4f426-148">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="4f426-149">-定義 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="4f426-149">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
