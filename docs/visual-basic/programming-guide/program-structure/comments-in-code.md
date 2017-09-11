---
title: "程式碼 (Visual Basic) 中的註解 |Microsoft 文件"
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
- Uncomment button
- REM statement
- comments, in code
- comments, Visual Basic code
- Comment button
- buttons, Uncomment
- buttons, Comment
- code comments, Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: 17
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
ms.openlocfilehash: e872c9bb67835573aadcc1016f2c6a98d434201e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="c7130-102">程式碼中的註解 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7130-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="c7130-103">當您閱讀程式碼範例時，常會遇到註解符號 (`'`)。</span><span class="sxs-lookup"><span data-stu-id="c7130-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="c7130-104">這個符號會告知[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器忽略它後面的文字或*註解*。</span><span class="sxs-lookup"><span data-stu-id="c7130-104">This symbol tells the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="c7130-105">註解是為了閱讀者方便而加入至程式碼的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="c7130-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="c7130-106">以簡短註解做為所有程序開頭是良好的程式設計作法，此註解會描述程序的基本特性 (作用為何)。</span><span class="sxs-lookup"><span data-stu-id="c7130-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="c7130-107">這對於您自己以及對於其他檢查程式碼的人都有好處。</span><span class="sxs-lookup"><span data-stu-id="c7130-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="c7130-108">您應該將描述功能特性的註解，與實作 (Implementation) 細節 (程序是如何運作) 分開。</span><span class="sxs-lookup"><span data-stu-id="c7130-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="c7130-109">當您將實作細節包含在描述中，請記得在更新函式時，將實作細節一同更新。</span><span class="sxs-lookup"><span data-stu-id="c7130-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="c7130-110">註解可以跟隨在陳述式之後的同一行中，或者佔據一整行。</span><span class="sxs-lookup"><span data-stu-id="c7130-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="c7130-111">兩者皆會在以下程式碼中加以說明。</span><span class="sxs-lookup"><span data-stu-id="c7130-111">Both are illustrated in the following code.</span></span>  
  
 <span data-ttu-id="c7130-112">[!code-vb[VbVbcnConventions #&16;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c7130-112">[!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]</span></span>  
  
 <span data-ttu-id="c7130-113">如果需要有一行以上的註解，請在每一行中使用註解符號，如下列範例：</span><span class="sxs-lookup"><span data-stu-id="c7130-113">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 <span data-ttu-id="c7130-114">[!code-vb[VbVbcnConventions #&17;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c7130-114">[!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]</span></span>  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="c7130-115">註解方針</span><span class="sxs-lookup"><span data-stu-id="c7130-115">Commenting Guidelines</span></span>  
 <span data-ttu-id="c7130-116">下表提供哪些註解類型可以出現在一段程式碼之前的一般方針。</span><span class="sxs-lookup"><span data-stu-id="c7130-116">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="c7130-117">這些都是建議，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 不會強制加入註解的規則。</span><span class="sxs-lookup"><span data-stu-id="c7130-117">These are suggestions; [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not enforce rules for adding comments.</span></span> <span data-ttu-id="c7130-118">撰寫對您自己與其他閱讀程式碼的人而言最有效的註解。</span><span class="sxs-lookup"><span data-stu-id="c7130-118">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="c7130-119">註解類型</span><span class="sxs-lookup"><span data-stu-id="c7130-119">Comment type</span></span>|<span data-ttu-id="c7130-120">註解說明</span><span class="sxs-lookup"><span data-stu-id="c7130-120">Comment description</span></span>|  
|<span data-ttu-id="c7130-121">用途</span><span class="sxs-lookup"><span data-stu-id="c7130-121">Purpose</span></span>|<span data-ttu-id="c7130-122">描述程序的功用 (非如何運作)</span><span class="sxs-lookup"><span data-stu-id="c7130-122">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="c7130-123">假設</span><span class="sxs-lookup"><span data-stu-id="c7130-123">Assumptions</span></span>|<span data-ttu-id="c7130-124">列出每個外部變數、控制項、開啟檔案或其他程序存取的項目</span><span class="sxs-lookup"><span data-stu-id="c7130-124">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="c7130-125">效果</span><span class="sxs-lookup"><span data-stu-id="c7130-125">Effects</span></span>|<span data-ttu-id="c7130-126">列出每個受影響的外部變數、控制項或檔案，以及其所受的影響 (僅限於不明顯的)</span><span class="sxs-lookup"><span data-stu-id="c7130-126">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="c7130-127">輸入</span><span class="sxs-lookup"><span data-stu-id="c7130-127">Inputs</span></span>|<span data-ttu-id="c7130-128">指定引數的用途</span><span class="sxs-lookup"><span data-stu-id="c7130-128">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="c7130-129">Returns</span><span class="sxs-lookup"><span data-stu-id="c7130-129">Returns</span></span>|<span data-ttu-id="c7130-130">說明程序傳回的值</span><span class="sxs-lookup"><span data-stu-id="c7130-130">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="c7130-131">請記住以下要點：</span><span class="sxs-lookup"><span data-stu-id="c7130-131">Remember the following points:</span></span>  
  
-   <span data-ttu-id="c7130-132">每個重要的變數宣告之前都應該有註解，此註解會描述所宣告之變數的用途。</span><span class="sxs-lookup"><span data-stu-id="c7130-132">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
-   <span data-ttu-id="c7130-133">變數、控制項和程序應該清楚命名，讓註解只需用於複雜的實作細節中。</span><span class="sxs-lookup"><span data-stu-id="c7130-133">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
-   <span data-ttu-id="c7130-134">註解不可以跟隨在同一行的行接續序列之後。</span><span class="sxs-lookup"><span data-stu-id="c7130-134">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="c7130-135">您可以新增或移除選取的程式碼的一或多行，選擇一段程式碼的註解符號**註解**(![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) 和**取消註解**(![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) 上的按鈕**編輯**工具列。</span><span class="sxs-lookup"><span data-stu-id="c7130-135">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) and **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7130-136">您也可以藉由在文字前方置入 `REM` 關鍵字，將註解加入至您的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="c7130-136">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="c7130-137">不過，`'`符號和**註解**/**取消註解**按鈕比較容易使用，而且需要較少的空間和記憶體。</span><span class="sxs-lookup"><span data-stu-id="c7130-137">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7130-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7130-138">See Also</span></span>  
 <span data-ttu-id="c7130-139">[記錄程式碼使用 XML 註解](http://msdn.microsoft.com/magazine/dd722812.aspx) </span><span class="sxs-lookup"><span data-stu-id="c7130-139">[Documenting Your Code With XML Comments](http://msdn.microsoft.com/magazine/dd722812.aspx) </span></span>  
<span data-ttu-id="c7130-140"> [如何︰ 建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="c7130-140"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md) </span></span>  
<span data-ttu-id="c7130-141"> [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="c7130-141"> [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span></span>  
<span data-ttu-id="c7130-142"> [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="c7130-142"> [Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="c7130-143"> [REM 陳述式](../../../visual-basic/language-reference/statements/rem-statement.md)</span><span class="sxs-lookup"><span data-stu-id="c7130-143"> [REM Statement](../../../visual-basic/language-reference/statements/rem-statement.md)</span></span>
