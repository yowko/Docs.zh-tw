---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dead17435cd147bdcdf91bdc5b8e0aa651e9e9fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="optimize"></a><span data-ttu-id="672ac-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="672ac-102">/optimize</span></span>
<span data-ttu-id="672ac-103">啟用或停用編譯器最佳化。</span><span class="sxs-lookup"><span data-stu-id="672ac-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="672ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="672ac-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="672ac-105">引數</span><span class="sxs-lookup"><span data-stu-id="672ac-105">Arguments</span></span>  
  
|<span data-ttu-id="672ac-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="672ac-106">Term</span></span>|<span data-ttu-id="672ac-107">定義</span><span class="sxs-lookup"><span data-stu-id="672ac-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="672ac-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="672ac-108">`+` &#124; `-`</span></span>|<span data-ttu-id="672ac-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="672ac-109">Optional.</span></span> <span data-ttu-id="672ac-110">`/optimize-`選項會停用編譯器最佳化。</span><span class="sxs-lookup"><span data-stu-id="672ac-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="672ac-111">`/optimize+`選項啟用最佳化。</span><span class="sxs-lookup"><span data-stu-id="672ac-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="672ac-112">根據預設，會停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="672ac-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="672ac-113">備註</span><span class="sxs-lookup"><span data-stu-id="672ac-113">Remarks</span></span>  
 <span data-ttu-id="672ac-114">較小、 更快更有效率，編譯器最佳化會使輸出檔。</span><span class="sxs-lookup"><span data-stu-id="672ac-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="672ac-115">不過，因為最佳化導致輸出檔中的程式碼重新排列`/optimize+`可能會造成偵錯困難。</span><span class="sxs-lookup"><span data-stu-id="672ac-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="672ac-116">使用產生的所有模組`/target:module`組件必須使用相同`/optimize`設定與組件。</span><span class="sxs-lookup"><span data-stu-id="672ac-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="672ac-117">如需詳細資訊，請參閱[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)。</span><span class="sxs-lookup"><span data-stu-id="672ac-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="672ac-118">您可以結合`/optimize`和`/debug`選項。</span><span class="sxs-lookup"><span data-stu-id="672ac-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="672ac-119">若要設定 / Visual Studio 整合式的開發環境中最佳化</span><span class="sxs-lookup"><span data-stu-id="672ac-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="672ac-120">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="672ac-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="672ac-121">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="672ac-121">On the **Project** menu, click **Properties**.</span></span><br />     <span data-ttu-id="672ac-122">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="672ac-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="672ac-123">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="672ac-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="672ac-124">3.按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="672ac-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="672ac-125">4.修改**啟用最佳化**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="672ac-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="672ac-126">範例</span><span class="sxs-lookup"><span data-stu-id="672ac-126">Example</span></span>  
 <span data-ttu-id="672ac-127">下列程式碼編譯`T2.vb`並啟用編譯器最佳化。</span><span class="sxs-lookup"><span data-stu-id="672ac-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="672ac-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="672ac-128">See Also</span></span>  
 [<span data-ttu-id="672ac-129">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="672ac-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="672ac-130">/debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="672ac-130">/debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="672ac-131">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="672ac-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="672ac-132">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="672ac-132">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
