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
ms.openlocfilehash: cb56e727479fd249cb0d7e5e7c3c50d5b68b3a72
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072011"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="c3ff4-102">-定義 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="c3ff4-102">-define (Visual Basic)</span></span>

<span data-ttu-id="c3ff4-103">定義條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ff4-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3ff4-104">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="c3ff4-105">或</span><span class="sxs-lookup"><span data-stu-id="c3ff4-105">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c3ff4-106">引數</span><span class="sxs-lookup"><span data-stu-id="c3ff4-106">Arguments</span></span>  
  
|<span data-ttu-id="c3ff4-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="c3ff4-107">Term</span></span>|<span data-ttu-id="c3ff4-108">定義</span><span class="sxs-lookup"><span data-stu-id="c3ff4-108">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="c3ff4-109">必要。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-109">Required.</span></span> <span data-ttu-id="c3ff4-110">要定義的符號。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-110">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="c3ff4-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-111">Optional.</span></span> <span data-ttu-id="c3ff4-112">要指派 `symbol` 的值。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-112">The value to assign `symbol`.</span></span> <span data-ttu-id="c3ff4-113">如果 `value` 是字串，則必須以反斜線/引號順序括住 (\\ ") 而非引號。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="c3ff4-114">如果未指定值，則會認為是 True。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-114">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3ff4-115">備註</span><span class="sxs-lookup"><span data-stu-id="c3ff4-115">Remarks</span></span>  

 <span data-ttu-id="c3ff4-116">此 `-define` 選項的效果類似于 `#Const` 在原始程式檔中使用預處理器指示詞，不同之處在于使用定義的常數 `-define` 是公用的，而且會套用至專案中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="c3ff4-117">您可以使用此選項建立的符號，搭配 `#If`...`Then`...`#Else` 指示詞，有條件地編譯原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="c3ff4-118">`-d` 是 `-define` 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-118">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="c3ff4-119">您可以使用逗號分隔符號定義，以 `-define` 定義多個符號。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="c3ff4-120">在 Visual Studio 整合式開發環境中設定-定義</span><span class="sxs-lookup"><span data-stu-id="c3ff4-120">To set -define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="c3ff4-121">1. 在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c3ff4-122">按一下 [專案] 功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-122">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="c3ff4-123">2. 按一下 [ **編譯** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="c3ff4-124">3. 按一下 [ **Advanced**]。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="c3ff4-125">4. 修改 [ **自訂常數** ] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c3ff4-126">範例</span><span class="sxs-lookup"><span data-stu-id="c3ff4-126">Example</span></span>  

 <span data-ttu-id="c3ff4-127">下列程式碼會定義然後使用兩個條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="c3ff4-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="c3ff4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3ff4-128">See also</span></span>

- [<span data-ttu-id="c3ff4-129">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="c3ff4-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c3ff4-130">#If .。。Then ... #Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="c3ff4-130">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="c3ff4-131">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="c3ff4-131">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)
- [<span data-ttu-id="c3ff4-132">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="c3ff4-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
