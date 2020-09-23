---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: d4b50d56373676bf78a7591102095209401c907d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097588"
---
# <a name="-optimize"></a><span data-ttu-id="7ca8f-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="7ca8f-102">-optimize</span></span>

<span data-ttu-id="7ca8f-103">啟用或停用編譯器優化。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ca8f-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ca8f-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7ca8f-105">引數</span><span class="sxs-lookup"><span data-stu-id="7ca8f-105">Arguments</span></span>  
  
|<span data-ttu-id="7ca8f-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="7ca8f-106">Term</span></span>|<span data-ttu-id="7ca8f-107">定義</span><span class="sxs-lookup"><span data-stu-id="7ca8f-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="7ca8f-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="7ca8f-108">`+` &#124; `-`</span></span>|<span data-ttu-id="7ca8f-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-109">Optional.</span></span> <span data-ttu-id="7ca8f-110">`-optimize-`選項會停用編譯器優化。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="7ca8f-111">`-optimize+`選項會啟用優化。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="7ca8f-112">根據預設，會停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ca8f-113">備註</span><span class="sxs-lookup"><span data-stu-id="7ca8f-113">Remarks</span></span>  

 <span data-ttu-id="7ca8f-114">編譯器最佳化可讓您的輸出檔案變得更小、更快、更有效率。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="7ca8f-115">不過，因為優化會導致輸出檔中的程式碼重新排列，所以 `-optimize+` 很難進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="7ca8f-116">針對元件產生的所有模組都 `-target:module` 必須使用與元件相同的 `-optimize` 設定。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="7ca8f-117">如需詳細資訊，請參閱 [-目標 (Visual Basic) ](target.md)。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-117">For more information, see [-target (Visual Basic)](target.md).</span></span>  
  
 <span data-ttu-id="7ca8f-118">您可以結合 `-optimize` 和 `-debug` 選項。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="7ca8f-119">在 Visual Studio 整合式開發環境中設定-優化</span><span class="sxs-lookup"><span data-stu-id="7ca8f-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="7ca8f-120">1. 在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7ca8f-121">按一下 [專案] 功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="7ca8f-122">2. 按一下 [ **編譯** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="7ca8f-123">3. 按一下 [ **Advanced** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="7ca8f-124">4. 修改 [ **啟用優化** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7ca8f-125">範例</span><span class="sxs-lookup"><span data-stu-id="7ca8f-125">Example</span></span>  

 <span data-ttu-id="7ca8f-126">下列程式碼會編譯 `T2.vb` 並啟用編譯器優化。</span><span class="sxs-lookup"><span data-stu-id="7ca8f-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ca8f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ca8f-127">See also</span></span>

- [<span data-ttu-id="7ca8f-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="7ca8f-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7ca8f-129">-debug (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="7ca8f-129">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="7ca8f-130">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="7ca8f-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="7ca8f-131">-目標 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="7ca8f-131">-target (Visual Basic)</span></span>](target.md)
