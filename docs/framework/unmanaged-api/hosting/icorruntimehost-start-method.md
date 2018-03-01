---
title: "ICorRuntimeHost::Start 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d79046db904de68e5b24b2f96206bb1de2de470
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="54295-102">ICorRuntimeHost::Start 方法</span><span class="sxs-lookup"><span data-stu-id="54295-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="54295-103">啟動 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="54295-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54295-104">語法</span><span class="sxs-lookup"><span data-stu-id="54295-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="54295-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="54295-105">Return Value</span></span>  
  
|<span data-ttu-id="54295-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54295-106">HRESULT</span></span>|<span data-ttu-id="54295-107">描述</span><span class="sxs-lookup"><span data-stu-id="54295-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54295-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="54295-108">S_OK</span></span>|<span data-ttu-id="54295-109">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="54295-109">The operation was successful.</span></span>|  
|<span data-ttu-id="54295-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="54295-110">S_FALSE</span></span>|<span data-ttu-id="54295-111">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="54295-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="54295-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54295-112">E_FAIL</span></span>|<span data-ttu-id="54295-113">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="54295-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="54295-114">若方法會傳回 E_FAIL，CLR 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="54295-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="54295-115">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="54295-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="54295-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54295-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54295-117">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="54295-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54295-118">備註</span><span class="sxs-lookup"><span data-stu-id="54295-118">Remarks</span></span>  
 <span data-ttu-id="54295-119">它通常是不需要呼叫`Start`方法，因為 CLR 執行 managed 程式碼的第一個要求時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="54295-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54295-120">需求</span><span class="sxs-lookup"><span data-stu-id="54295-120">Requirements</span></span>  
 <span data-ttu-id="54295-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54295-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54295-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54295-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54295-123">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="54295-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54295-124">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="54295-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54295-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="54295-125">See Also</span></span>  
 [<span data-ttu-id="54295-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="54295-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
