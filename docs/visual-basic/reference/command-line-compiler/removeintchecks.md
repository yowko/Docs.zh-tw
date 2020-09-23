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
ms.openlocfilehash: ce1f24f25ea58cb6ddc2f5c582b6103d8f18d922
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085161"
---
# <a name="-removeintchecks"></a><span data-ttu-id="f91ed-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="f91ed-102">-removeintchecks</span></span>

<span data-ttu-id="f91ed-103">開啟或關閉整數作業的溢位錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="f91ed-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91ed-104">語法</span><span class="sxs-lookup"><span data-stu-id="f91ed-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f91ed-105">引數</span><span class="sxs-lookup"><span data-stu-id="f91ed-105">Arguments</span></span>  
  
|<span data-ttu-id="f91ed-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="f91ed-106">Term</span></span>|<span data-ttu-id="f91ed-107">定義</span><span class="sxs-lookup"><span data-stu-id="f91ed-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="f91ed-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f91ed-108">`+` &#124; `-`</span></span>|<span data-ttu-id="f91ed-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f91ed-109">Optional.</span></span> <span data-ttu-id="f91ed-110">`-removeintchecks-`選項會讓編譯器檢查所有的整數計算是否有溢位錯誤。</span><span class="sxs-lookup"><span data-stu-id="f91ed-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="f91ed-111">預設值為 `-removeintchecks-`。</span><span class="sxs-lookup"><span data-stu-id="f91ed-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="f91ed-112">指定 `-removeintchecks` 或 `-removeintchecks+` 防止錯誤檢查，而且可以更快速地進行整數計算。</span><span class="sxs-lookup"><span data-stu-id="f91ed-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="f91ed-113">但是，如果沒有錯誤檢查，而且資料類型的容量溢位，則可能會儲存不正確的結果，而不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="f91ed-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="f91ed-114">在 Visual Studio 整合式開發環境中設定-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="f91ed-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f91ed-115">1. 在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="f91ed-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f91ed-116">按一下 [專案] 功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="f91ed-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f91ed-117">2. 按一下 [ **編譯** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f91ed-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f91ed-118">3. 按一下 [ **Advanced** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f91ed-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="f91ed-119">4. 修改 [ **移除整數溢位檢查** ] 方塊的值。</span><span class="sxs-lookup"><span data-stu-id="f91ed-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f91ed-120">範例</span><span class="sxs-lookup"><span data-stu-id="f91ed-120">Example</span></span>  

 <span data-ttu-id="f91ed-121">下列程式碼會編譯 `Test.vb` 並關閉整數溢位錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="f91ed-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f91ed-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f91ed-122">See also</span></span>

- [<span data-ttu-id="f91ed-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="f91ed-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f91ed-124">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="f91ed-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
