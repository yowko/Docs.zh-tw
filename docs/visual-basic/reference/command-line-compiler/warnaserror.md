---
title: "/warnaserror (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8ed72415a75860b34e37c2bf4fc686cdae37f69e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="warnaserror-visual-basic"></a><span data-ttu-id="40d2a-102">/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40d2a-102">/warnaserror (Visual Basic)</span></span>
<span data-ttu-id="40d2a-103">讓編譯器將第一個出現的警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="40d2a-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40d2a-104">語法</span><span class="sxs-lookup"><span data-stu-id="40d2a-104">Syntax</span></span>  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="40d2a-105">引數</span><span class="sxs-lookup"><span data-stu-id="40d2a-105">Arguments</span></span>  
  
|<span data-ttu-id="40d2a-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="40d2a-106">Term</span></span>|<span data-ttu-id="40d2a-107">定義</span><span class="sxs-lookup"><span data-stu-id="40d2a-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="40d2a-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="40d2a-108">+ &#124; -</span></span>|<span data-ttu-id="40d2a-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="40d2a-109">Optional.</span></span> <span data-ttu-id="40d2a-110">根據預設，`/warnaserror-`是生效; 警告不會防止編譯器產生的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="40d2a-110">By default, `/warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="40d2a-111">`/warnaserror`是相同的選項為`/warnaserror+`，會將警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="40d2a-111">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="40d2a-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="40d2a-112">Optional.</span></span> <span data-ttu-id="40d2a-113">逗號分隔清單的警告編號的數字的`/warnaserror`選項會套用。</span><span class="sxs-lookup"><span data-stu-id="40d2a-113">Comma-delimited list of the warning ID numbers to which the `/warnaserror` option applies.</span></span> <span data-ttu-id="40d2a-114">如果沒有警告指定 ID，`/warnaserror`選項會套用至所有警告。</span><span class="sxs-lookup"><span data-stu-id="40d2a-114">If no warning ID is specified, the `/warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40d2a-115">備註</span><span class="sxs-lookup"><span data-stu-id="40d2a-115">Remarks</span></span>  
 <span data-ttu-id="40d2a-116">`/warnaserror`選項會將所有警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="40d2a-116">The `/warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="40d2a-117">原本為警告而是會回報為錯誤報告的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="40d2a-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="40d2a-118">編譯器會報告為警告的相同警告後續出現項目。</span><span class="sxs-lookup"><span data-stu-id="40d2a-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="40d2a-119">根據預設，`/warnaserror-`有效，會將只是告知性警告。</span><span class="sxs-lookup"><span data-stu-id="40d2a-119">By default, `/warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="40d2a-120">`/warnaserror`是相同的選項為`/warnaserror+`，會將警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="40d2a-120">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="40d2a-121">如果您想只有少數的特定警告視為錯誤，您可以指定要視為錯誤的警告編號的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="40d2a-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40d2a-122">`/warnaserror`選項不會控制如何顯示警告。</span><span class="sxs-lookup"><span data-stu-id="40d2a-122">The `/warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="40d2a-123">使用[/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)選項來停用警告。</span><span class="sxs-lookup"><span data-stu-id="40d2a-123">Use the [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="40d2a-124">若要設定所有警告視為錯誤，在 Visual Studio IDE 中 /warnaserror</span><span class="sxs-lookup"><span data-stu-id="40d2a-124">To set /warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="40d2a-125">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="40d2a-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="40d2a-126">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="40d2a-126">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="40d2a-127">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="40d2a-127">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="40d2a-128">2.按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="40d2a-128">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="40d2a-129">3.請確定**停用所有警告**未核取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="40d2a-129">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="40d2a-130">4.檢查**將所有警告視為錯誤**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="40d2a-130">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="40d2a-131">若要設定特定的警告視為錯誤，在 Visual Studio IDE 中 /warnaserror</span><span class="sxs-lookup"><span data-stu-id="40d2a-131">To set /warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="40d2a-132">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="40d2a-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="40d2a-133">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="40d2a-133">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="40d2a-134">2.按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="40d2a-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="40d2a-135">3.請確定**停用所有警告**未核取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="40d2a-135">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="40d2a-136">4.請確定**將所有警告視為錯誤**未核取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="40d2a-136">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="40d2a-137">5.選取**錯誤**從**通知**應該視為錯誤的警告旁邊的資料行。</span><span class="sxs-lookup"><span data-stu-id="40d2a-137">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="40d2a-138">範例</span><span class="sxs-lookup"><span data-stu-id="40d2a-138">Example</span></span>  
 <span data-ttu-id="40d2a-139">下列程式碼編譯`In.vb`，並指示編譯器將會顯示錯誤，它會尋找每個警告的第一個相符項目。</span><span class="sxs-lookup"><span data-stu-id="40d2a-139">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="40d2a-140">範例</span><span class="sxs-lookup"><span data-stu-id="40d2a-140">Example</span></span>  
 <span data-ttu-id="40d2a-141">下列程式碼編譯`T2.vb`和未使用區域變數 (42024) 警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="40d2a-141">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="40d2a-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40d2a-142">See Also</span></span>  
 <span data-ttu-id="40d2a-143">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="40d2a-143">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="40d2a-144"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="40d2a-144"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="40d2a-145"> [在 Visual Basic 中設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="40d2a-145"> [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)</span></span>
