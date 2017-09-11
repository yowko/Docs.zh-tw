---
title: "/define (Visual Basic) |Microsoft 文件"
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
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: 15
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
ms.openlocfilehash: e4eac32b4ab7259b9d3fd2ec37e21406c4cec326
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="define-visual-basic"></a><span data-ttu-id="45a76-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45a76-102">/define (Visual Basic)</span></span>
<span data-ttu-id="45a76-103">定義條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="45a76-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45a76-104">語法</span><span class="sxs-lookup"><span data-stu-id="45a76-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="45a76-105">引數</span><span class="sxs-lookup"><span data-stu-id="45a76-105">Arguments</span></span>  
  
|<span data-ttu-id="45a76-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="45a76-106">Term</span></span>|<span data-ttu-id="45a76-107">定義</span><span class="sxs-lookup"><span data-stu-id="45a76-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="45a76-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="45a76-108">Required.</span></span> <span data-ttu-id="45a76-109">要定義的符號。</span><span class="sxs-lookup"><span data-stu-id="45a76-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="45a76-110">選擇項。</span><span class="sxs-lookup"><span data-stu-id="45a76-110">Optional.</span></span> <span data-ttu-id="45a76-111">要指派 `symbol` 的值。</span><span class="sxs-lookup"><span data-stu-id="45a76-111">The value to assign `symbol`.</span></span> <span data-ttu-id="45a76-112">如果`value`是一個字串，它必須以反斜線/引號的順序括住 (\\」) 而不是引號。</span><span class="sxs-lookup"><span data-stu-id="45a76-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="45a76-113">如果未指定值，則會認為是 True。</span><span class="sxs-lookup"><span data-stu-id="45a76-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45a76-114">備註</span><span class="sxs-lookup"><span data-stu-id="45a76-114">Remarks</span></span>  
 <span data-ttu-id="45a76-115">`/define` 選項有一個類似在原始程式檔中使用 `#Const` 前置處理器指示詞的效果，除了以 `/define` 定義的常數是公開的，且適用於專案中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="45a76-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="45a76-116">您可以使用此選項建立的符號，搭配 `#If`...`Then`...`#Else` 指示詞，有條件地編譯原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="45a76-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="45a76-117">`/d` 是 `/define` 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="45a76-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="45a76-118">您可以使用逗號分隔符號定義，以 `/define` 定義多個符號。</span><span class="sxs-lookup"><span data-stu-id="45a76-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="45a76-119">在 Visual Studio 整合式開發環境中設定 / 定義</span><span class="sxs-lookup"><span data-stu-id="45a76-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="45a76-120">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="45a76-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="45a76-121">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="45a76-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="45a76-122">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="45a76-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="45a76-123">2.按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="45a76-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="45a76-124">3.按一下 [ **進階**]。</span><span class="sxs-lookup"><span data-stu-id="45a76-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="45a76-125">4.修改中的值**自訂常數**方塊。</span><span class="sxs-lookup"><span data-stu-id="45a76-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="45a76-126">範例</span><span class="sxs-lookup"><span data-stu-id="45a76-126">Example</span></span>  
 <span data-ttu-id="45a76-127">下列程式碼會定義然後使用兩個條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="45a76-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 <span data-ttu-id="45a76-128">[!code-vb[VbVbalrCompiler #&45;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="45a76-128">[!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45a76-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45a76-129">See Also</span></span>  
 <span data-ttu-id="45a76-130">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="45a76-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="45a76-131"> [#If......#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="45a76-131"> [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="45a76-132"> [#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md) </span><span class="sxs-lookup"><span data-stu-id="45a76-132"> [#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) </span></span>  
<span data-ttu-id="45a76-133"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="45a76-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
