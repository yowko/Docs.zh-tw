---
title: "CorMarkThreadInThreadPool 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 167220c563f8a3e051f7a3af8a486ea2d63bceb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cormarkthreadinthreadpool-function"></a><span data-ttu-id="daad7-102">CorMarkThreadInThreadPool 函式</span><span class="sxs-lookup"><span data-stu-id="daad7-102">CorMarkThreadInThreadPool Function</span></span>
<span data-ttu-id="daad7-103">標記目前正在執行的執行緒集區執行緒，以便執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="daad7-103">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="daad7-104">從.NET Framework 2.0 版開始，此函式沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="daad7-104">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="daad7-105">它不是必要項目，並可以從您的程式碼中移除。此函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="daad7-105">It is not required, and can be removed from your code.This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daad7-106">語法</span><span class="sxs-lookup"><span data-stu-id="daad7-106">Syntax</span></span>  
  
```  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="daad7-107">需求</span><span class="sxs-lookup"><span data-stu-id="daad7-107">Requirements</span></span>  
 <span data-ttu-id="daad7-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="daad7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daad7-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="daad7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="daad7-110">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="daad7-110">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="daad7-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daad7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daad7-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="daad7-112">See Also</span></span>  
 [<span data-ttu-id="daad7-113">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="daad7-113">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
