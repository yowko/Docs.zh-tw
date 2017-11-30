---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a><span data-ttu-id="798bc-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="798bc-102">/define (Visual Basic)</span></span>
<span data-ttu-id="798bc-103">定義條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="798bc-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="798bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="798bc-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="798bc-105">引數</span><span class="sxs-lookup"><span data-stu-id="798bc-105">Arguments</span></span>  
  
|<span data-ttu-id="798bc-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="798bc-106">Term</span></span>|<span data-ttu-id="798bc-107">定義</span><span class="sxs-lookup"><span data-stu-id="798bc-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="798bc-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="798bc-108">Required.</span></span> <span data-ttu-id="798bc-109">要定義的符號。</span><span class="sxs-lookup"><span data-stu-id="798bc-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="798bc-110">選擇項。</span><span class="sxs-lookup"><span data-stu-id="798bc-110">Optional.</span></span> <span data-ttu-id="798bc-111">要指派 `symbol` 的值。</span><span class="sxs-lookup"><span data-stu-id="798bc-111">The value to assign `symbol`.</span></span> <span data-ttu-id="798bc-112">如果`value`是一個字串，必須以反斜線/引號序列括住 (\\") 而不是引號。</span><span class="sxs-lookup"><span data-stu-id="798bc-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="798bc-113">如果未指定值，則會認為是 True。</span><span class="sxs-lookup"><span data-stu-id="798bc-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="798bc-114">備註</span><span class="sxs-lookup"><span data-stu-id="798bc-114">Remarks</span></span>  
 <span data-ttu-id="798bc-115">`/define` 選項有一個類似在原始程式檔中使用 `#Const` 前置處理器指示詞的效果，除了以 `/define` 定義的常數是公開的，且適用於專案中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="798bc-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="798bc-116">您可以使用此選項建立的符號，搭配 `#If`...`Then`...`#Else` 指示詞，有條件地編譯原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="798bc-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="798bc-117">`/d` 是 `/define` 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="798bc-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="798bc-118">您可以使用逗號分隔符號定義，以 `/define` 定義多個符號。</span><span class="sxs-lookup"><span data-stu-id="798bc-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="798bc-119">在 Visual Studio 整合式開發環境中設定 / 定義</span><span class="sxs-lookup"><span data-stu-id="798bc-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="798bc-120">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="798bc-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="798bc-121">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="798bc-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="798bc-122">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="798bc-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="798bc-123">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="798bc-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="798bc-124">3.按一下 [ **進階**]。</span><span class="sxs-lookup"><span data-stu-id="798bc-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="798bc-125">4.修改中的值**自訂常數**方塊。</span><span class="sxs-lookup"><span data-stu-id="798bc-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="798bc-126">範例</span><span class="sxs-lookup"><span data-stu-id="798bc-126">Example</span></span>  
 <span data-ttu-id="798bc-127">下列程式碼會定義然後使用兩個條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="798bc-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="798bc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="798bc-128">See Also</span></span>  
 [<span data-ttu-id="798bc-129">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="798bc-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="798bc-130">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="798bc-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="798bc-131">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="798bc-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="798bc-132">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="798bc-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
