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
ms.openlocfilehash: d46881b76685fd04f8bc5e3a67830e58f85cd774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436672"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="0d9c7-102">ICorRuntimeHost::LocksHeldByLogicalThread 方法</span><span class="sxs-lookup"><span data-stu-id="0d9c7-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="0d9c7-103">擷取目前的執行緒持有的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="0d9c7-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="0d9c7-104">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="0d9c7-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d9c7-105">語法</span><span class="sxs-lookup"><span data-stu-id="0d9c7-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d9c7-106">參數</span><span class="sxs-lookup"><span data-stu-id="0d9c7-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="0d9c7-107">[out]目前的執行緒持有的鎖定數目指標。</span><span class="sxs-lookup"><span data-stu-id="0d9c7-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d9c7-108">需求</span><span class="sxs-lookup"><span data-stu-id="0d9c7-108">Requirements</span></span>  
 <span data-ttu-id="0d9c7-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d9c7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d9c7-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d9c7-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d9c7-111">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0d9c7-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d9c7-112">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="0d9c7-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d9c7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d9c7-113">See Also</span></span>  
 [<span data-ttu-id="0d9c7-114">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="0d9c7-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
