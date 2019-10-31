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
ms.openlocfilehash: 15ce6b589beb6c8b30ff4e8b16440c8110cc466b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136897"
---
# <a name="cormarkthreadinthreadpool-function"></a><span data-ttu-id="43de8-102">CorMarkThreadInThreadPool 函式</span><span class="sxs-lookup"><span data-stu-id="43de8-102">CorMarkThreadInThreadPool Function</span></span>
<span data-ttu-id="43de8-103">標示目前執行中的執行緒集區執行緒，以執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="43de8-103">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="43de8-104">從 .NET Framework 版本2.0 開始，此函式不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="43de8-104">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="43de8-105">這不是必要的，而且可以從程式碼中移除。</span><span class="sxs-lookup"><span data-stu-id="43de8-105">It is not required, and can be removed from your code.</span></span> <span data-ttu-id="43de8-106">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="43de8-106">This function is deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43de8-107">語法</span><span class="sxs-lookup"><span data-stu-id="43de8-107">Syntax</span></span>  
  
```cpp  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="43de8-108">需求</span><span class="sxs-lookup"><span data-stu-id="43de8-108">Requirements</span></span>  
 <span data-ttu-id="43de8-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43de8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43de8-110">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="43de8-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43de8-111">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="43de8-111">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43de8-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43de8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43de8-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="43de8-113">See also</span></span>

- [<span data-ttu-id="43de8-114">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="43de8-114">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
