---
title: -定義 (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 4cab6bc968275bc12af4365fd3da5e3b5ff417f2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195173"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="b7c14-102">-定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7c14-102">-define (Visual Basic)</span></span>
<span data-ttu-id="b7c14-103">定義條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="b7c14-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7c14-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7c14-104">Syntax</span></span>  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b7c14-105">引數</span><span class="sxs-lookup"><span data-stu-id="b7c14-105">Arguments</span></span>  
  
|<span data-ttu-id="b7c14-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="b7c14-106">Term</span></span>|<span data-ttu-id="b7c14-107">定義</span><span class="sxs-lookup"><span data-stu-id="b7c14-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="b7c14-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="b7c14-108">Required.</span></span> <span data-ttu-id="b7c14-109">要定義的符號。</span><span class="sxs-lookup"><span data-stu-id="b7c14-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="b7c14-110">選擇項。</span><span class="sxs-lookup"><span data-stu-id="b7c14-110">Optional.</span></span> <span data-ttu-id="b7c14-111">要指派 `symbol` 的值。</span><span class="sxs-lookup"><span data-stu-id="b7c14-111">The value to assign `symbol`.</span></span> <span data-ttu-id="b7c14-112">如果`value`是一個字串，它必須以反斜線/引號的順序括住 (\\」) 而不是引號。</span><span class="sxs-lookup"><span data-stu-id="b7c14-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="b7c14-113">如果未指定值，則會認為是 True。</span><span class="sxs-lookup"><span data-stu-id="b7c14-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7c14-114">備註</span><span class="sxs-lookup"><span data-stu-id="b7c14-114">Remarks</span></span>  
 <span data-ttu-id="b7c14-115">`-define`選項的效果類似於使用`#Const`原始程式檔，除了定義的常數的前置處理器指示詞`-define`公開並套用至專案中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="b7c14-115">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="b7c14-116">您可以使用此選項建立的符號，搭配 `#If`...`Then`...`#Else` 指示詞，有條件地編譯原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="b7c14-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="b7c14-117">`-d` 是 `-define` 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="b7c14-117">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="b7c14-118">您可以使用逗號分隔符號定義，以 `-define` 定義多個符號。</span><span class="sxs-lookup"><span data-stu-id="b7c14-118">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="b7c14-119">在 Visual Studio 整合式開發環境中設定 / 定義</span><span class="sxs-lookup"><span data-stu-id="b7c14-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="b7c14-120">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="b7c14-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b7c14-121">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="b7c14-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="b7c14-122">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b7c14-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="b7c14-123">3.按一下 [ **進階**]。</span><span class="sxs-lookup"><span data-stu-id="b7c14-123">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="b7c14-124">4.修改中的值**自訂常數** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="b7c14-124">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b7c14-125">範例</span><span class="sxs-lookup"><span data-stu-id="b7c14-125">Example</span></span>  
 <span data-ttu-id="b7c14-126">下列程式碼會定義然後使用兩個條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="b7c14-126">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b7c14-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7c14-127">See Also</span></span>  
 [<span data-ttu-id="b7c14-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="b7c14-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b7c14-129">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="b7c14-129">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="b7c14-130">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="b7c14-130">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="b7c14-131">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="b7c14-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
