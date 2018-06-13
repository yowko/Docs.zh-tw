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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51c103fb38dd97ec076096037932925e31280f02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437712"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="261ee-102">ICLRTaskManager::GetCurrentTaskType 方法</span><span class="sxs-lookup"><span data-stu-id="261ee-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="261ee-103">取得目前執行之工作的類型。</span><span class="sxs-lookup"><span data-stu-id="261ee-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="261ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="261ee-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="261ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="261ee-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="261ee-106">[out]值的指標[ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md)列舉，指出目前正在執行工作的類型。</span><span class="sxs-lookup"><span data-stu-id="261ee-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="261ee-107">需求</span><span class="sxs-lookup"><span data-stu-id="261ee-107">Requirements</span></span>  
 <span data-ttu-id="261ee-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="261ee-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="261ee-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="261ee-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="261ee-110">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="261ee-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="261ee-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="261ee-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261ee-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="261ee-112">See Also</span></span>  
 [<span data-ttu-id="261ee-113">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="261ee-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
