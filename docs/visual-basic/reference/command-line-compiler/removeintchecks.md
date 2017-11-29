---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e765f0007eea8e196b1a1b3b55b969c5b074b52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="removeintchecks"></a><span data-ttu-id="d65c1-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="d65c1-102">/removeintchecks</span></span>
<span data-ttu-id="d65c1-103">開啟溢位錯誤檢查適用於整數作業開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="d65c1-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d65c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="d65c1-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d65c1-105">引數</span><span class="sxs-lookup"><span data-stu-id="d65c1-105">Arguments</span></span>  
  
|<span data-ttu-id="d65c1-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="d65c1-106">Term</span></span>|<span data-ttu-id="d65c1-107">定義</span><span class="sxs-lookup"><span data-stu-id="d65c1-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d65c1-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d65c1-108">`+` &#124; `-`</span></span>|<span data-ttu-id="d65c1-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="d65c1-109">Optional.</span></span> <span data-ttu-id="d65c1-110">`/removeintchecks-`選項讓編譯器將檢查所有整數計算的溢位錯誤。</span><span class="sxs-lookup"><span data-stu-id="d65c1-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="d65c1-111">預設為 `/removeintchecks-`。</span><span class="sxs-lookup"><span data-stu-id="d65c1-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="d65c1-112">指定`/removeintchecks`或`/removeintchecks+`會阻止錯誤檢查，而且可以進行更快速的整數計算。</span><span class="sxs-lookup"><span data-stu-id="d65c1-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="d65c1-113">不過，如果沒有錯誤檢查，和不正確的結果而不會引發錯誤，如果資料型別容量溢位，可能會儲存。</span><span class="sxs-lookup"><span data-stu-id="d65c1-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="d65c1-114">在 Visual Studio 中設定 /removeintchecks 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="d65c1-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d65c1-115">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="d65c1-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d65c1-116">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="d65c1-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="d65c1-117">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="d65c1-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="d65c1-118">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d65c1-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d65c1-119">3.按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d65c1-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="d65c1-120">4.值修改為**移除整數溢位檢查**方塊。</span><span class="sxs-lookup"><span data-stu-id="d65c1-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d65c1-121">範例</span><span class="sxs-lookup"><span data-stu-id="d65c1-121">Example</span></span>  
 <span data-ttu-id="d65c1-122">下列程式碼編譯`Test.vb`並關閉整數溢位錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="d65c1-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d65c1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d65c1-123">See Also</span></span>  
 [<span data-ttu-id="d65c1-124">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="d65c1-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d65c1-125">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="d65c1-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
