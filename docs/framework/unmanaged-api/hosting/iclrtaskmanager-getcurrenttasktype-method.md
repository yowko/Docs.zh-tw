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
ms.openlocfilehash: 684b94471c53701c5ebe1dc7e7593eae16ad50fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728780"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="c811d-102">ICLRTaskManager::GetCurrentTaskType 方法</span><span class="sxs-lookup"><span data-stu-id="c811d-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>

<span data-ttu-id="c811d-103">取得目前正在執行之工作的類型。</span><span class="sxs-lookup"><span data-stu-id="c811d-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c811d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c811d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c811d-105">參數</span><span class="sxs-lookup"><span data-stu-id="c811d-105">Parameters</span></span>  

 `pTaskType`  
 <span data-ttu-id="c811d-106">擴展 [ETaskType](etasktype-enumeration.md) 列舉值的指標，指出目前正在執行的工作類型。</span><span class="sxs-lookup"><span data-stu-id="c811d-106">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c811d-107">需求</span><span class="sxs-lookup"><span data-stu-id="c811d-107">Requirements</span></span>  

 <span data-ttu-id="c811d-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c811d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c811d-109">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c811d-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c811d-110">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c811d-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c811d-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c811d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c811d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c811d-112">See also</span></span>

- [<span data-ttu-id="c811d-113">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c811d-113">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
