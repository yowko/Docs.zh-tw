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
ms.openlocfilehash: b44797f6efaf8904e3df876e9278a977c912ac6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="87e03-102">ICorRuntimeHost::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="87e03-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="87e03-103">將定義域列舉值重設回網域清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="87e03-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e03-104">語法</span><span class="sxs-lookup"><span data-stu-id="87e03-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87e03-105">參數</span><span class="sxs-lookup"><span data-stu-id="87e03-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="87e03-106">[in]若要重設列舉值。</span><span class="sxs-lookup"><span data-stu-id="87e03-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87e03-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="87e03-107">Return Value</span></span>  
  
|<span data-ttu-id="87e03-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87e03-108">HRESULT</span></span>|<span data-ttu-id="87e03-109">描述</span><span class="sxs-lookup"><span data-stu-id="87e03-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87e03-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="87e03-110">S_OK</span></span>|<span data-ttu-id="87e03-111">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="87e03-111">The operation was successful.</span></span>|  
|<span data-ttu-id="87e03-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="87e03-112">S_FALSE</span></span>|<span data-ttu-id="87e03-113">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="87e03-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="87e03-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="87e03-114">E_FAIL</span></span>|<span data-ttu-id="87e03-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="87e03-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="87e03-116">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="87e03-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="87e03-117">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="87e03-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="87e03-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="87e03-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="87e03-119">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="87e03-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87e03-120">需求</span><span class="sxs-lookup"><span data-stu-id="87e03-120">Requirements</span></span>  
 <span data-ttu-id="87e03-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87e03-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e03-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="87e03-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87e03-123">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="87e03-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87e03-124">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="87e03-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e03-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87e03-125">See Also</span></span>  
 [<span data-ttu-id="87e03-126">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="87e03-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="87e03-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="87e03-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
