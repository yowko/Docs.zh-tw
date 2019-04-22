---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: c06326a250fba0de2f63e13672b4fffbfa8a07f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835059"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="80cee-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80cee-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="80cee-103">可讓編譯器在第一個出現的警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="80cee-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80cee-104">語法</span><span class="sxs-lookup"><span data-stu-id="80cee-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="80cee-105">引數</span><span class="sxs-lookup"><span data-stu-id="80cee-105">Arguments</span></span>  
  
|<span data-ttu-id="80cee-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="80cee-106">Term</span></span>|<span data-ttu-id="80cee-107">定義</span><span class="sxs-lookup"><span data-stu-id="80cee-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="80cee-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="80cee-108">+ &#124; -</span></span>|<span data-ttu-id="80cee-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="80cee-109">Optional.</span></span> <span data-ttu-id="80cee-110">根據預設，`-warnaserror-`是作用中; 警告不會防止編譯器產生的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="80cee-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="80cee-111">`-warnaserror`相同的選項為`-warnaserror+`，會導致警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="80cee-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="80cee-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="80cee-112">Optional.</span></span> <span data-ttu-id="80cee-113">以逗號分隔的清單，警告識別碼的數字的`-warnaserror`選項會套用。</span><span class="sxs-lookup"><span data-stu-id="80cee-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="80cee-114">如果未不指定任何警告識別碼，則`-warnaserror`選項會套用至所有警告。</span><span class="sxs-lookup"><span data-stu-id="80cee-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80cee-115">備註</span><span class="sxs-lookup"><span data-stu-id="80cee-115">Remarks</span></span>  
 <span data-ttu-id="80cee-116">`-warnaserror`選項會將所有警告都視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="80cee-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="80cee-117">任何會報告為警告而是會回報為錯誤的訊息。</span><span class="sxs-lookup"><span data-stu-id="80cee-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="80cee-118">編譯器會報告為警告的相同警告後面出現。</span><span class="sxs-lookup"><span data-stu-id="80cee-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="80cee-119">根據預設，`-warnaserror-`會生效，這會導致只是告知性警告。</span><span class="sxs-lookup"><span data-stu-id="80cee-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="80cee-120">`-warnaserror`相同的選項為`-warnaserror+`，會導致警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="80cee-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="80cee-121">如果您想只將少數特定警告視為錯誤，您可以指定以逗號分隔的警告編號清單視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="80cee-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80cee-122">`-warnaserror`選項不會控制警告的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="80cee-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="80cee-123">使用[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)停用警告的選項。</span><span class="sxs-lookup"><span data-stu-id="80cee-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="80cee-124">若要設定將所有警告視為錯誤，Visual Studio IDE 中-warnaserror</span><span class="sxs-lookup"><span data-stu-id="80cee-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="80cee-125">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="80cee-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="80cee-126">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="80cee-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="80cee-127">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="80cee-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="80cee-128">3.請確定**停用所有警告**未核取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="80cee-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="80cee-129">4.請檢查**將所有警告視為錯誤**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="80cee-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="80cee-130">若要設定將特定警告視為錯誤，Visual Studio IDE 中-warnaserror</span><span class="sxs-lookup"><span data-stu-id="80cee-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="80cee-131">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="80cee-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="80cee-132">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="80cee-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="80cee-133">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="80cee-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="80cee-134">3.請確定**停用所有警告**未核取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="80cee-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="80cee-135">4.請確定**將所有警告視為錯誤**未核取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="80cee-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="80cee-136">5.選取 **錯誤**從**通知**應該視為錯誤的警告相鄰的資料行。</span><span class="sxs-lookup"><span data-stu-id="80cee-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="80cee-137">範例</span><span class="sxs-lookup"><span data-stu-id="80cee-137">Example</span></span>  
 <span data-ttu-id="80cee-138">下列程式碼編譯`In.vb`和指示編譯器將會顯示錯誤，它會尋找每個警告的第一個相符項目。</span><span class="sxs-lookup"><span data-stu-id="80cee-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="80cee-139">範例</span><span class="sxs-lookup"><span data-stu-id="80cee-139">Example</span></span>  
 <span data-ttu-id="80cee-140">下列程式碼編譯`T2.vb`和未使用的本機變數 (42024) 警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="80cee-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="80cee-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80cee-141">See also</span></span>

- [<span data-ttu-id="80cee-142">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="80cee-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="80cee-143">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="80cee-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="80cee-144">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80cee-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
