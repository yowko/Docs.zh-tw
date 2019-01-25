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
ms.openlocfilehash: 3ef92fbe5ba99d93eaf06aacc7efd943136e9785
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543194"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="4c765-102">ICorRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="4c765-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="4c765-103">停止目前的處理序的執行階段中的程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="4c765-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c765-104">語法</span><span class="sxs-lookup"><span data-stu-id="4c765-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4c765-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="4c765-105">Return Value</span></span>  
  
|<span data-ttu-id="4c765-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c765-106">HRESULT</span></span>|<span data-ttu-id="4c765-107">描述</span><span class="sxs-lookup"><span data-stu-id="4c765-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c765-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c765-108">S_OK</span></span>|<span data-ttu-id="4c765-109">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="4c765-109">The operation was successful.</span></span>|  
|<span data-ttu-id="4c765-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4c765-110">S_FALSE</span></span>|<span data-ttu-id="4c765-111">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="4c765-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="4c765-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4c765-112">E_FAIL</span></span>|<span data-ttu-id="4c765-113">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="4c765-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="4c765-114">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="4c765-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="4c765-115">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4c765-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4c765-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4c765-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4c765-117">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4c765-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c765-118">備註</span><span class="sxs-lookup"><span data-stu-id="4c765-118">Remarks</span></span>  
 <span data-ttu-id="4c765-119">通常不需要呼叫`Stop`方法，因為程式碼就會停止執行處理序結束時。</span><span class="sxs-lookup"><span data-stu-id="4c765-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c765-120">若要在呼叫之後`Stop`，CLR 無法重新初始化成相同的程序。</span><span class="sxs-lookup"><span data-stu-id="4c765-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c765-121">需求</span><span class="sxs-lookup"><span data-stu-id="4c765-121">Requirements</span></span>  
 <span data-ttu-id="4c765-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c765-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c765-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c765-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c765-124">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4c765-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c765-125">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="4c765-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c765-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c765-126">See also</span></span>
- [<span data-ttu-id="4c765-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="4c765-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
