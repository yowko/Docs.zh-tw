---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 4382ec8feda2df1e83fd2fdc509abb66984e501f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937245"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="670eb-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="670eb-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="670eb-103">使編譯器將第一次出現的警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="670eb-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="670eb-104">語法</span><span class="sxs-lookup"><span data-stu-id="670eb-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="670eb-105">引數</span><span class="sxs-lookup"><span data-stu-id="670eb-105">Arguments</span></span>  
  
|<span data-ttu-id="670eb-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="670eb-106">Term</span></span>|<span data-ttu-id="670eb-107">定義</span><span class="sxs-lookup"><span data-stu-id="670eb-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="670eb-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="670eb-108">+ &#124; -</span></span>|<span data-ttu-id="670eb-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="670eb-109">Optional.</span></span> <span data-ttu-id="670eb-110">根據預設, `-warnaserror-`會生效; 警告不會防止編譯器產生輸出檔。</span><span class="sxs-lookup"><span data-stu-id="670eb-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="670eb-111">選項 (與`-warnaserror+`相同) 會導致警告視為錯誤。 `-warnaserror`</span><span class="sxs-lookup"><span data-stu-id="670eb-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="670eb-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="670eb-112">Optional.</span></span> <span data-ttu-id="670eb-113">以逗號分隔的清單, 其中列出`-warnaserror`選項所套用的警告識別碼編號。</span><span class="sxs-lookup"><span data-stu-id="670eb-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="670eb-114">如果未指定警告識別碼, 此`-warnaserror`選項會套用至所有警告。</span><span class="sxs-lookup"><span data-stu-id="670eb-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="670eb-115">備註</span><span class="sxs-lookup"><span data-stu-id="670eb-115">Remarks</span></span>  
 <span data-ttu-id="670eb-116">此`-warnaserror`選項會將所有警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="670eb-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="670eb-117">通常會回報為警告的任何訊息會改為回報為錯誤。</span><span class="sxs-lookup"><span data-stu-id="670eb-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="670eb-118">編譯器會報告與警告相同的後續出現的警告。</span><span class="sxs-lookup"><span data-stu-id="670eb-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="670eb-119">根據預設, `-warnaserror-`會生效, 這會導致警告僅供參考。</span><span class="sxs-lookup"><span data-stu-id="670eb-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="670eb-120">選項 (與`-warnaserror+`相同) 會導致警告視為錯誤。 `-warnaserror`</span><span class="sxs-lookup"><span data-stu-id="670eb-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="670eb-121">如果您只想要將幾個特定警告視為錯誤, 您可以指定以逗號分隔的警告編號清單來視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="670eb-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="670eb-122">`-warnaserror`選項不會控制警告的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="670eb-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="670eb-123">使用[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)選項可停用警告。</span><span class="sxs-lookup"><span data-stu-id="670eb-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="670eb-124">若要設定-warnaserror 以將所有警告視為錯誤在 Visual Studio IDE 中</span><span class="sxs-lookup"><span data-stu-id="670eb-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="670eb-125">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="670eb-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="670eb-126">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="670eb-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="670eb-127">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="670eb-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="670eb-128">3.請確定未核取 [**停用所有警告**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="670eb-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="670eb-129">4.勾選 [將**所有警告視為錯誤**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="670eb-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="670eb-130">若要設定-warnaserror 以將特定警告視為 Visual Studio IDE 中的錯誤</span><span class="sxs-lookup"><span data-stu-id="670eb-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="670eb-131">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="670eb-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="670eb-132">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="670eb-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="670eb-133">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="670eb-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="670eb-134">3.請確定未核取 [**停用所有警告**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="670eb-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="670eb-135">4.請確定未核取 [將**所有警告視為錯誤**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="670eb-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="670eb-136">5.從應視為錯誤的警告旁的**通知**資料行中, 選取 [**錯誤**]。</span><span class="sxs-lookup"><span data-stu-id="670eb-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="670eb-137">範例</span><span class="sxs-lookup"><span data-stu-id="670eb-137">Example</span></span>  
 <span data-ttu-id="670eb-138">下列程式碼會`In.vb`編譯並指示編譯器在第一次出現的每個警告發現時顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="670eb-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="670eb-139">範例</span><span class="sxs-lookup"><span data-stu-id="670eb-139">Example</span></span>  
 <span data-ttu-id="670eb-140">下列程式碼會`T2.vb`將未使用的區域變數 (42024) 的警告編譯並視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="670eb-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="670eb-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="670eb-141">See also</span></span>

- [<span data-ttu-id="670eb-142">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="670eb-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="670eb-143">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="670eb-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="670eb-144">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="670eb-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
