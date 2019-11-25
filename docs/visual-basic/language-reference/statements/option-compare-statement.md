---
title: Option Compare 陳述式
ms.date: 07/20/2015
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
ms.openlocfilehash: 7538466c8f4b90e2e655a2ec762d8c545546a481
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344434"
---
# <a name="option-compare-statement"></a><span data-ttu-id="71c71-102">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="71c71-102">Option Compare Statement</span></span>
<span data-ttu-id="71c71-103">Declares the default comparison method to use when comparing string data.</span><span class="sxs-lookup"><span data-stu-id="71c71-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71c71-104">語法</span><span class="sxs-lookup"><span data-stu-id="71c71-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="71c71-105">組件</span><span class="sxs-lookup"><span data-stu-id="71c71-105">Parts</span></span>  
  
|<span data-ttu-id="71c71-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="71c71-106">Term</span></span>|<span data-ttu-id="71c71-107">定義</span><span class="sxs-lookup"><span data-stu-id="71c71-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="71c71-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="71c71-108">Optional.</span></span> <span data-ttu-id="71c71-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span><span class="sxs-lookup"><span data-stu-id="71c71-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="71c71-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span><span class="sxs-lookup"><span data-stu-id="71c71-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="71c71-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span><span class="sxs-lookup"><span data-stu-id="71c71-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="71c71-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="71c71-112">Optional.</span></span> <span data-ttu-id="71c71-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span><span class="sxs-lookup"><span data-stu-id="71c71-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="71c71-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span><span class="sxs-lookup"><span data-stu-id="71c71-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="71c71-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span><span class="sxs-lookup"><span data-stu-id="71c71-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71c71-116">備註</span><span class="sxs-lookup"><span data-stu-id="71c71-116">Remarks</span></span>  
 <span data-ttu-id="71c71-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span><span class="sxs-lookup"><span data-stu-id="71c71-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="71c71-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span><span class="sxs-lookup"><span data-stu-id="71c71-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="71c71-119">The default text comparison method is `Binary`.</span><span class="sxs-lookup"><span data-stu-id="71c71-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="71c71-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span><span class="sxs-lookup"><span data-stu-id="71c71-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="71c71-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span><span class="sxs-lookup"><span data-stu-id="71c71-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="71c71-122">In Microsoft Windows, sort order is determined by the code page.</span><span class="sxs-lookup"><span data-stu-id="71c71-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="71c71-123">如需詳細資訊，請參閱[字碼頁](/cpp/c-runtime-library/code-pages)。</span><span class="sxs-lookup"><span data-stu-id="71c71-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="71c71-124">在下列範例中，英文/歐語系字碼頁 (ANSI 1252) 中的字元是使用 `Option Compare Binary` 來排序，這會產生一般的二進位排序順序。</span><span class="sxs-lookup"><span data-stu-id="71c71-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="71c71-125">使用 `Option Compare Text` 排序相同字碼頁中的相同字元時，會產生下列的文字排序順序。</span><span class="sxs-lookup"><span data-stu-id="71c71-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="71c71-126">Option Compare 陳述式不存在時</span><span class="sxs-lookup"><span data-stu-id="71c71-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="71c71-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span><span class="sxs-lookup"><span data-stu-id="71c71-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="71c71-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span><span class="sxs-lookup"><span data-stu-id="71c71-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="71c71-129">在 IDE 中設定選項比較</span><span class="sxs-lookup"><span data-stu-id="71c71-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="71c71-130">在方案總管中選取專案。</span><span class="sxs-lookup"><span data-stu-id="71c71-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="71c71-131">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="71c71-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="71c71-132">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="71c71-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="71c71-133">Set the value in the **Option Compare** box.</span><span class="sxs-lookup"><span data-stu-id="71c71-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="71c71-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span><span class="sxs-lookup"><span data-stu-id="71c71-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="71c71-135">To change this setting, on the **Tools** menu, click **Options**.</span><span class="sxs-lookup"><span data-stu-id="71c71-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="71c71-136">在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。</span><span class="sxs-lookup"><span data-stu-id="71c71-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="71c71-137">The initial default setting in **VB Defaults** is **Binary**.</span><span class="sxs-lookup"><span data-stu-id="71c71-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="71c71-138">在命令列上設定選項比較</span><span class="sxs-lookup"><span data-stu-id="71c71-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="71c71-139">Include the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span><span class="sxs-lookup"><span data-stu-id="71c71-139">Include the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71c71-140">範例</span><span class="sxs-lookup"><span data-stu-id="71c71-140">Example</span></span>  
 <span data-ttu-id="71c71-141">下列範例會使用 `Option Compare` 陳述式來將二進位比較設為預設字串比較方法。</span><span class="sxs-lookup"><span data-stu-id="71c71-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="71c71-142">若要使用這段程式碼，請取消註解 `Option Compare Binary` 陳述式，並將其放置在原始程式檔的頂端。</span><span class="sxs-lookup"><span data-stu-id="71c71-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="71c71-143">範例</span><span class="sxs-lookup"><span data-stu-id="71c71-143">Example</span></span>  
 <span data-ttu-id="71c71-144">下列範例會使用 `Option Compare` 陳述式，將不區分大小寫文字排序順序設定為預設字串比較方法。</span><span class="sxs-lookup"><span data-stu-id="71c71-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="71c71-145">若要使用這段程式碼，請取消註解 `Option Compare Text` 陳述式，並將其放置在原始程式檔的頂端。</span><span class="sxs-lookup"><span data-stu-id="71c71-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="71c71-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="71c71-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="71c71-147">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="71c71-147">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="71c71-148">比較運算子</span><span class="sxs-lookup"><span data-stu-id="71c71-148">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="71c71-149">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71c71-149">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="71c71-150">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="71c71-150">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="71c71-151">字串函式</span><span class="sxs-lookup"><span data-stu-id="71c71-151">String Functions</span></span>](../../../visual-basic/language-reference/functions/string-functions.md)
- [<span data-ttu-id="71c71-152">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="71c71-152">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="71c71-153">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="71c71-153">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
