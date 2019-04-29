---
title: ICorRuntimeHost::Stop 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c59a0c5ef1e89c2853a566bd3b587d15a1ed80c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700718"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="e634e-102">ICorRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="e634e-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="e634e-103">停止目前的處理序的執行階段中的程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="e634e-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e634e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e634e-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e634e-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="e634e-105">Return Value</span></span>  
  
|<span data-ttu-id="e634e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e634e-106">HRESULT</span></span>|<span data-ttu-id="e634e-107">描述</span><span class="sxs-lookup"><span data-stu-id="e634e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e634e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e634e-108">S_OK</span></span>|<span data-ttu-id="e634e-109">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="e634e-109">The operation was successful.</span></span>|  
|<span data-ttu-id="e634e-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e634e-110">S_FALSE</span></span>|<span data-ttu-id="e634e-111">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="e634e-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e634e-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e634e-112">E_FAIL</span></span>|<span data-ttu-id="e634e-113">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="e634e-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e634e-114">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="e634e-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e634e-115">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e634e-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e634e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e634e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e634e-117">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e634e-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e634e-118">備註</span><span class="sxs-lookup"><span data-stu-id="e634e-118">Remarks</span></span>  
 <span data-ttu-id="e634e-119">通常不需要呼叫`Stop`方法，因為程式碼就會停止執行處理序結束時。</span><span class="sxs-lookup"><span data-stu-id="e634e-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e634e-120">若要在呼叫之後`Stop`，CLR 無法重新初始化成相同的程序。</span><span class="sxs-lookup"><span data-stu-id="e634e-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e634e-121">需求</span><span class="sxs-lookup"><span data-stu-id="e634e-121">Requirements</span></span>  
 <span data-ttu-id="e634e-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e634e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e634e-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e634e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e634e-124">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e634e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e634e-125">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e634e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e634e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e634e-126">See also</span></span>

- [<span data-ttu-id="e634e-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="e634e-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
