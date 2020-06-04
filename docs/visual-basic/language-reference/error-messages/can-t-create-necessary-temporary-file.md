---
title: 無法建立必要的暫存檔
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: 1a1464e0ac0d87bf9763efe63f2e09927a157a24
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415423"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="84a8e-102">無法建立必要的暫存檔</span><span class="sxs-lookup"><span data-stu-id="84a8e-102">Can't create necessary temporary file</span></span>
<span data-ttu-id="84a8e-103">磁片磁碟機已滿，其中包含 TEMP 環境變數所指定的目錄，或 TEMP 環境變數指定了無效或唯讀磁片磁碟機或目錄。</span><span class="sxs-lookup"><span data-stu-id="84a8e-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84a8e-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="84a8e-104">To correct this error</span></span>  
  
1. <span data-ttu-id="84a8e-105">刪除磁片磁碟機中的檔案（如果已滿）。</span><span class="sxs-lookup"><span data-stu-id="84a8e-105">Delete files from the drive, if full.</span></span>  
  
2. <span data-ttu-id="84a8e-106">請在 TEMP 環境變數中指定不同的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="84a8e-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3. <span data-ttu-id="84a8e-107">請為 TEMP 環境變數指定有效的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="84a8e-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4. <span data-ttu-id="84a8e-108">從目前指定的磁片磁碟機或目錄移除唯讀限制。</span><span class="sxs-lookup"><span data-stu-id="84a8e-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a8e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84a8e-109">See also</span></span>

- [<span data-ttu-id="84a8e-110">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="84a8e-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
