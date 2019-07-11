---
title: ICorRuntimeHost::CloseEnum 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bfddd1d8f6fed105224cb2294d68f3f0bc016403
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762160"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="c97c5-102">ICorRuntimeHost::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="c97c5-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="c97c5-103">將網域列舉值重設回網域清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="c97c5-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c97c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="c97c5-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c97c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="c97c5-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="c97c5-106">[in]若要重設列舉值。</span><span class="sxs-lookup"><span data-stu-id="c97c5-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c97c5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c97c5-107">Return Value</span></span>  
  
|<span data-ttu-id="c97c5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c97c5-108">HRESULT</span></span>|<span data-ttu-id="c97c5-109">說明</span><span class="sxs-lookup"><span data-stu-id="c97c5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c97c5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c97c5-110">S_OK</span></span>|<span data-ttu-id="c97c5-111">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="c97c5-111">The operation was successful.</span></span>|  
|<span data-ttu-id="c97c5-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c97c5-112">S_FALSE</span></span>|<span data-ttu-id="c97c5-113">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="c97c5-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="c97c5-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c97c5-114">E_FAIL</span></span>|<span data-ttu-id="c97c5-115">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="c97c5-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="c97c5-116">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="c97c5-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="c97c5-117">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c97c5-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c97c5-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c97c5-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c97c5-119">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="c97c5-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c97c5-120">需求</span><span class="sxs-lookup"><span data-stu-id="c97c5-120">Requirements</span></span>  
 <span data-ttu-id="c97c5-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c97c5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c97c5-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c97c5-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c97c5-123">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c97c5-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c97c5-124">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="c97c5-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c97c5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c97c5-125">See also</span></span>

- [<span data-ttu-id="c97c5-126">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="c97c5-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="c97c5-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="c97c5-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
