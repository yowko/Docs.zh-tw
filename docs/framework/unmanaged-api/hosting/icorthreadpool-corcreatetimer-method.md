---
title: "ICorThreadpool::CorCreateTimer 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorCreateTimer
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e7a427396158fda7d387eecbeff58e6c1ef591dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="b3881-102">ICorThreadpool::CorCreateTimer 方法</span><span class="sxs-lookup"><span data-stu-id="b3881-102">ICorThreadpool::CorCreateTimer Method</span></span>
<span data-ttu-id="b3881-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="b3881-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3881-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3881-104">Syntax</span></span>  
  
```  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b3881-105">需求</span><span class="sxs-lookup"><span data-stu-id="b3881-105">Requirements</span></span>  
 <span data-ttu-id="b3881-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3881-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3881-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3881-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3881-108">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b3881-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3881-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3881-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3881-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3881-110">See Also</span></span>  
 [<span data-ttu-id="b3881-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="b3881-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
