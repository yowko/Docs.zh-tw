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
ms.openlocfilehash: ccff575974093de0bf00b257cba78c509f9cbd92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134780"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="0b0ae-102">IGCHostControl::RequestVirtualMemLimit 方法</span><span class="sxs-lookup"><span data-stu-id="0b0ae-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="0b0ae-103">要求主機變更虛擬記憶體的限制。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b0ae-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b0ae-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b0ae-105">參數</span><span class="sxs-lookup"><span data-stu-id="0b0ae-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="0b0ae-106">在要配置的要求記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="0b0ae-107">[in、out]配置的實際記憶體大小的指標。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b0ae-108">需求</span><span class="sxs-lookup"><span data-stu-id="0b0ae-108">Requirements</span></span>  
 <span data-ttu-id="0b0ae-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b0ae-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b0ae-110">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="0b0ae-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b0ae-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0b0ae-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b0ae-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b0ae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b0ae-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="0b0ae-113">See also</span></span>

- [<span data-ttu-id="0b0ae-114">IGCHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="0b0ae-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
