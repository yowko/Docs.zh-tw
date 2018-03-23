---
title: -removeintchecks
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a14ffaca6e61c6e3306f8ff58de441e2ba2ade
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-removeintchecks"></a><span data-ttu-id="fce40-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="fce40-102">-removeintchecks</span></span>
<span data-ttu-id="fce40-103">開啟溢位錯誤檢查適用於整數作業開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="fce40-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fce40-104">語法</span><span class="sxs-lookup"><span data-stu-id="fce40-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="fce40-105">引數</span><span class="sxs-lookup"><span data-stu-id="fce40-105">Arguments</span></span>  
  
|<span data-ttu-id="fce40-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="fce40-106">Term</span></span>|<span data-ttu-id="fce40-107">定義</span><span class="sxs-lookup"><span data-stu-id="fce40-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="fce40-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="fce40-108">`+` &#124; `-`</span></span>|<span data-ttu-id="fce40-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="fce40-109">Optional.</span></span> <span data-ttu-id="fce40-110">`-removeintchecks-`選項讓編譯器將檢查所有整數計算的溢位錯誤。</span><span class="sxs-lookup"><span data-stu-id="fce40-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="fce40-111">預設值為 `-removeintchecks-`。</span><span class="sxs-lookup"><span data-stu-id="fce40-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="fce40-112">指定`-removeintchecks`或`-removeintchecks+`會阻止錯誤檢查，而且可以進行更快速的整數計算。</span><span class="sxs-lookup"><span data-stu-id="fce40-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="fce40-113">不過，如果沒有錯誤檢查，和不正確的結果而不會引發錯誤，如果資料型別容量溢位，可能會儲存。</span><span class="sxs-lookup"><span data-stu-id="fce40-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="fce40-114">在 Visual Studio 整合式的開發環境中設定-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="fce40-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="fce40-115">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="fce40-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fce40-116">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="fce40-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="fce40-117">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fce40-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="fce40-118">3.按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fce40-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="fce40-119">4.值修改為**移除整數溢位檢查**方塊。</span><span class="sxs-lookup"><span data-stu-id="fce40-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fce40-120">範例</span><span class="sxs-lookup"><span data-stu-id="fce40-120">Example</span></span>  
 <span data-ttu-id="fce40-121">下列程式碼編譯`Test.vb`並關閉整數溢位錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="fce40-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fce40-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fce40-122">See Also</span></span>  
 [<span data-ttu-id="fce40-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="fce40-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="fce40-124">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="fce40-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
