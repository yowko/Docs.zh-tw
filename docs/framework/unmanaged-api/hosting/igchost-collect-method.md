---
title: IGCHost::Collect 方法
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c4fa79f4918412720592bce449a001a349ae657
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766558"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="f39b7-102">IGCHost::Collect 方法</span><span class="sxs-lookup"><span data-stu-id="f39b7-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="f39b7-103">強制發生指定的層代，不論目前的記憶體回收集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="f39b7-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f39b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="f39b7-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f39b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="f39b7-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="f39b7-106">[in]要執行記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="f39b7-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="f39b7-107">-1 值表示所有層代將會進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="f39b7-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f39b7-108">需求</span><span class="sxs-lookup"><span data-stu-id="f39b7-108">Requirements</span></span>  
 <span data-ttu-id="f39b7-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f39b7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f39b7-110">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="f39b7-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f39b7-111">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f39b7-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f39b7-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f39b7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39b7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f39b7-113">See also</span></span>

- [<span data-ttu-id="f39b7-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="f39b7-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
