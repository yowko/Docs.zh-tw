---
title: IGCHostControl::RequestVirtualMemLimit 方法
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948b18832ccfc5e0fc2e42ee58e6444a581de260
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209682"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="7f088-102">IGCHostControl::RequestVirtualMemLimit 方法</span><span class="sxs-lookup"><span data-stu-id="7f088-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="7f088-103">要求的主機，若要變更虛擬記憶體的限制。</span><span class="sxs-lookup"><span data-stu-id="7f088-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f088-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f088-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f088-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f088-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="7f088-106">[in]記憶體配置要求的大小。</span><span class="sxs-lookup"><span data-stu-id="7f088-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="7f088-107">[in、 out]實際大小配置的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="7f088-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f088-108">需求</span><span class="sxs-lookup"><span data-stu-id="7f088-108">Requirements</span></span>  
 <span data-ttu-id="7f088-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f088-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f088-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7f088-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f088-111">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7f088-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f088-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f088-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f088-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f088-113">See also</span></span>

- [<span data-ttu-id="7f088-114">IGCHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="7f088-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
