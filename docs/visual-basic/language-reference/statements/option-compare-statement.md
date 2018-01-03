---
title: "Option Compare 陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 00753eddb641c07ef9c6e6282fe00c5e8d00547a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="option-compare-statement"></a><span data-ttu-id="1b01d-102">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="1b01d-102">Option Compare Statement</span></span>
<span data-ttu-id="1b01d-103">宣告比較字串資料時要使用的預設比較方法。</span><span class="sxs-lookup"><span data-stu-id="1b01d-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b01d-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b01d-104">Syntax</span></span>  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="1b01d-105">組件</span><span class="sxs-lookup"><span data-stu-id="1b01d-105">Parts</span></span>  
  
|<span data-ttu-id="1b01d-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="1b01d-106">Term</span></span>|<span data-ttu-id="1b01d-107">定義</span><span class="sxs-lookup"><span data-stu-id="1b01d-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="1b01d-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="1b01d-108">Optional.</span></span> <span data-ttu-id="1b01d-109">字串比較是依據排序次序會導致衍生自內部的二進位表示法的字元。</span><span class="sxs-lookup"><span data-stu-id="1b01d-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="1b01d-110">這種類型是比較的很有用，特別是比較的當字串可以包含要解譯為文字的字元。</span><span class="sxs-lookup"><span data-stu-id="1b01d-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="1b01d-111">在此情況下，您不想要依字母順序排列其等效，例如不區分大小寫比較偏差。</span><span class="sxs-lookup"><span data-stu-id="1b01d-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="1b01d-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="1b01d-112">Optional.</span></span> <span data-ttu-id="1b01d-113">字串比較是依據您的系統地區設定所決定的不區分大小寫文字排序順序中的結果。</span><span class="sxs-lookup"><span data-stu-id="1b01d-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="1b01d-114">如果字串包含所有文字字元，而且您想要納入帳戶字母其等效例如不區分大小寫和密切相關的字母比較它們，這種比較很有用。</span><span class="sxs-lookup"><span data-stu-id="1b01d-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="1b01d-115">例如，您可能要考慮`A`和`a`視為相等，和`Ä`和`ä`是之前`B`和`b`。</span><span class="sxs-lookup"><span data-stu-id="1b01d-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b01d-116">備註</span><span class="sxs-lookup"><span data-stu-id="1b01d-116">Remarks</span></span>  
 <span data-ttu-id="1b01d-117">如果單獨使用，`Option Compare`陳述式必須出現在任何其他來源的程式碼陳述式之前的檔案。</span><span class="sxs-lookup"><span data-stu-id="1b01d-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="1b01d-118">`Option Compare`陳述式指定的字串比較方法 (`Binary`或`Text`)。</span><span class="sxs-lookup"><span data-stu-id="1b01d-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="1b01d-119">預設文字比較方法是`Binary`。</span><span class="sxs-lookup"><span data-stu-id="1b01d-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="1b01d-120">A`Binary`比較比較每個字串中的每個字元的數字 Unicode 值。</span><span class="sxs-lookup"><span data-stu-id="1b01d-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="1b01d-121">A`Text`比較比較根據目前文化特性中其語彙意義的每個 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="1b01d-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="1b01d-122">在 Microsoft Windows 中，依字碼頁會決定排序次序。</span><span class="sxs-lookup"><span data-stu-id="1b01d-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="1b01d-123">如需詳細資訊，請參閱[字碼頁](/cpp/c-runtime-library/code-pages)。</span><span class="sxs-lookup"><span data-stu-id="1b01d-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="1b01d-124">在下列範例中，英文/歐語系字碼頁 (ANSI 1252) 中的字元是使用 `Option Compare Binary` 來排序，這會產生一般的二進位排序順序。</span><span class="sxs-lookup"><span data-stu-id="1b01d-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="1b01d-125">使用 `Option Compare Text` 排序相同字碼頁中的相同字元時，會產生下列的文字排序順序。</span><span class="sxs-lookup"><span data-stu-id="1b01d-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="1b01d-126">Option Compare 陳述式不存在時</span><span class="sxs-lookup"><span data-stu-id="1b01d-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="1b01d-127">如果不包含原始碼`Option Compare`陳述式， **Option Compare**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。</span><span class="sxs-lookup"><span data-stu-id="1b01d-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="1b01d-128">如果您使用命令列編譯器時，所指定的設定[/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)編譯器選項使用。</span><span class="sxs-lookup"><span data-stu-id="1b01d-128">If you use the command-line compiler, the setting specified by the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="1b01d-129">在 IDE 中設定選項比較</span><span class="sxs-lookup"><span data-stu-id="1b01d-129">To set Option Compare in the IDE</span></span>  
  
1.  <span data-ttu-id="1b01d-130">在方案總管中選取專案。</span><span class="sxs-lookup"><span data-stu-id="1b01d-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="1b01d-131">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="1b01d-131">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1b01d-132">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b01d-132">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="1b01d-133">設定中的值**Option Compare**方塊。</span><span class="sxs-lookup"><span data-stu-id="1b01d-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="1b01d-134">當您建立專案， **Option Compare**上設定**編譯** 索引標籤設為**Option Compare**中設定**選項**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1b01d-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="1b01d-135">若要變更這項設定，在**工具**功能表上，按一下 **選項**。</span><span class="sxs-lookup"><span data-stu-id="1b01d-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="1b01d-136">在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。</span><span class="sxs-lookup"><span data-stu-id="1b01d-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="1b01d-137">中的初始預設設定**VB 預設值**是**二進位**。</span><span class="sxs-lookup"><span data-stu-id="1b01d-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="1b01d-138">在命令列上設定選項比較</span><span class="sxs-lookup"><span data-stu-id="1b01d-138">To set Option Compare on the command line</span></span>  
  
-   <span data-ttu-id="1b01d-139">包含[/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)編譯器選項在**vbc**命令。</span><span class="sxs-lookup"><span data-stu-id="1b01d-139">Include the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b01d-140">範例</span><span class="sxs-lookup"><span data-stu-id="1b01d-140">Example</span></span>  
 <span data-ttu-id="1b01d-141">下列範例會使用 `Option Compare` 陳述式來將二進位比較設為預設字串比較方法。</span><span class="sxs-lookup"><span data-stu-id="1b01d-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="1b01d-142">若要使用這段程式碼，請取消註解 `Option Compare Binary` 陳述式，並將其放置在原始程式檔的頂端。</span><span class="sxs-lookup"><span data-stu-id="1b01d-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="1b01d-143">範例</span><span class="sxs-lookup"><span data-stu-id="1b01d-143">Example</span></span>  
 <span data-ttu-id="1b01d-144">下列範例會使用 `Option Compare` 陳述式，將不區分大小寫文字排序順序設定為預設字串比較方法。</span><span class="sxs-lookup"><span data-stu-id="1b01d-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="1b01d-145">若要使用這段程式碼，請取消註解 `Option Compare Text` 陳述式，並將其放置在原始程式檔的頂端。</span><span class="sxs-lookup"><span data-stu-id="1b01d-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1b01d-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b01d-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>  
 <xref:Microsoft.VisualBasic.Strings.Replace%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [<span data-ttu-id="1b01d-147">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="1b01d-147">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="1b01d-148">比較運算子</span><span class="sxs-lookup"><span data-stu-id="1b01d-148">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="1b01d-149">在 Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="1b01d-149">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="1b01d-150">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="1b01d-150">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="1b01d-151">字串函式</span><span class="sxs-lookup"><span data-stu-id="1b01d-151">String Functions</span></span>](../../../visual-basic/language-reference/functions/string-functions.md)  
 [<span data-ttu-id="1b01d-152">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="1b01d-152">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="1b01d-153">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="1b01d-153">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
