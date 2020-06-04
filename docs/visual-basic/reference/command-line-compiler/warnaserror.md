---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 94a8b43a891df9837925869e17fac4536a995264
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414268"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="6662e-102">-warnaserror （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6662e-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="6662e-103">使編譯器將第一次出現的警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="6662e-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6662e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6662e-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6662e-105">引數</span><span class="sxs-lookup"><span data-stu-id="6662e-105">Arguments</span></span>  
  
|<span data-ttu-id="6662e-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="6662e-106">Term</span></span>|<span data-ttu-id="6662e-107">定義</span><span class="sxs-lookup"><span data-stu-id="6662e-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="6662e-108">+ &#124;-</span><span class="sxs-lookup"><span data-stu-id="6662e-108">+ &#124; -</span></span>|<span data-ttu-id="6662e-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6662e-109">Optional.</span></span> <span data-ttu-id="6662e-110">根據預設， `-warnaserror-` 會生效; 警告不會防止編譯器產生輸出檔。</span><span class="sxs-lookup"><span data-stu-id="6662e-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="6662e-111">`-warnaserror`選項（與相同 `-warnaserror+` ）會導致警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="6662e-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="6662e-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6662e-112">Optional.</span></span> <span data-ttu-id="6662e-113">以逗號分隔的清單，其中列出選項所套用的警告識別碼編號 `-warnaserror` 。</span><span class="sxs-lookup"><span data-stu-id="6662e-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="6662e-114">如果未指定警告識別碼，此 `-warnaserror` 選項會套用至所有警告。</span><span class="sxs-lookup"><span data-stu-id="6662e-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6662e-115">備註</span><span class="sxs-lookup"><span data-stu-id="6662e-115">Remarks</span></span>  
 <span data-ttu-id="6662e-116">此 `-warnaserror` 選項會將所有警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="6662e-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="6662e-117">通常會回報為警告的任何訊息會改為回報為錯誤。</span><span class="sxs-lookup"><span data-stu-id="6662e-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="6662e-118">編譯器會報告與警告相同的後續出現的警告。</span><span class="sxs-lookup"><span data-stu-id="6662e-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="6662e-119">根據預設， `-warnaserror-` 會生效，這會導致警告僅供參考。</span><span class="sxs-lookup"><span data-stu-id="6662e-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="6662e-120">`-warnaserror`選項（與相同 `-warnaserror+` ）會導致警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="6662e-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="6662e-121">如果您只想要將幾個特定警告視為錯誤，您可以指定以逗號分隔的警告編號清單來視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="6662e-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6662e-122">`-warnaserror`選項不會控制警告的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="6662e-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="6662e-123">使用[-nowarn](nowarn.md)選項可停用警告。</span><span class="sxs-lookup"><span data-stu-id="6662e-123">Use the [-nowarn](nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="6662e-124">若要設定-warnaserror 以將所有警告視為錯誤在 Visual Studio IDE 中</span><span class="sxs-lookup"><span data-stu-id="6662e-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="6662e-125">1. 在**方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="6662e-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6662e-126">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6662e-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="6662e-127">2. 按一下 [**編譯**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6662e-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="6662e-128">3. 請確定未核取 [**停用所有警告**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6662e-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="6662e-129">4. 勾選 [將**所有警告視為錯誤**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6662e-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="6662e-130">若要設定-warnaserror 以將特定警告視為 Visual Studio IDE 中的錯誤</span><span class="sxs-lookup"><span data-stu-id="6662e-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="6662e-131">1. 在**方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="6662e-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6662e-132">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6662e-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="6662e-133">2. 按一下 [**編譯**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6662e-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="6662e-134">3. 請確定未核取 [**停用所有警告**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6662e-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="6662e-135">4. 請確定未核取 [將**所有警告視為錯誤**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6662e-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="6662e-136">5. 從應視為錯誤的警告旁的**通知**資料行中，選取 [**錯誤**]。</span><span class="sxs-lookup"><span data-stu-id="6662e-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6662e-137">範例</span><span class="sxs-lookup"><span data-stu-id="6662e-137">Example</span></span>  
 <span data-ttu-id="6662e-138">下列程式碼 `In.vb` 會編譯並指示編譯器在第一次出現的每個警告發現時顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="6662e-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="6662e-139">範例</span><span class="sxs-lookup"><span data-stu-id="6662e-139">Example</span></span>  
 <span data-ttu-id="6662e-140">下列程式碼會將 `T2.vb` 未使用的區域變數（42024）的警告編譯並視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="6662e-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6662e-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6662e-141">See also</span></span>

- [<span data-ttu-id="6662e-142">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="6662e-142">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="6662e-143">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="6662e-143">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="6662e-144">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6662e-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
