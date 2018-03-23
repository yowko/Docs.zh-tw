---
title: -最佳化
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7df1c873c166def9fde1bedc139470263e3e4437
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-optimize"></a><span data-ttu-id="0368a-102">-最佳化</span><span class="sxs-lookup"><span data-stu-id="0368a-102">-optimize</span></span>
<span data-ttu-id="0368a-103">啟用或停用編譯器最佳化。</span><span class="sxs-lookup"><span data-stu-id="0368a-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0368a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0368a-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0368a-105">引數</span><span class="sxs-lookup"><span data-stu-id="0368a-105">Arguments</span></span>  
  
|<span data-ttu-id="0368a-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="0368a-106">Term</span></span>|<span data-ttu-id="0368a-107">定義</span><span class="sxs-lookup"><span data-stu-id="0368a-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="0368a-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0368a-108">`+` &#124; `-`</span></span>|<span data-ttu-id="0368a-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0368a-109">Optional.</span></span> <span data-ttu-id="0368a-110">`-optimize-`選項會停用編譯器最佳化。</span><span class="sxs-lookup"><span data-stu-id="0368a-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="0368a-111">`-optimize+`選項啟用最佳化。</span><span class="sxs-lookup"><span data-stu-id="0368a-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="0368a-112">根據預設，會停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="0368a-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0368a-113">備註</span><span class="sxs-lookup"><span data-stu-id="0368a-113">Remarks</span></span>  
 <span data-ttu-id="0368a-114">編譯器最佳化可讓您的輸出檔案變得更小、更快、更有效率。</span><span class="sxs-lookup"><span data-stu-id="0368a-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="0368a-115">不過，因為最佳化導致輸出檔中的程式碼重新排列`-optimize+`可能會造成偵錯困難。</span><span class="sxs-lookup"><span data-stu-id="0368a-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="0368a-116">使用產生的所有模組`-target:module`組件必須使用相同`-optimize`設定與組件。</span><span class="sxs-lookup"><span data-stu-id="0368a-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="0368a-117">如需詳細資訊，請參閱[-目標 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)。</span><span class="sxs-lookup"><span data-stu-id="0368a-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="0368a-118">您可以結合`-optimize`和`-debug`選項。</span><span class="sxs-lookup"><span data-stu-id="0368a-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="0368a-119">若要設定的最佳化 Visual Studio 整合式的開發環境中</span><span class="sxs-lookup"><span data-stu-id="0368a-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0368a-120">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="0368a-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0368a-121">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0368a-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="0368a-122">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0368a-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="0368a-123">3.按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0368a-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="0368a-124">4.修改**啟用最佳化**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0368a-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0368a-125">範例</span><span class="sxs-lookup"><span data-stu-id="0368a-125">Example</span></span>  
 <span data-ttu-id="0368a-126">下列程式碼編譯`T2.vb`並啟用編譯器最佳化。</span><span class="sxs-lookup"><span data-stu-id="0368a-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="0368a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0368a-127">See Also</span></span>  
 [<span data-ttu-id="0368a-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="0368a-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0368a-129">-偵錯 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0368a-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="0368a-130">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="0368a-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="0368a-131">-目標 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0368a-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
