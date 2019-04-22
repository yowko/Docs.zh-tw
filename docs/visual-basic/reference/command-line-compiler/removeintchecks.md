---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: c086a031d5cef4563a6769e7683dcb1110b8fe49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822722"
---
# <a name="-removeintchecks"></a><span data-ttu-id="12a11-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="12a11-102">-removeintchecks</span></span>
<span data-ttu-id="12a11-103">會檢查開啟或關閉的整數運算溢位錯誤。</span><span class="sxs-lookup"><span data-stu-id="12a11-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a11-104">語法</span><span class="sxs-lookup"><span data-stu-id="12a11-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="12a11-105">引數</span><span class="sxs-lookup"><span data-stu-id="12a11-105">Arguments</span></span>  
  
|<span data-ttu-id="12a11-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="12a11-106">Term</span></span>|<span data-ttu-id="12a11-107">定義</span><span class="sxs-lookup"><span data-stu-id="12a11-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="12a11-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="12a11-108">`+` &#124; `-`</span></span>|<span data-ttu-id="12a11-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="12a11-109">Optional.</span></span> <span data-ttu-id="12a11-110">`-removeintchecks-`選項可讓編譯器檢查溢位錯誤的所有整數計算。</span><span class="sxs-lookup"><span data-stu-id="12a11-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="12a11-111">預設為 `-removeintchecks-`。</span><span class="sxs-lookup"><span data-stu-id="12a11-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="12a11-112">指定`-removeintchecks`或`-removeintchecks+`可防止錯誤檢查，並能更快速的整數計算。</span><span class="sxs-lookup"><span data-stu-id="12a11-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="12a11-113">不過，如果沒有錯誤檢查，以及如果資料型別容量溢位，可能會不正確的結果儲存而不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="12a11-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="12a11-114">若要在 Visual Studio 整合式的開發環境中設定-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="12a11-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="12a11-115">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="12a11-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="12a11-116">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="12a11-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="12a11-117">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="12a11-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="12a11-118">3.按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="12a11-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="12a11-119">4.修改的值**移除整數溢位檢查** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="12a11-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="12a11-120">範例</span><span class="sxs-lookup"><span data-stu-id="12a11-120">Example</span></span>  
 <span data-ttu-id="12a11-121">下列程式碼編譯`Test.vb`並關閉整數溢位錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="12a11-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="12a11-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12a11-122">See also</span></span>

- [<span data-ttu-id="12a11-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="12a11-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="12a11-124">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="12a11-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
