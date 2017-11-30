---
title: /nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8da27ea2f9f0a4d370928d70cda1a796b822d97c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn"></a><span data-ttu-id="a9516-102">/nowarn</span><span class="sxs-lookup"><span data-stu-id="a9516-102">/nowarn</span></span>
<span data-ttu-id="a9516-103">抑制編譯器產生警告的功能。</span><span class="sxs-lookup"><span data-stu-id="a9516-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9516-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9516-104">Syntax</span></span>  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a9516-105">引數</span><span class="sxs-lookup"><span data-stu-id="a9516-105">Arguments</span></span>  
  
|<span data-ttu-id="a9516-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="a9516-106">Term</span></span>|<span data-ttu-id="a9516-107">定義</span><span class="sxs-lookup"><span data-stu-id="a9516-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="a9516-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a9516-108">Optional.</span></span> <span data-ttu-id="a9516-109">編譯器不會顯示警告 ID 編號的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="a9516-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="a9516-110">如果未指定警告 Id，則會隱藏所有警告。</span><span class="sxs-lookup"><span data-stu-id="a9516-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9516-111">備註</span><span class="sxs-lookup"><span data-stu-id="a9516-111">Remarks</span></span>  
 <span data-ttu-id="a9516-112">`/nowarn`選項讓編譯器將不會產生警告。</span><span class="sxs-lookup"><span data-stu-id="a9516-112">The `/nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="a9516-113">若要隱藏個別的警告，提供警告識別碼，`/nowarn`冒號之後的選項。</span><span class="sxs-lookup"><span data-stu-id="a9516-113">To suppress an individual warning, supply the warning ID to the `/nowarn` option following the colon.</span></span> <span data-ttu-id="a9516-114">以逗號分隔多個警告編號。</span><span class="sxs-lookup"><span data-stu-id="a9516-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="a9516-115">您需要指定警告識別項的數字部分。</span><span class="sxs-lookup"><span data-stu-id="a9516-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="a9516-116">例如，如果您想要隱藏 BC42024，未使用的區域變數，警告指定`/nowarn:42024`。</span><span class="sxs-lookup"><span data-stu-id="a9516-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `/nowarn:42024`.</span></span>  
  
 <span data-ttu-id="a9516-117">如需有關的警告 ID 編號的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="a9516-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="a9516-118">在 Visual Studio 中設定 /nowarn 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="a9516-118">To set /nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="a9516-119">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="a9516-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a9516-120">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="a9516-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="a9516-121">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="a9516-121">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="a9516-122">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a9516-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="a9516-123">3.選取**停用所有警告**核取方塊可停都用所有警告。</span><span class="sxs-lookup"><span data-stu-id="a9516-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="a9516-124">-或-</span><span class="sxs-lookup"><span data-stu-id="a9516-124">- or -</span></span><br />     <span data-ttu-id="a9516-125">若要停用特定警告，請按一下**無**警告相鄰的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="a9516-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a9516-126">範例</span><span class="sxs-lookup"><span data-stu-id="a9516-126">Example</span></span>  
 <span data-ttu-id="a9516-127">下列程式碼編譯`T2.vb`並不會顯示任何警告。</span><span class="sxs-lookup"><span data-stu-id="a9516-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="a9516-128">範例</span><span class="sxs-lookup"><span data-stu-id="a9516-128">Example</span></span>  
 <span data-ttu-id="a9516-129">下列程式碼編譯`T2.vb`並不會顯示未使用的區域變數 (42024) 的警告。</span><span class="sxs-lookup"><span data-stu-id="a9516-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9516-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9516-130">See Also</span></span>  
 [<span data-ttu-id="a9516-131">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="a9516-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a9516-132">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="a9516-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="a9516-133">在 Visual Basic 中設定警告</span><span class="sxs-lookup"><span data-stu-id="a9516-133">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
