---
title: CorMarkThreadInThreadPool 函式
ms.date: 03/30/2017
api_name:
- CorMarkThreadInThreadPool
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorMarkThreadInThreadPool
helpviewer_keywords:
- CorMarkThreadInThreadPool function [.NET Framework hosting]
ms.assetid: 3f958d41-e82e-4ec3-ae6f-16c7b3b31e3e
topic_type:
- apiref
ms.openlocfilehash: 30e8df6e2dcdfed15badaa6c0996ee6c912315d2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616514"
---
# <a name="cormarkthreadinthreadpool-function"></a><span data-ttu-id="45882-102">CorMarkThreadInThreadPool 函式</span><span class="sxs-lookup"><span data-stu-id="45882-102">CorMarkThreadInThreadPool Function</span></span>
<span data-ttu-id="45882-103">標示目前執行中的執行緒集區執行緒，以執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="45882-103">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="45882-104">從 .NET Framework 版本2.0 開始，此函式不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="45882-104">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="45882-105">這不是必要的，而且可以從程式碼中移除。</span><span class="sxs-lookup"><span data-stu-id="45882-105">It is not required, and can be removed from your code.</span></span> <span data-ttu-id="45882-106">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="45882-106">This function is deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45882-107">語法</span><span class="sxs-lookup"><span data-stu-id="45882-107">Syntax</span></span>  
  
```cpp  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="45882-108">需求</span><span class="sxs-lookup"><span data-stu-id="45882-108">Requirements</span></span>  
 <span data-ttu-id="45882-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45882-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45882-110">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="45882-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45882-111">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="45882-111">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45882-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45882-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45882-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45882-113">See also</span></span>

- [<span data-ttu-id="45882-114">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="45882-114">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
