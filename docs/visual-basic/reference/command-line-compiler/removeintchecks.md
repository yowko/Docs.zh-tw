---
title: "/removeintchecks |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
dev_langs:
- VB
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: 14
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
ms.openlocfilehash: 25f67774238c6e9a6b3a2c50b3702e43d5a6374c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="removeintchecks"></a><span data-ttu-id="4d5e0-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="4d5e0-102">/removeintchecks</span></span>
<span data-ttu-id="4d5e0-103">開啟溢位錯誤檢查適用於整數作業開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d5e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d5e0-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d5e0-105">引數</span><span class="sxs-lookup"><span data-stu-id="4d5e0-105">Arguments</span></span>  
  
|<span data-ttu-id="4d5e0-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="4d5e0-106">Term</span></span>|<span data-ttu-id="4d5e0-107">定義</span><span class="sxs-lookup"><span data-stu-id="4d5e0-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="4d5e0-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="4d5e0-108">`+` &#124; `-`</span></span>|<span data-ttu-id="4d5e0-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-109">Optional.</span></span> <span data-ttu-id="4d5e0-110">`/removeintchecks-`選項會使編譯器檢查所有的整數計算的溢位錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="4d5e0-111">預設為 `/removeintchecks-`。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="4d5e0-112">指定`/removeintchecks`或`/removeintchecks+`防止錯誤檢查，並能更快的整數計算。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="4d5e0-113">不過，如果沒有錯誤檢查，以及如果資料型別容量溢位，可能會不正確的結果儲存而不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="4d5e0-114">在 Visual Studio 中設定 /removeintchecks 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="4d5e0-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="4d5e0-115">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4d5e0-116">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="4d5e0-117">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="4d5e0-118">2.按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="4d5e0-119">3.按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="4d5e0-120">4.修改的值**移除整數的溢位檢查**方塊。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4d5e0-121">範例</span><span class="sxs-lookup"><span data-stu-id="4d5e0-121">Example</span></span>  
 <span data-ttu-id="4d5e0-122">下列程式碼編譯`Test.vb`並關閉整數溢位錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="4d5e0-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d5e0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d5e0-123">See Also</span></span>  
 <span data-ttu-id="4d5e0-124">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="4d5e0-124">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="4d5e0-125"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="4d5e0-125"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
