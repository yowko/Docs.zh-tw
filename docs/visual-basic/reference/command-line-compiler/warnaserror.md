---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ae8ed68045529e626f2788f854d8e6a6933e7e2
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="0a468-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a468-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="0a468-103">可讓編譯器將第一個出現的警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a468-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a468-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a468-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0a468-105">引數</span><span class="sxs-lookup"><span data-stu-id="0a468-105">Arguments</span></span>  
  
|<span data-ttu-id="0a468-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="0a468-106">Term</span></span>|<span data-ttu-id="0a468-107">定義</span><span class="sxs-lookup"><span data-stu-id="0a468-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="0a468-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="0a468-108">+ &#124; -</span></span>|<span data-ttu-id="0a468-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a468-109">Optional.</span></span> <span data-ttu-id="0a468-110">根據預設，`-warnaserror-`是作用中; 警告不會防止編譯器產生的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="0a468-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="0a468-111">`-warnaserror`相同的選項為`-warnaserror+`，會導致警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a468-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="0a468-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a468-112">Optional.</span></span> <span data-ttu-id="0a468-113">以逗號分隔清單的警告 ID 編號的`-warnaserror`選項會套用。</span><span class="sxs-lookup"><span data-stu-id="0a468-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="0a468-114">如果未不指定任何警告 ID，則`-warnaserror`選項會套用至所有警告。</span><span class="sxs-lookup"><span data-stu-id="0a468-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a468-115">備註</span><span class="sxs-lookup"><span data-stu-id="0a468-115">Remarks</span></span>  
 <span data-ttu-id="0a468-116">`-warnaserror`選項會將所有警告都視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a468-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="0a468-117">原本為警告而是會回報為錯誤報告的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="0a468-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="0a468-118">編譯器會報告為警告的相同警告後面出現。</span><span class="sxs-lookup"><span data-stu-id="0a468-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="0a468-119">根據預設，`-warnaserror-`生效，這會導致只是告知性警告。</span><span class="sxs-lookup"><span data-stu-id="0a468-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="0a468-120">`-warnaserror`相同的選項為`-warnaserror+`，會導致警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a468-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="0a468-121">如果您想只有少數的特定警告視為錯誤，您可以指定要視為錯誤的警告編號的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="0a468-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a468-122">`-warnaserror`選項不會控制會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="0a468-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="0a468-123">使用[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)選項以停用警告。</span><span class="sxs-lookup"><span data-stu-id="0a468-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="0a468-124">若要設定-warnaserror 將所有警告視為錯誤，Visual Studio IDE 中</span><span class="sxs-lookup"><span data-stu-id="0a468-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="0a468-125">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="0a468-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0a468-126">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0a468-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="0a468-127">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0a468-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="0a468-128">3.請確定**停用所有警告**未選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0a468-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="0a468-129">4.請檢查**將所有警告視為錯誤**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0a468-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="0a468-130">若要設定-warnaserror 將特定警告視為錯誤，Visual Studio IDE 中</span><span class="sxs-lookup"><span data-stu-id="0a468-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="0a468-131">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="0a468-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0a468-132">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0a468-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="0a468-133">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0a468-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="0a468-134">3.請確定**停用所有警告**未選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0a468-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="0a468-135">4.請確定**將所有警告視為錯誤**未選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0a468-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="0a468-136">5.選取**錯誤**從**通知**應該視為錯誤的警告旁邊的資料行。</span><span class="sxs-lookup"><span data-stu-id="0a468-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0a468-137">範例</span><span class="sxs-lookup"><span data-stu-id="0a468-137">Example</span></span>  
 <span data-ttu-id="0a468-138">下列程式碼編譯`In.vb`和指示編譯器將顯示的第一個找到的每個警告的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a468-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="0a468-139">範例</span><span class="sxs-lookup"><span data-stu-id="0a468-139">Example</span></span>  
 <span data-ttu-id="0a468-140">下列程式碼編譯`T2.vb`和未使用本機變數 (42024) 警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a468-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a468-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a468-141">See Also</span></span>  
 [<span data-ttu-id="0a468-142">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="0a468-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0a468-143">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="0a468-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="0a468-144">在 Visual Basic 中設定警告</span><span class="sxs-lookup"><span data-stu-id="0a468-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
