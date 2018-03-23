---
title: -optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df01fccd7276f0ec759065306ad3614d735f89ef
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-optioninfer"></a><span data-ttu-id="36133-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="36133-102">-optioninfer</span></span>
<span data-ttu-id="36133-103">可讓您在變數宣告中使用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="36133-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36133-104">語法</span><span class="sxs-lookup"><span data-stu-id="36133-104">Syntax</span></span>  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="36133-105">引數</span><span class="sxs-lookup"><span data-stu-id="36133-105">Arguments</span></span>  
  
|<span data-ttu-id="36133-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="36133-106">Term</span></span>|<span data-ttu-id="36133-107">定義</span><span class="sxs-lookup"><span data-stu-id="36133-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="36133-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="36133-108">`+` &#124; `-`</span></span>|<span data-ttu-id="36133-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="36133-109">Optional.</span></span> <span data-ttu-id="36133-110">指定 `-optioninfer+` 以啟用區域類型推斷，或是指定 `-optioninfer-` 以封鎖它。</span><span class="sxs-lookup"><span data-stu-id="36133-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="36133-111">未指定值的 `-optioninfer` 選項與 `-optioninfer+` 相同。</span><span class="sxs-lookup"><span data-stu-id="36133-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="36133-112">不存在 `-optioninfer` 參數時的預設值也是 `-optioninfer+`。</span><span class="sxs-lookup"><span data-stu-id="36133-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="36133-113">預設值是在 Vbc.rsp 回應檔中設定。</span><span class="sxs-lookup"><span data-stu-id="36133-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="36133-114">您可以使用 `-noconfig` 選項來保留編譯器的內部預設值而不是 vbc.rsp 中所指定的預設值。</span><span class="sxs-lookup"><span data-stu-id="36133-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="36133-115">這個選項的編譯器預設值是 `-optioninfer-`。</span><span class="sxs-lookup"><span data-stu-id="36133-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36133-116">備註</span><span class="sxs-lookup"><span data-stu-id="36133-116">Remarks</span></span>  
 <span data-ttu-id="36133-117">如果原始程式碼檔內含[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)，陳述式會覆寫`-optioninfer`命令列編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="36133-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="36133-118">在 Visual Studio IDE 中設定-optioninfer</span><span class="sxs-lookup"><span data-stu-id="36133-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="36133-119">選取的專案中**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="36133-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="36133-120">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="36133-120">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="36133-121">在**編譯**索引標籤上，修改中的值**Option infer**方塊。</span><span class="sxs-lookup"><span data-stu-id="36133-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36133-122">範例</span><span class="sxs-lookup"><span data-stu-id="36133-122">Example</span></span>  
 <span data-ttu-id="36133-123">下列程式碼會在已啟用區域類型推斷下編譯 `test.vb`。</span><span class="sxs-lookup"><span data-stu-id="36133-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="36133-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36133-124">See Also</span></span>  
 [<span data-ttu-id="36133-125">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="36133-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="36133-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="36133-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="36133-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="36133-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="36133-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="36133-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="36133-129">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="36133-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="36133-130">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="36133-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="36133-131">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="36133-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="36133-132">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="36133-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="36133-133">專案設計工具、編譯頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36133-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="36133-134">/noconfig</span><span class="sxs-lookup"><span data-stu-id="36133-134">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="36133-135">從命令列建置</span><span class="sxs-lookup"><span data-stu-id="36133-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
