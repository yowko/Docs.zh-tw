---
title: "ICorRuntimeHost::CloseEnum 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CloseEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 677ab3a97b7fcceccd8ceb0943c62df8bc999649
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="753bc-102">ICorRuntimeHost::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="753bc-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="753bc-103">將定義域列舉值重設回網域清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="753bc-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="753bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="753bc-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="753bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="753bc-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="753bc-106">[in]若要重設列舉值。</span><span class="sxs-lookup"><span data-stu-id="753bc-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="753bc-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="753bc-107">Return Value</span></span>  
  
|<span data-ttu-id="753bc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="753bc-108">HRESULT</span></span>|<span data-ttu-id="753bc-109">描述</span><span class="sxs-lookup"><span data-stu-id="753bc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="753bc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="753bc-110">S_OK</span></span>|<span data-ttu-id="753bc-111">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="753bc-111">The operation was successful.</span></span>|  
|<span data-ttu-id="753bc-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="753bc-112">S_FALSE</span></span>|<span data-ttu-id="753bc-113">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="753bc-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="753bc-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="753bc-114">E_FAIL</span></span>|<span data-ttu-id="753bc-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="753bc-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="753bc-116">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="753bc-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="753bc-117">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="753bc-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="753bc-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="753bc-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="753bc-119">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="753bc-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="753bc-120">需求</span><span class="sxs-lookup"><span data-stu-id="753bc-120">Requirements</span></span>  
 <span data-ttu-id="753bc-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="753bc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="753bc-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="753bc-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="753bc-123">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="753bc-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="753bc-124">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="753bc-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753bc-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="753bc-125">See Also</span></span>  
 [<span data-ttu-id="753bc-126">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="753bc-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="753bc-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="753bc-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
