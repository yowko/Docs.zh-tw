---
title: 使用權限遭拒 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
ms.openlocfilehash: d904ee48ee187d073647b6e09af57264c8c318f6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813947"
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="bfd55-102">使用權限遭拒 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfd55-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="bfd55-103">已嘗試寫入防寫保護的磁碟，或存取鎖定的檔案。</span><span class="sxs-lookup"><span data-stu-id="bfd55-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bfd55-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bfd55-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="bfd55-105">若要開啟防寫保護的檔案，變更檔案的寫入保護屬性。</span><span class="sxs-lookup"><span data-stu-id="bfd55-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2.  <span data-ttu-id="bfd55-106">請確定其他處理序不會鎖定檔案，並等候開啟檔案，直到其他處理序釋放它為止。</span><span class="sxs-lookup"><span data-stu-id="bfd55-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3.  <span data-ttu-id="bfd55-107">若要存取登錄，請檢查您的使用者權限包含這種類型的登錄存取權。</span><span class="sxs-lookup"><span data-stu-id="bfd55-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd55-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfd55-108">See also</span></span>

- [<span data-ttu-id="bfd55-109">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="bfd55-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
