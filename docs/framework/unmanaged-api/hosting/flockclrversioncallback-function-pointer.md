---
title: "FLockClrVersionCallback 函式指標"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FLockClrVersionCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: FLockClrVersionCallback
helpviewer_keywords: FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90b3bd053eb2e1161d6bb107afe9b3c627b1b207
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="344c8-102">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="344c8-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="344c8-103">指向以 common language runtime (CLR) 呼叫表示初始設定已啟動，或是已完成的函式。</span><span class="sxs-lookup"><span data-stu-id="344c8-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="344c8-104">此函式指標中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="344c8-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="344c8-105">語法</span><span class="sxs-lookup"><span data-stu-id="344c8-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="344c8-106">備註</span><span class="sxs-lookup"><span data-stu-id="344c8-106">Remarks</span></span>  
 <span data-ttu-id="344c8-107">此函式是由主機實作。</span><span class="sxs-lookup"><span data-stu-id="344c8-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="344c8-108">需求</span><span class="sxs-lookup"><span data-stu-id="344c8-108">Requirements</span></span>  
 <span data-ttu-id="344c8-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="344c8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="344c8-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="344c8-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="344c8-111">**程式庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="344c8-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="344c8-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="344c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="344c8-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="344c8-113">See Also</span></span>  
 [<span data-ttu-id="344c8-114">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="344c8-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 [<span data-ttu-id="344c8-115">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="344c8-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
