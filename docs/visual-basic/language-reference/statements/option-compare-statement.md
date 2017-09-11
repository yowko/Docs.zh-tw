---
title: "Option Compare 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
dev_langs:
- VB
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword
- binary comparison
- strings [Visual Basic], returning from functions
- binary comparison, Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword, Option Compare statement
- Binary keyword, Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: 37
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 00618cd914c06b896d68b4074464af866f747895
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="option-compare-statement"></a><span data-ttu-id="49ddf-102">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="49ddf-102">Option Compare Statement</span></span>
<span data-ttu-id="49ddf-103">宣告比較字串資料時要使用的預設比較方法。</span><span class="sxs-lookup"><span data-stu-id="49ddf-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49ddf-104">語法</span><span class="sxs-lookup"><span data-stu-id="49ddf-104">Syntax</span></span>  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="49ddf-105">組件</span><span class="sxs-lookup"><span data-stu-id="49ddf-105">Parts</span></span>  
  
|<span data-ttu-id="49ddf-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="49ddf-106">Term</span></span>|<span data-ttu-id="49ddf-107">定義</span><span class="sxs-lookup"><span data-stu-id="49ddf-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="49ddf-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="49ddf-108">Optional.</span></span> <span data-ttu-id="49ddf-109">字串比較是依據衍生自內部的二進位表示的字元的排序順序中的結果。</span><span class="sxs-lookup"><span data-stu-id="49ddf-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="49ddf-110">這種類型是比較的很有用，特別是比較的如果字串可以包含不是比較的將解譯為文字的字元。</span><span class="sxs-lookup"><span data-stu-id="49ddf-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="49ddf-111">在此情況下，您不想要依字母順序排列其等效，例如不區分大小寫比較偏差。</span><span class="sxs-lookup"><span data-stu-id="49ddf-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="49ddf-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="49ddf-112">Optional.</span></span> <span data-ttu-id="49ddf-113">字串比較是不區分大小寫文字排序順序取決於您的系統地區設定所依據的結果。</span><span class="sxs-lookup"><span data-stu-id="49ddf-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="49ddf-114">如果字串包含所有文字字元，而且您想要考慮到帳戶密切相關的字母等不區分大小寫字母其等效相比較，這種比較很有用。</span><span class="sxs-lookup"><span data-stu-id="49ddf-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="49ddf-115">例如，您可能要考慮`A`和`a`視為相等，以及`Ä`和`ä`排在前面`B`和`b`。</span><span class="sxs-lookup"><span data-stu-id="49ddf-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49ddf-116">備註</span><span class="sxs-lookup"><span data-stu-id="49ddf-116">Remarks</span></span>  
 <span data-ttu-id="49ddf-117">如果使用`Option Compare`陳述式必須出現在任何其他來源的程式碼陳述式之前的檔案。</span><span class="sxs-lookup"><span data-stu-id="49ddf-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="49ddf-118">`Option Compare`陳述式指定的字串比較方法 (`Binary`或`Text`)。</span><span class="sxs-lookup"><span data-stu-id="49ddf-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="49ddf-119">預設文字比較方法是`Binary`。</span><span class="sxs-lookup"><span data-stu-id="49ddf-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="49ddf-120">A`Binary`比較比較每個字串中的每個字元的數字 Unicode 值。</span><span class="sxs-lookup"><span data-stu-id="49ddf-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="49ddf-121">A`Text`比較比較根據其目前的文化特性中的語彙意義的每個 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="49ddf-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="49ddf-122">Microsoft Windows 中的字碼頁會決定排序次序。</span><span class="sxs-lookup"><span data-stu-id="49ddf-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="49ddf-123">如需詳細資訊，請參閱[字碼頁](https://docs.microsoft.com/cpp/c-runtime-library/code-pages)。</span><span class="sxs-lookup"><span data-stu-id="49ddf-123">For more information, see [Code Pages](https://docs.microsoft.com/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="49ddf-124">在下列範例中，英文/歐語系字碼頁 (ANSI 1252) 中的字元是使用 `Option Compare Binary` 來排序，這會產生一般的二進位排序順序。</span><span class="sxs-lookup"><span data-stu-id="49ddf-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="49ddf-125">使用 `Option Compare Text` 排序相同字碼頁中的相同字元時，會產生下列的文字排序順序。</span><span class="sxs-lookup"><span data-stu-id="49ddf-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="49ddf-126">Option Compare 陳述式不存在時</span><span class="sxs-lookup"><span data-stu-id="49ddf-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="49ddf-127">如果原始程式碼不包含`Option Compare`陳述式，**選項比較**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。</span><span class="sxs-lookup"><span data-stu-id="49ddf-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="49ddf-128">如果您使用命令列編譯器時，所指定的設定[/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)編譯器選項使用。</span><span class="sxs-lookup"><span data-stu-id="49ddf-128">If you use the command-line compiler, the setting specified by the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="49ddf-129">在 IDE 中設定選項比較</span><span class="sxs-lookup"><span data-stu-id="49ddf-129">To set Option Compare in the IDE</span></span>  
  
1.  <span data-ttu-id="49ddf-130">在**方案總管 中**，選取專案。</span><span class="sxs-lookup"><span data-stu-id="49ddf-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="49ddf-131">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="49ddf-131">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="49ddf-132">如需詳細資訊，請參閱[NIB︰ 使用專案設計工具管理專案屬性](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)。</span><span class="sxs-lookup"><span data-stu-id="49ddf-132">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="49ddf-133">按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="49ddf-133">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="49ddf-134">在設定的值**選項比較**方塊。</span><span class="sxs-lookup"><span data-stu-id="49ddf-134">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="49ddf-135">當您建立專案，**選項比較**上設定**編譯** 索引標籤設為**選項比較**中設定**選項**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="49ddf-135">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="49ddf-136">若要變更此設定，請在**工具**] 功能表上，按一下 [**選項**。</span><span class="sxs-lookup"><span data-stu-id="49ddf-136">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="49ddf-137">在**選項**對話方塊方塊中，展開**專案和方案**，然後按一下  **VB 預設值**。</span><span class="sxs-lookup"><span data-stu-id="49ddf-137">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="49ddf-138">中的初始預設設定**VB 預設值**是**二進位**。</span><span class="sxs-lookup"><span data-stu-id="49ddf-138">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="49ddf-139">在命令列上設定選項比較</span><span class="sxs-lookup"><span data-stu-id="49ddf-139">To set Option Compare on the command line</span></span>  
  
-   <span data-ttu-id="49ddf-140">包含[/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)編譯器選項，在**vbc**命令。</span><span class="sxs-lookup"><span data-stu-id="49ddf-140">Include the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49ddf-141">範例</span><span class="sxs-lookup"><span data-stu-id="49ddf-141">Example</span></span>  
 <span data-ttu-id="49ddf-142">下列範例會使用 `Option Compare` 陳述式來將二進位比較設為預設字串比較方法。</span><span class="sxs-lookup"><span data-stu-id="49ddf-142">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="49ddf-143">若要使用這段程式碼，請取消註解 `Option Compare Binary` 陳述式，並將其放置在原始程式檔的頂端。</span><span class="sxs-lookup"><span data-stu-id="49ddf-143">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 <span data-ttu-id="49ddf-144">[!code-vb[VbVbalrStatements #&45;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="49ddf-144">[!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="49ddf-145">範例</span><span class="sxs-lookup"><span data-stu-id="49ddf-145">Example</span></span>  
 <span data-ttu-id="49ddf-146">下列範例會使用 `Option Compare` 陳述式，將不區分大小寫文字排序順序設定為預設字串比較方法。</span><span class="sxs-lookup"><span data-stu-id="49ddf-146">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="49ddf-147">若要使用這段程式碼，請取消註解 `Option Compare Text` 陳述式，並將其放置在原始程式檔的頂端。</span><span class="sxs-lookup"><span data-stu-id="49ddf-147">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 <span data-ttu-id="49ddf-148">[!code-vb[VbVbalrStatements #&46;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="49ddf-148">[!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49ddf-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49ddf-149">See Also</span></span>  
 <span data-ttu-id="49ddf-150"><xref:Microsoft.VisualBasic.Strings.InStr%2A></xref:Microsoft.VisualBasic.Strings.InStr%2A></span><span class="sxs-lookup"><span data-stu-id="49ddf-150"><xref:Microsoft.VisualBasic.Strings.InStr%2A></span></span>   
 <span data-ttu-id="49ddf-151"><xref:Microsoft.VisualBasic.Strings.InStrRev%2A></xref:Microsoft.VisualBasic.Strings.InStrRev%2A></span><span class="sxs-lookup"><span data-stu-id="49ddf-151"><xref:Microsoft.VisualBasic.Strings.InStrRev%2A></span></span>   
 <span data-ttu-id="49ddf-152"><xref:Microsoft.VisualBasic.Strings.Replace%2A></xref:Microsoft.VisualBasic.Strings.Replace%2A></span><span class="sxs-lookup"><span data-stu-id="49ddf-152"><xref:Microsoft.VisualBasic.Strings.Replace%2A></span></span>   
 <span data-ttu-id="49ddf-153"><xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A></span><span class="sxs-lookup"><span data-stu-id="49ddf-153"><xref:Microsoft.VisualBasic.Strings.Split%2A></span></span>   
 <span data-ttu-id="49ddf-154"><xref:Microsoft.VisualBasic.Strings.StrComp%2A></xref:Microsoft.VisualBasic.Strings.StrComp%2A></span><span class="sxs-lookup"><span data-stu-id="49ddf-154"><xref:Microsoft.VisualBasic.Strings.StrComp%2A></span></span>   
<span data-ttu-id="49ddf-155"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="49ddf-155"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="49ddf-156"> [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="49ddf-156"> [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="49ddf-157"> [在 Visual Basic 中的比較運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="49ddf-157"> [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="49ddf-158"> [Like 運算子](../../../visual-basic/language-reference/operators/like-operator.md) </span><span class="sxs-lookup"><span data-stu-id="49ddf-158"> [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md) </span></span>  
<span data-ttu-id="49ddf-159"> [字串函式](../../../visual-basic/language-reference/functions/string-functions.md) </span><span class="sxs-lookup"><span data-stu-id="49ddf-159"> [String Functions](../../../visual-basic/language-reference/functions/string-functions.md) </span></span>  
<span data-ttu-id="49ddf-160"> [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="49ddf-160"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="49ddf-161"> [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="49ddf-161"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
