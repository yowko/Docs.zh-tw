---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005379"
---
# <a name="-optimize"></a><span data-ttu-id="71dad-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="71dad-102">-optimize</span></span>
<span data-ttu-id="71dad-103">啟用或停用編譯器優化。</span><span class="sxs-lookup"><span data-stu-id="71dad-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71dad-104">語法</span><span class="sxs-lookup"><span data-stu-id="71dad-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="71dad-105">引數</span><span class="sxs-lookup"><span data-stu-id="71dad-105">Arguments</span></span>  
  
|<span data-ttu-id="71dad-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="71dad-106">Term</span></span>|<span data-ttu-id="71dad-107">定義</span><span class="sxs-lookup"><span data-stu-id="71dad-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="71dad-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="71dad-108">`+` &#124; `-`</span></span>|<span data-ttu-id="71dad-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="71dad-109">Optional.</span></span> <span data-ttu-id="71dad-110">@No__t-0 選項會停用編譯器優化。</span><span class="sxs-lookup"><span data-stu-id="71dad-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="71dad-111">@No__t-0 選項會啟用優化。</span><span class="sxs-lookup"><span data-stu-id="71dad-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="71dad-112">根據預設，會停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="71dad-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71dad-113">備註</span><span class="sxs-lookup"><span data-stu-id="71dad-113">Remarks</span></span>  
 <span data-ttu-id="71dad-114">編譯器最佳化可讓您的輸出檔案變得更小、更快、更有效率。</span><span class="sxs-lookup"><span data-stu-id="71dad-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="71dad-115">不過，由於優化會導致輸出檔中的程式碼重新排列，`-optimize+` 會使偵錯工具變得很棘手。</span><span class="sxs-lookup"><span data-stu-id="71dad-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="71dad-116">為元件產生的所有模組 `-target:module`，都必須使用與元件相同的 @no__t 1 設定。</span><span class="sxs-lookup"><span data-stu-id="71dad-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="71dad-117">如需詳細資訊，請參閱[-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)。</span><span class="sxs-lookup"><span data-stu-id="71dad-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="71dad-118">您可以結合 `-optimize` 和 `-debug` 選項。</span><span class="sxs-lookup"><span data-stu-id="71dad-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="71dad-119">在 Visual Studio 的整合式開發環境中設定-optimize</span><span class="sxs-lookup"><span data-stu-id="71dad-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="71dad-120">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="71dad-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="71dad-121">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="71dad-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="71dad-122">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="71dad-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="71dad-123">3.按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="71dad-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="71dad-124">4.修改 [**啟用優化**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="71dad-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="71dad-125">範例</span><span class="sxs-lookup"><span data-stu-id="71dad-125">Example</span></span>  
 <span data-ttu-id="71dad-126">下列程式碼會編譯 `T2.vb`，並啟用編譯器優化。</span><span class="sxs-lookup"><span data-stu-id="71dad-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="71dad-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71dad-127">See also</span></span>

- [<span data-ttu-id="71dad-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="71dad-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="71dad-129">-debug （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="71dad-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="71dad-130">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="71dad-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="71dad-131">-target （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="71dad-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
