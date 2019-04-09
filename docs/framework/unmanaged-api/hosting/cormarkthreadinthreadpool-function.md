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
ms.openlocfilehash: a39b0f2546d84cf24a58d5367c87d0a862aead93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085073"
---
# <a name="cormarkthreadinthreadpool-function"></a><span data-ttu-id="21111-102">CorMarkThreadInThreadPool 函式</span><span class="sxs-lookup"><span data-stu-id="21111-102">CorMarkThreadInThreadPool Function</span></span>
<span data-ttu-id="21111-103">標記目前正在執行的執行緒集區執行緒，以便執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="21111-103">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="21111-104">從.NET Framework 2.0 版開始，此函式沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="21111-104">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="21111-105">它不是必要項，並可從您的程式碼中移除。</span><span class="sxs-lookup"><span data-stu-id="21111-105">It is not required, and can be removed from your code.</span></span> <span data-ttu-id="21111-106">此函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="21111-106">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21111-107">語法</span><span class="sxs-lookup"><span data-stu-id="21111-107">Syntax</span></span>  
  
```  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="21111-108">需求</span><span class="sxs-lookup"><span data-stu-id="21111-108">Requirements</span></span>  
 <span data-ttu-id="21111-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21111-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21111-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="21111-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21111-111">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21111-111">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="21111-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="21111-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="21111-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21111-113">See also</span></span>

- [<span data-ttu-id="21111-114">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="21111-114">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
