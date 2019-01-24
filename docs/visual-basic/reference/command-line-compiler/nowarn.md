---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: eff367fd6cc14c655f0c623731e334054233b0a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744306"
---
# <a name="-nowarn"></a><span data-ttu-id="74eb1-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="74eb1-102">-nowarn</span></span>
<span data-ttu-id="74eb1-103">抑制編譯器產生警告的功能。</span><span class="sxs-lookup"><span data-stu-id="74eb1-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74eb1-104">語法</span><span class="sxs-lookup"><span data-stu-id="74eb1-104">Syntax</span></span>  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="74eb1-105">引數</span><span class="sxs-lookup"><span data-stu-id="74eb1-105">Arguments</span></span>  
  
|<span data-ttu-id="74eb1-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="74eb1-106">Term</span></span>|<span data-ttu-id="74eb1-107">定義</span><span class="sxs-lookup"><span data-stu-id="74eb1-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="74eb1-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="74eb1-108">Optional.</span></span> <span data-ttu-id="74eb1-109">應該隱藏編譯器警告 ID 編號的逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="74eb1-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="74eb1-110">如果未指定警告識別碼，則會隱藏所有警告。</span><span class="sxs-lookup"><span data-stu-id="74eb1-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74eb1-111">備註</span><span class="sxs-lookup"><span data-stu-id="74eb1-111">Remarks</span></span>  
 <span data-ttu-id="74eb1-112">`-nowarn`選項可讓編譯器將不會產生警告。</span><span class="sxs-lookup"><span data-stu-id="74eb1-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="74eb1-113">若要隱藏個別的警告，提供警告識別碼`-nowarn`冒號之後的選項。</span><span class="sxs-lookup"><span data-stu-id="74eb1-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="74eb1-114">以逗號分隔多個警告編號。</span><span class="sxs-lookup"><span data-stu-id="74eb1-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="74eb1-115">您需要指定警告識別項的數值部分。</span><span class="sxs-lookup"><span data-stu-id="74eb1-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="74eb1-116">例如，如果您想要隱藏 BC42024，未使用的區域變數的警告指定`-nowarn:42024`。</span><span class="sxs-lookup"><span data-stu-id="74eb1-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="74eb1-117">如需有關的警告 ID 編號的詳細資訊，請參閱[Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="74eb1-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="74eb1-118">若要在 Visual Studio 整合式的開發環境中設定-nowarn</span><span class="sxs-lookup"><span data-stu-id="74eb1-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="74eb1-119">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="74eb1-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="74eb1-120">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="74eb1-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="74eb1-121">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="74eb1-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="74eb1-122">3.選取 **停用所有警告**核取方塊以停都用所有警告。</span><span class="sxs-lookup"><span data-stu-id="74eb1-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="74eb1-123">-或-</span><span class="sxs-lookup"><span data-stu-id="74eb1-123">- or -</span></span><br />     <span data-ttu-id="74eb1-124">若要停用特定警告，請按一下**無**從下拉式清單中相鄰的警告。</span><span class="sxs-lookup"><span data-stu-id="74eb1-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="74eb1-125">範例</span><span class="sxs-lookup"><span data-stu-id="74eb1-125">Example</span></span>  
 <span data-ttu-id="74eb1-126">下列程式碼編譯`T2.vb`並不會顯示任何警告。</span><span class="sxs-lookup"><span data-stu-id="74eb1-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="74eb1-127">範例</span><span class="sxs-lookup"><span data-stu-id="74eb1-127">Example</span></span>  
 <span data-ttu-id="74eb1-128">下列程式碼編譯`T2.vb`並不會顯示未使用的本機變數 (42024) 的警告。</span><span class="sxs-lookup"><span data-stu-id="74eb1-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="74eb1-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74eb1-129">See also</span></span>
- [<span data-ttu-id="74eb1-130">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="74eb1-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="74eb1-131">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="74eb1-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="74eb1-132">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="74eb1-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
