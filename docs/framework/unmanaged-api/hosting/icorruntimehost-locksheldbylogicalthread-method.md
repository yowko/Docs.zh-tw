---
title: ICorRuntimeHost::LocksHeldByLogicalThread 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3eed83cbc983d59e99b3a42e667e9e126316c263
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780102"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="56c0f-102">ICorRuntimeHost::LocksHeldByLogicalThread 方法</span><span class="sxs-lookup"><span data-stu-id="56c0f-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="56c0f-103">擷取目前的執行緒持有的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="56c0f-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="56c0f-104">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="56c0f-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56c0f-105">語法</span><span class="sxs-lookup"><span data-stu-id="56c0f-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56c0f-106">參數</span><span class="sxs-lookup"><span data-stu-id="56c0f-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="56c0f-107">[out]目前的執行緒持有的鎖定數目指標。</span><span class="sxs-lookup"><span data-stu-id="56c0f-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56c0f-108">需求</span><span class="sxs-lookup"><span data-stu-id="56c0f-108">Requirements</span></span>  
 <span data-ttu-id="56c0f-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56c0f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56c0f-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56c0f-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56c0f-111">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="56c0f-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56c0f-112">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="56c0f-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c0f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56c0f-113">See also</span></span>

- [<span data-ttu-id="56c0f-114">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="56c0f-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
