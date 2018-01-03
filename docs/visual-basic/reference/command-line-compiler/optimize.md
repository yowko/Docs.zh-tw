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
ms.openlocfilehash: e157fb0e1fcdb3899440eed02a42b16f75541989
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="optimize"></a><span data-ttu-id="67ba9-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="67ba9-102">/optimize</span></span>
<span data-ttu-id="67ba9-103">啟用或停用編譯器最佳化。</span><span class="sxs-lookup"><span data-stu-id="67ba9-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67ba9-104">語法</span><span class="sxs-lookup"><span data-stu-id="67ba9-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="67ba9-105">引數</span><span class="sxs-lookup"><span data-stu-id="67ba9-105">Arguments</span></span>  
  
|<span data-ttu-id="67ba9-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="67ba9-106">Term</span></span>|<span data-ttu-id="67ba9-107">定義</span><span class="sxs-lookup"><span data-stu-id="67ba9-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="67ba9-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="67ba9-108">`+` &#124; `-`</span></span>|<span data-ttu-id="67ba9-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="67ba9-109">Optional.</span></span> <span data-ttu-id="67ba9-110">`/optimize-`選項會停用編譯器最佳化。</span><span class="sxs-lookup"><span data-stu-id="67ba9-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="67ba9-111">`/optimize+`選項啟用最佳化。</span><span class="sxs-lookup"><span data-stu-id="67ba9-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="67ba9-112">根據預設，會停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="67ba9-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67ba9-113">備註</span><span class="sxs-lookup"><span data-stu-id="67ba9-113">Remarks</span></span>  
 <span data-ttu-id="67ba9-114">編譯器最佳化可讓您的輸出檔案變得更小、更快、更有效率。</span><span class="sxs-lookup"><span data-stu-id="67ba9-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="67ba9-115">不過，因為最佳化導致輸出檔中的程式碼重新排列`/optimize+`可能會造成偵錯困難。</span><span class="sxs-lookup"><span data-stu-id="67ba9-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="67ba9-116">使用產生的所有模組`/target:module`組件必須使用相同`/optimize`設定與組件。</span><span class="sxs-lookup"><span data-stu-id="67ba9-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="67ba9-117">如需詳細資訊，請參閱[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)。</span><span class="sxs-lookup"><span data-stu-id="67ba9-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="67ba9-118">您可以結合`/optimize`和`/debug`選項。</span><span class="sxs-lookup"><span data-stu-id="67ba9-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="67ba9-119">若要設定 / Visual Studio 整合式的開發環境中最佳化</span><span class="sxs-lookup"><span data-stu-id="67ba9-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="67ba9-120">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="67ba9-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="67ba9-121">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="67ba9-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="67ba9-122">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="67ba9-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="67ba9-123">3.按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="67ba9-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="67ba9-124">4.修改**啟用最佳化**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="67ba9-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="67ba9-125">範例</span><span class="sxs-lookup"><span data-stu-id="67ba9-125">Example</span></span>  
 <span data-ttu-id="67ba9-126">下列程式碼編譯`T2.vb`並啟用編譯器最佳化。</span><span class="sxs-lookup"><span data-stu-id="67ba9-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="67ba9-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="67ba9-127">See Also</span></span>  
 [<span data-ttu-id="67ba9-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="67ba9-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="67ba9-129">/debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67ba9-129">/debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="67ba9-130">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="67ba9-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="67ba9-131">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67ba9-131">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
