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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3da22faa5e8863275cdfa8d03b980a5cbb55e87d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758361"
---
# <a name="cormarkthreadinthreadpool-function"></a><span data-ttu-id="f6db6-102">CorMarkThreadInThreadPool 函式</span><span class="sxs-lookup"><span data-stu-id="f6db6-102">CorMarkThreadInThreadPool Function</span></span>
<span data-ttu-id="f6db6-103">標記目前正在執行的執行緒集區執行緒，以便執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6db6-103">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="f6db6-104">從.NET Framework 2.0 版開始，此函式沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f6db6-104">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="f6db6-105">它不是必要項，並可從您的程式碼中移除。</span><span class="sxs-lookup"><span data-stu-id="f6db6-105">It is not required, and can be removed from your code.</span></span> <span data-ttu-id="f6db6-106">在.NET Framework 4 中，此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="f6db6-106">This function is deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6db6-107">語法</span><span class="sxs-lookup"><span data-stu-id="f6db6-107">Syntax</span></span>  
  
```cpp  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f6db6-108">需求</span><span class="sxs-lookup"><span data-stu-id="f6db6-108">Requirements</span></span>  
 <span data-ttu-id="f6db6-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6db6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6db6-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6db6-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6db6-111">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6db6-111">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6db6-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6db6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6db6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6db6-113">See also</span></span>

- [<span data-ttu-id="f6db6-114">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="f6db6-114">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
