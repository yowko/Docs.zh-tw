---
title: ICLRTaskManager::GetCurrentTaskType 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 848255d44ce8637182f18288d30151a3f0df0912
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092170"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="9f8fa-102">ICLRTaskManager::GetCurrentTaskType 方法</span><span class="sxs-lookup"><span data-stu-id="9f8fa-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="9f8fa-103">取得目前正在執行之工作的型別。</span><span class="sxs-lookup"><span data-stu-id="9f8fa-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f8fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="9f8fa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f8fa-105">參數</span><span class="sxs-lookup"><span data-stu-id="9f8fa-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="9f8fa-106">脫銷[ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md)列舉值的指標，指出目前正在執行的工作類型。</span><span class="sxs-lookup"><span data-stu-id="9f8fa-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f8fa-107">需求</span><span class="sxs-lookup"><span data-stu-id="9f8fa-107">Requirements</span></span>  
 <span data-ttu-id="9f8fa-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9f8fa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f8fa-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="9f8fa-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f8fa-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9f8fa-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f8fa-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f8fa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f8fa-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="9f8fa-112">See also</span></span>

- [<span data-ttu-id="9f8fa-113">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9f8fa-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
