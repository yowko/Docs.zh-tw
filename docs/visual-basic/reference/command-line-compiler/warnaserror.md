---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: f9ca5575e2a042d68fc490494f2e86991d58b80c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351713"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="05c92-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05c92-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="05c92-103">Causes the compiler to treat the first occurrence of a warning as an error.</span><span class="sxs-lookup"><span data-stu-id="05c92-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c92-104">語法</span><span class="sxs-lookup"><span data-stu-id="05c92-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="05c92-105">引數</span><span class="sxs-lookup"><span data-stu-id="05c92-105">Arguments</span></span>  
  
|<span data-ttu-id="05c92-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="05c92-106">Term</span></span>|<span data-ttu-id="05c92-107">定義</span><span class="sxs-lookup"><span data-stu-id="05c92-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="05c92-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="05c92-108">+ &#124; -</span></span>|<span data-ttu-id="05c92-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="05c92-109">Optional.</span></span> <span data-ttu-id="05c92-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span><span class="sxs-lookup"><span data-stu-id="05c92-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="05c92-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span><span class="sxs-lookup"><span data-stu-id="05c92-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="05c92-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="05c92-112">Optional.</span></span> <span data-ttu-id="05c92-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span><span class="sxs-lookup"><span data-stu-id="05c92-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="05c92-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span><span class="sxs-lookup"><span data-stu-id="05c92-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05c92-115">備註</span><span class="sxs-lookup"><span data-stu-id="05c92-115">Remarks</span></span>  
 <span data-ttu-id="05c92-116">The `-warnaserror` option treats all warnings as errors.</span><span class="sxs-lookup"><span data-stu-id="05c92-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="05c92-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span><span class="sxs-lookup"><span data-stu-id="05c92-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="05c92-118">The compiler reports subsequent occurrences of the same warning as warnings.</span><span class="sxs-lookup"><span data-stu-id="05c92-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="05c92-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span><span class="sxs-lookup"><span data-stu-id="05c92-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="05c92-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span><span class="sxs-lookup"><span data-stu-id="05c92-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="05c92-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span><span class="sxs-lookup"><span data-stu-id="05c92-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05c92-122">The `-warnaserror` option does not control how warnings are displayed.</span><span class="sxs-lookup"><span data-stu-id="05c92-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="05c92-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span><span class="sxs-lookup"><span data-stu-id="05c92-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="05c92-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="05c92-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="05c92-125">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="05c92-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="05c92-126">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="05c92-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="05c92-127">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="05c92-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="05c92-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="05c92-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="05c92-129">4.  Check the **Treat all warnings as errors** check box.</span><span class="sxs-lookup"><span data-stu-id="05c92-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="05c92-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="05c92-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="05c92-131">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="05c92-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="05c92-132">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="05c92-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="05c92-133">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="05c92-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="05c92-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="05c92-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="05c92-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="05c92-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="05c92-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span><span class="sxs-lookup"><span data-stu-id="05c92-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05c92-137">範例</span><span class="sxs-lookup"><span data-stu-id="05c92-137">Example</span></span>  
 <span data-ttu-id="05c92-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span><span class="sxs-lookup"><span data-stu-id="05c92-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="05c92-139">範例</span><span class="sxs-lookup"><span data-stu-id="05c92-139">Example</span></span>  
 <span data-ttu-id="05c92-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span><span class="sxs-lookup"><span data-stu-id="05c92-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="05c92-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="05c92-141">See also</span></span>

- [<span data-ttu-id="05c92-142">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="05c92-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="05c92-143">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="05c92-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="05c92-144">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05c92-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
