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
ms.openlocfilehash: ca1b97c509ea8ed2c43c30cab278048aeb4170a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="14d40-102">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="14d40-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="14d40-103">指向以 common language runtime (CLR) 呼叫表示初始設定已啟動，或是已完成的函式。</span><span class="sxs-lookup"><span data-stu-id="14d40-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="14d40-104">此函式指標中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="14d40-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14d40-105">語法</span><span class="sxs-lookup"><span data-stu-id="14d40-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="14d40-106">備註</span><span class="sxs-lookup"><span data-stu-id="14d40-106">Remarks</span></span>  
 <span data-ttu-id="14d40-107">此函式是由主機實作。</span><span class="sxs-lookup"><span data-stu-id="14d40-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14d40-108">需求</span><span class="sxs-lookup"><span data-stu-id="14d40-108">Requirements</span></span>  
 <span data-ttu-id="14d40-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="14d40-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14d40-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="14d40-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14d40-111">**程式庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="14d40-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="14d40-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14d40-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d40-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14d40-113">See Also</span></span>  
 [<span data-ttu-id="14d40-114">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="14d40-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 [<span data-ttu-id="14d40-115">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="14d40-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
