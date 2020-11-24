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
ms.openlocfilehash: 9342233317535ebecbcddea48b9029b81868eb0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690144"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="60f54-102">ICorRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="60f54-102">ICorRuntimeHost::Stop Method</span></span>

<span data-ttu-id="60f54-103">停止執行時間中目前進程的程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="60f54-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f54-104">語法</span><span class="sxs-lookup"><span data-stu-id="60f54-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="60f54-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="60f54-105">Return Value</span></span>  
  
|<span data-ttu-id="60f54-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60f54-106">HRESULT</span></span>|<span data-ttu-id="60f54-107">描述</span><span class="sxs-lookup"><span data-stu-id="60f54-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60f54-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="60f54-108">S_OK</span></span>|<span data-ttu-id="60f54-109">作業成功。</span><span class="sxs-lookup"><span data-stu-id="60f54-109">The operation was successful.</span></span>|  
|<span data-ttu-id="60f54-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="60f54-110">S_FALSE</span></span>|<span data-ttu-id="60f54-111">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="60f54-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="60f54-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60f54-112">E_FAIL</span></span>|<span data-ttu-id="60f54-113">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="60f54-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="60f54-114">如果方法傳回 E_FAIL，則程式中的 common language runtime (CLR) 將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="60f54-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="60f54-115">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="60f54-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="60f54-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="60f54-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="60f54-117">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="60f54-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60f54-118">備註</span><span class="sxs-lookup"><span data-stu-id="60f54-118">Remarks</span></span>  

 <span data-ttu-id="60f54-119">通常不需要呼叫 `Stop` 方法，因為程式碼會在進程結束時停止執行。</span><span class="sxs-lookup"><span data-stu-id="60f54-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60f54-120">在呼叫之後 `Stop` ，CLR 無法重新初始化為相同的進程。</span><span class="sxs-lookup"><span data-stu-id="60f54-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f54-121">需求</span><span class="sxs-lookup"><span data-stu-id="60f54-121">Requirements</span></span>  

 <span data-ttu-id="60f54-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60f54-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f54-123">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="60f54-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60f54-124">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="60f54-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60f54-125">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="60f54-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f54-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60f54-126">See also</span></span>

- [<span data-ttu-id="60f54-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="60f54-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
