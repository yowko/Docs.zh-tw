---
title: 檔案太多
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: cd168ce86569d2d7558e21a5b4cc5ef385b28313
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873553"
---
# <a name="too-many-files"></a><span data-ttu-id="50fa2-102">檔案太多</span><span class="sxs-lookup"><span data-stu-id="50fa2-102">Too many files</span></span>

<span data-ttu-id="50fa2-103">在跟作業系統允許的根目錄中建立了多個檔案，或是開啟的檔案數目超過您 CONFIG.SYS 檔案中的 **files =** 設定所指定的數目。</span><span class="sxs-lookup"><span data-stu-id="50fa2-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="50fa2-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="50fa2-104">To correct this error</span></span>  
  
1. <span data-ttu-id="50fa2-105">如果您的程式開啟、關閉或儲存根目錄中的檔案，請變更您的程式，使其使用子目錄。</span><span class="sxs-lookup"><span data-stu-id="50fa2-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="50fa2-106">增加您的檔案中所指定的檔案數目 **=** CONFIG.SYS 檔案中的設定，然後重新開機電腦。</span><span class="sxs-lookup"><span data-stu-id="50fa2-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50fa2-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50fa2-107">See also</span></span>

- [<span data-ttu-id="50fa2-108">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="50fa2-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
