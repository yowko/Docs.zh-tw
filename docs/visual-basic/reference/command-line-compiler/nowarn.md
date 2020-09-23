---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: cde96fff975a65d6303ee62e6a811bfd83d5ff97
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097679"
---
# <a name="-nowarn"></a><span data-ttu-id="3e499-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="3e499-102">-nowarn</span></span>

<span data-ttu-id="3e499-103">抑制編譯器產生警告的功能。</span><span class="sxs-lookup"><span data-stu-id="3e499-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e499-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e499-104">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3e499-105">引數</span><span class="sxs-lookup"><span data-stu-id="3e499-105">Arguments</span></span>  
  
|<span data-ttu-id="3e499-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="3e499-106">Term</span></span>|<span data-ttu-id="3e499-107">定義</span><span class="sxs-lookup"><span data-stu-id="3e499-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="3e499-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3e499-108">Optional.</span></span> <span data-ttu-id="3e499-109">編譯器應該隱藏的警告識別碼編號清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="3e499-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="3e499-110">如果未指定警告識別碼，則會隱藏所有警告。</span><span class="sxs-lookup"><span data-stu-id="3e499-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e499-111">備註</span><span class="sxs-lookup"><span data-stu-id="3e499-111">Remarks</span></span>  

 <span data-ttu-id="3e499-112">`-nowarn`選項會導致編譯器不會產生警告。</span><span class="sxs-lookup"><span data-stu-id="3e499-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="3e499-113">若要隱藏個別警告，請將警告識別碼提供給 `-nowarn` 冒號後面的選項。</span><span class="sxs-lookup"><span data-stu-id="3e499-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="3e499-114">以逗號分隔多個警告編號。</span><span class="sxs-lookup"><span data-stu-id="3e499-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="3e499-115">您只需要指定警告識別碼的數值部分。</span><span class="sxs-lookup"><span data-stu-id="3e499-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="3e499-116">例如，如果您想要隱藏 BC42024 （未使用之區域變數的警告），請指定 `-nowarn:42024` 。</span><span class="sxs-lookup"><span data-stu-id="3e499-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="3e499-117">如需有關警告識別碼的詳細資訊，請參閱設定 [Visual Basic 中的警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="3e499-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="3e499-118">在 Visual Studio 整合式開發環境中設定-nowarn</span><span class="sxs-lookup"><span data-stu-id="3e499-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="3e499-119">1. 在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="3e499-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3e499-120">按一下 [專案] 功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="3e499-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="3e499-121">2. 按一下 [ **編譯** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3e499-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="3e499-122">3. 選取 [ **停用所有警告** ] 核取方塊，以停用所有警告。</span><span class="sxs-lookup"><span data-stu-id="3e499-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="3e499-123">- 或 -</span><span class="sxs-lookup"><span data-stu-id="3e499-123">- or -</span></span><br />     <span data-ttu-id="3e499-124">若要停用特定警告，請在警告旁的下拉式清單中按一下 [ **無** ]。</span><span class="sxs-lookup"><span data-stu-id="3e499-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3e499-125">範例</span><span class="sxs-lookup"><span data-stu-id="3e499-125">Example</span></span>  

 <span data-ttu-id="3e499-126">下列程式碼 `T2.vb` 會進行編譯，而且不會顯示任何警告。</span><span class="sxs-lookup"><span data-stu-id="3e499-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="3e499-127">範例</span><span class="sxs-lookup"><span data-stu-id="3e499-127">Example</span></span>  

 <span data-ttu-id="3e499-128">下列 `T2.vb` 程式碼會進行編譯，而且不會顯示 (42024) 中未使用之區域變數的警告。</span><span class="sxs-lookup"><span data-stu-id="3e499-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e499-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e499-129">See also</span></span>

- [<span data-ttu-id="3e499-130">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="3e499-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3e499-131">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="3e499-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="3e499-132">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e499-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
