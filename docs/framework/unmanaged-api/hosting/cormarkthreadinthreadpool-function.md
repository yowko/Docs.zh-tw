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
ms.openlocfilehash: d1e0f79304c4ed0d052bb05e364f64d6cb524f21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495236"
---
# <a name="cormarkthreadinthreadpool-function"></a><span data-ttu-id="ea827-102">CorMarkThreadInThreadPool 函式</span><span class="sxs-lookup"><span data-stu-id="ea827-102">CorMarkThreadInThreadPool Function</span></span>
<span data-ttu-id="ea827-103">標記目前正在執行的執行緒集區執行緒，以便執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ea827-103">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="ea827-104">從.NET Framework 2.0 版開始，此函式沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="ea827-104">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="ea827-105">它不是必要項，並可從您的程式碼中移除。此函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ea827-105">It is not required, and can be removed from your code.This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea827-106">語法</span><span class="sxs-lookup"><span data-stu-id="ea827-106">Syntax</span></span>  
  
```  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="ea827-107">需求</span><span class="sxs-lookup"><span data-stu-id="ea827-107">Requirements</span></span>  
 <span data-ttu-id="ea827-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea827-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea827-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ea827-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea827-110">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea827-110">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea827-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea827-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea827-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea827-112">See also</span></span>
- [<span data-ttu-id="ea827-113">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="ea827-113">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
