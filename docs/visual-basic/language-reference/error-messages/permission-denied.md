---
title: 權限遭拒
ms.date: 07/20/2015
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
ms.openlocfilehash: 410301a1e99040fc617ab1bf1e851329ab3072d2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347008"
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="200a2-102">使用權限遭拒 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="200a2-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="200a2-103">嘗試寫入受寫入保護的磁片，或存取已鎖定的檔案。</span><span class="sxs-lookup"><span data-stu-id="200a2-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="200a2-104">若要改正這項錯誤</span><span class="sxs-lookup"><span data-stu-id="200a2-104">To correct this error</span></span>  
  
1. <span data-ttu-id="200a2-105">若要開啟受寫入保護的檔案，請變更檔案的寫入保護屬性。</span><span class="sxs-lookup"><span data-stu-id="200a2-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2. <span data-ttu-id="200a2-106">請確定另一個進程尚未鎖定檔案，然後等候開啟檔案，直到其他進程釋放該檔案為止。</span><span class="sxs-lookup"><span data-stu-id="200a2-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3. <span data-ttu-id="200a2-107">若要存取登錄，請檢查您的使用者權限是否包含這種類型的登錄存取權。</span><span class="sxs-lookup"><span data-stu-id="200a2-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200a2-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="200a2-108">See also</span></span>

- [<span data-ttu-id="200a2-109">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="200a2-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
