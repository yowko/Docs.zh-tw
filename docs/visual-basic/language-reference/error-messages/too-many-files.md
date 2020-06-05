---
title: 檔案太多
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: 38d39ad20f350137d714ae5d09db5d2204b83621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362796"
---
# <a name="too-many-files"></a><span data-ttu-id="3b183-102">檔案太多</span><span class="sxs-lookup"><span data-stu-id="3b183-102">Too many files</span></span>
<span data-ttu-id="3b183-103">在根目錄中建立的檔案比作業系統允許的還要多，或開啟的檔案數超過您設定中的**files =** 設定中指定的數目。SYS 檔案。</span><span class="sxs-lookup"><span data-stu-id="3b183-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3b183-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="3b183-104">To correct this error</span></span>  
  
1. <span data-ttu-id="3b183-105">如果您的程式正在開啟、關閉或儲存根目錄中的檔案，請變更您的程式，使其使用子目錄。</span><span class="sxs-lookup"><span data-stu-id="3b183-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="3b183-106">增加您的檔案中指定的檔案數 **=** 設定中的。SYS 檔案，然後重新開機您的電腦。</span><span class="sxs-lookup"><span data-stu-id="3b183-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b183-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b183-107">See also</span></span>

- [<span data-ttu-id="3b183-108">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="3b183-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
