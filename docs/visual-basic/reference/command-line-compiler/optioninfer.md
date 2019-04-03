---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: 89fcd981dbb5442f6150f539db4c7d404fe8d691
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839843"
---
# <a name="-optioninfer"></a><span data-ttu-id="e75cc-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="e75cc-102">-optioninfer</span></span>
<span data-ttu-id="e75cc-103">可讓您在變數宣告中使用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="e75cc-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e75cc-104">語法</span><span class="sxs-lookup"><span data-stu-id="e75cc-104">Syntax</span></span>  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e75cc-105">引數</span><span class="sxs-lookup"><span data-stu-id="e75cc-105">Arguments</span></span>  
  
|<span data-ttu-id="e75cc-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="e75cc-106">Term</span></span>|<span data-ttu-id="e75cc-107">定義</span><span class="sxs-lookup"><span data-stu-id="e75cc-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="e75cc-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e75cc-108">`+` &#124; `-`</span></span>|<span data-ttu-id="e75cc-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e75cc-109">Optional.</span></span> <span data-ttu-id="e75cc-110">指定 `-optioninfer+` 以啟用區域類型推斷，或是指定 `-optioninfer-` 以封鎖它。</span><span class="sxs-lookup"><span data-stu-id="e75cc-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="e75cc-111">未指定值的 `-optioninfer` 選項與 `-optioninfer+` 相同。</span><span class="sxs-lookup"><span data-stu-id="e75cc-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="e75cc-112">不存在 `-optioninfer` 參數時的預設值也是 `-optioninfer+`。</span><span class="sxs-lookup"><span data-stu-id="e75cc-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="e75cc-113">預設值是在 Vbc.rsp 回應檔中設定。</span><span class="sxs-lookup"><span data-stu-id="e75cc-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e75cc-114">您可以使用 `-noconfig` 選項來保留編譯器的內部預設值而不是 vbc.rsp 中所指定的預設值。</span><span class="sxs-lookup"><span data-stu-id="e75cc-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="e75cc-115">這個選項的編譯器預設值是 `-optioninfer-`。</span><span class="sxs-lookup"><span data-stu-id="e75cc-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e75cc-116">備註</span><span class="sxs-lookup"><span data-stu-id="e75cc-116">Remarks</span></span>  
 <span data-ttu-id="e75cc-117">如果原始程式碼檔中包含[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)，此陳述式會覆寫`-optioninfer`命令列編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="e75cc-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="e75cc-118">若要在 Visual Studio IDE 中設定-optioninfer</span><span class="sxs-lookup"><span data-stu-id="e75cc-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="e75cc-119">選取的專案中**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="e75cc-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="e75cc-120">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="e75cc-120">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="e75cc-121">在 [**編譯**索引標籤上，修改中的值**Option infer** ] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="e75cc-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e75cc-122">範例</span><span class="sxs-lookup"><span data-stu-id="e75cc-122">Example</span></span>  
 <span data-ttu-id="e75cc-123">下列程式碼會在已啟用區域類型推斷下編譯 `test.vb`。</span><span class="sxs-lookup"><span data-stu-id="e75cc-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e75cc-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e75cc-124">See also</span></span>

- [<span data-ttu-id="e75cc-125">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="e75cc-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e75cc-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="e75cc-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="e75cc-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e75cc-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="e75cc-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="e75cc-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="e75cc-129">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="e75cc-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="e75cc-130">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="e75cc-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="e75cc-131">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="e75cc-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="e75cc-132">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="e75cc-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="e75cc-133">專案設計工具、編譯頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e75cc-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="e75cc-134">/noconfig</span><span class="sxs-lookup"><span data-stu-id="e75cc-134">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="e75cc-135">從命令列建置</span><span class="sxs-lookup"><span data-stu-id="e75cc-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
