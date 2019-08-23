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
ms.openlocfilehash: ca51b87e7afc8e9e48d541a32b3bd60a19a5ff70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965962"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="a5b59-102">ICorRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="a5b59-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="a5b59-103">在執行時間中停止執行目前進程的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a5b59-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5b59-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5b59-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a5b59-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a5b59-105">Return Value</span></span>  
  
|<span data-ttu-id="a5b59-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5b59-106">HRESULT</span></span>|<span data-ttu-id="a5b59-107">說明</span><span class="sxs-lookup"><span data-stu-id="a5b59-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5b59-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5b59-108">S_OK</span></span>|<span data-ttu-id="a5b59-109">作業成功。</span><span class="sxs-lookup"><span data-stu-id="a5b59-109">The operation was successful.</span></span>|  
|<span data-ttu-id="a5b59-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a5b59-110">S_FALSE</span></span>|<span data-ttu-id="a5b59-111">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="a5b59-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a5b59-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a5b59-112">E_FAIL</span></span>|<span data-ttu-id="a5b59-113">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a5b59-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a5b59-114">如果方法傳回 E_FAIL, 則 common language runtime (CLR) 在進程中就不再可用。</span><span class="sxs-lookup"><span data-stu-id="a5b59-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a5b59-115">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a5b59-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a5b59-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a5b59-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a5b59-117">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a5b59-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5b59-118">備註</span><span class="sxs-lookup"><span data-stu-id="a5b59-118">Remarks</span></span>  
 <span data-ttu-id="a5b59-119">通常不需要呼叫`Stop`方法, 因為程式碼會在進程結束時停止執行。</span><span class="sxs-lookup"><span data-stu-id="a5b59-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5b59-120">呼叫`Stop`之後, 無法將 CLR 重新初始化為相同的進程。</span><span class="sxs-lookup"><span data-stu-id="a5b59-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5b59-121">需求</span><span class="sxs-lookup"><span data-stu-id="a5b59-121">Requirements</span></span>  
 <span data-ttu-id="a5b59-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5b59-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5b59-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a5b59-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5b59-124">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a5b59-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5b59-125">**.NET Framework 版本:** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="a5b59-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b59-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5b59-126">See also</span></span>

- [<span data-ttu-id="a5b59-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="a5b59-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
