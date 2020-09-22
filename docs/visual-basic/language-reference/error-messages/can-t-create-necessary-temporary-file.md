---
title: 無法建立必要的暫存檔
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: c6d8e471796a0fb745289df8b3d1b156265949ca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874669"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="c65b6-102">無法建立必要的暫存檔</span><span class="sxs-lookup"><span data-stu-id="c65b6-102">Can't create necessary temporary file</span></span>

<span data-ttu-id="c65b6-103">磁片磁碟機已滿，內含 TEMP 環境變數所指定的目錄，或 TEMP 環境變數指定了無效或唯讀的磁片磁碟機或目錄。</span><span class="sxs-lookup"><span data-stu-id="c65b6-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c65b6-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c65b6-104">To correct this error</span></span>  
  
1. <span data-ttu-id="c65b6-105">從磁片磁碟機刪除檔案（如果已滿）。</span><span class="sxs-lookup"><span data-stu-id="c65b6-105">Delete files from the drive, if full.</span></span>  
  
2. <span data-ttu-id="c65b6-106">請在 TEMP 環境變數中指定不同的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="c65b6-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3. <span data-ttu-id="c65b6-107">請為 TEMP 環境變數指定有效的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="c65b6-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4. <span data-ttu-id="c65b6-108">從目前指定的磁片磁碟機或目錄移除唯讀的限制。</span><span class="sxs-lookup"><span data-stu-id="c65b6-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65b6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c65b6-109">See also</span></span>

- [<span data-ttu-id="c65b6-110">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="c65b6-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
