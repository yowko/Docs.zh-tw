---
title: 權限遭拒
ms.date: 07/20/2015
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
ms.openlocfilehash: bf95a7a0c6cb80bc02434eab7a86d07cb6855ee2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387136"
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="b9d7a-102">使用權限遭拒 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9d7a-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="b9d7a-103">嘗試寫入受寫入保護的磁片，或存取已鎖定的檔案。</span><span class="sxs-lookup"><span data-stu-id="b9d7a-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b9d7a-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b9d7a-104">To correct this error</span></span>  
  
1. <span data-ttu-id="b9d7a-105">若要開啟受寫入保護的檔案，請變更檔案的寫入保護屬性。</span><span class="sxs-lookup"><span data-stu-id="b9d7a-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2. <span data-ttu-id="b9d7a-106">請確定另一個進程尚未鎖定檔案，然後等候開啟檔案，直到其他進程釋放該檔案為止。</span><span class="sxs-lookup"><span data-stu-id="b9d7a-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3. <span data-ttu-id="b9d7a-107">若要存取登錄，請檢查您的使用者權限是否包含這種類型的登錄存取權。</span><span class="sxs-lookup"><span data-stu-id="b9d7a-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d7a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9d7a-108">See also</span></span>

- [<span data-ttu-id="b9d7a-109">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="b9d7a-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
