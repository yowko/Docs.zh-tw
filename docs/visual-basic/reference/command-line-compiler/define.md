---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: fd0875f09bf3ba7211ede500aa0da45f8b7cd2c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344768"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="fbf7e-102">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbf7e-102">-define (Visual Basic)</span></span>
<span data-ttu-id="fbf7e-103">定義條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf7e-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbf7e-104">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="fbf7e-105">或</span><span class="sxs-lookup"><span data-stu-id="fbf7e-105">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="fbf7e-106">引數</span><span class="sxs-lookup"><span data-stu-id="fbf7e-106">Arguments</span></span>  
  
|<span data-ttu-id="fbf7e-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="fbf7e-107">Term</span></span>|<span data-ttu-id="fbf7e-108">定義</span><span class="sxs-lookup"><span data-stu-id="fbf7e-108">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="fbf7e-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-109">Required.</span></span> <span data-ttu-id="fbf7e-110">要定義的符號。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-110">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="fbf7e-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-111">Optional.</span></span> <span data-ttu-id="fbf7e-112">要指派 `symbol` 的值。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-112">The value to assign `symbol`.</span></span> <span data-ttu-id="fbf7e-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span><span class="sxs-lookup"><span data-stu-id="fbf7e-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="fbf7e-114">如果未指定值，則會認為是 True。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-114">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbf7e-115">備註</span><span class="sxs-lookup"><span data-stu-id="fbf7e-115">Remarks</span></span>  
 <span data-ttu-id="fbf7e-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span><span class="sxs-lookup"><span data-stu-id="fbf7e-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="fbf7e-117">您可以使用此選項建立的符號，搭配 `#If`...`Then`...`#Else` 指示詞，有條件地編譯原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="fbf7e-118">`-d` 是 `-define` 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-118">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="fbf7e-119">您可以使用逗號分隔符號定義，以 `-define` 定義多個符號。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="fbf7e-120">在 Visual Studio 整合式開發環境中設定 / 定義</span><span class="sxs-lookup"><span data-stu-id="fbf7e-120">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="fbf7e-121">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="fbf7e-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fbf7e-122">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-122">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="fbf7e-123">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="fbf7e-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="fbf7e-124">3.  Click **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="fbf7e-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="fbf7e-125">4.  Modify the value in the **Custom Constants** box.</span><span class="sxs-lookup"><span data-stu-id="fbf7e-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fbf7e-126">範例</span><span class="sxs-lookup"><span data-stu-id="fbf7e-126">Example</span></span>  
 <span data-ttu-id="fbf7e-127">下列程式碼會定義然後使用兩個條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="fbf7e-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="fbf7e-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbf7e-128">See also</span></span>

- [<span data-ttu-id="fbf7e-129">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="fbf7e-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fbf7e-130">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="fbf7e-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="fbf7e-131">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="fbf7e-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="fbf7e-132">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="fbf7e-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
