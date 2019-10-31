---
title: ICorConfiguration::SetGCHostControl 方法
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
ms.openlocfilehash: 5a32fb0480e76f47495590a29c329f54722e2dee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127784"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="93dc7-102">ICorConfiguration::SetGCHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="93dc7-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="93dc7-103">設定要由垃圾收集行程用來要求主控制項變更虛擬記憶體限制的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="93dc7-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93dc7-104">語法</span><span class="sxs-lookup"><span data-stu-id="93dc7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93dc7-105">參數</span><span class="sxs-lookup"><span data-stu-id="93dc7-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="93dc7-106">在[IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)物件的指標，可讓垃圾收集行程要求主控制項變更虛擬記憶體的限制。</span><span class="sxs-lookup"><span data-stu-id="93dc7-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93dc7-107">需求</span><span class="sxs-lookup"><span data-stu-id="93dc7-107">Requirements</span></span>  
 <span data-ttu-id="93dc7-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93dc7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93dc7-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="93dc7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93dc7-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="93dc7-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93dc7-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93dc7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93dc7-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="93dc7-112">See also</span></span>

- [<span data-ttu-id="93dc7-113">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="93dc7-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
