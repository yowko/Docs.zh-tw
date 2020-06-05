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
ms.openlocfilehash: ec4722cb7088819dae95ca1b7cbc1469d957a7aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400470"
---
# <a name="-removeintchecks"></a><span data-ttu-id="ff045-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="ff045-102">-removeintchecks</span></span>
<span data-ttu-id="ff045-103">開啟或關閉整數作業的錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="ff045-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff045-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff045-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ff045-105">引數</span><span class="sxs-lookup"><span data-stu-id="ff045-105">Arguments</span></span>  
  
|<span data-ttu-id="ff045-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="ff045-106">Term</span></span>|<span data-ttu-id="ff045-107">定義</span><span class="sxs-lookup"><span data-stu-id="ff045-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="ff045-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ff045-108">`+` &#124; `-`</span></span>|<span data-ttu-id="ff045-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="ff045-109">Optional.</span></span> <span data-ttu-id="ff045-110">`-removeintchecks-`選項會使編譯器檢查溢位錯誤的所有整數計算。</span><span class="sxs-lookup"><span data-stu-id="ff045-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="ff045-111">預設值為 `-removeintchecks-`。</span><span class="sxs-lookup"><span data-stu-id="ff045-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="ff045-112">指定 `-removeintchecks` 或 `-removeintchecks+` 可防止錯誤檢查，並可讓整數計算更快。</span><span class="sxs-lookup"><span data-stu-id="ff045-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="ff045-113">不過，如果沒有錯誤檢查，而且資料類型容量溢位，則可能會儲存不正確的結果，而不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="ff045-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="ff045-114">在 Visual Studio 的整合式開發環境中設定-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="ff045-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ff045-115">1. 在**方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="ff045-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ff045-116">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ff045-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ff045-117">2. 按一下 [**編譯**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ff045-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="ff045-118">3. 按一下 [ **Advanced** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ff045-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="ff045-119">4. 修改 [**移除整數溢位檢查**] 核取方塊的值。</span><span class="sxs-lookup"><span data-stu-id="ff045-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ff045-120">範例</span><span class="sxs-lookup"><span data-stu-id="ff045-120">Example</span></span>  
 <span data-ttu-id="ff045-121">下列程式碼會編譯 `Test.vb` 並關閉整數溢位-錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="ff045-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff045-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff045-122">See also</span></span>

- [<span data-ttu-id="ff045-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="ff045-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ff045-124">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="ff045-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
