---
title: ICLRRuntimeHost::Start 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 608612f6a0f4395092e33ce75fdbd249f19ae4f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172610"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="79925-102">ICLRRuntimeHost::Start 方法</span><span class="sxs-lookup"><span data-stu-id="79925-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="79925-103">初始化 common language runtime (CLR) 處理序。</span><span class="sxs-lookup"><span data-stu-id="79925-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79925-104">語法</span><span class="sxs-lookup"><span data-stu-id="79925-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="79925-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="79925-105">Return Value</span></span>  
  
|<span data-ttu-id="79925-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79925-106">HRESULT</span></span>|<span data-ttu-id="79925-107">描述</span><span class="sxs-lookup"><span data-stu-id="79925-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79925-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="79925-108">S_OK</span></span>|<span data-ttu-id="79925-109">`Start` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="79925-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="79925-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79925-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79925-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="79925-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79925-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79925-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79925-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="79925-113">The call timed out.</span></span>|  
|<span data-ttu-id="79925-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79925-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79925-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="79925-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79925-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79925-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79925-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="79925-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79925-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79925-118">E_FAIL</span></span>|<span data-ttu-id="79925-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="79925-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79925-120">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="79925-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79925-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="79925-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79925-122">備註</span><span class="sxs-lookup"><span data-stu-id="79925-122">Remarks</span></span>  
 <span data-ttu-id="79925-123">在許多情況下不需要呼叫`Start`，因為執行階段會初始化本身會自動在執行 managed 程式碼的第一個要求時。</span><span class="sxs-lookup"><span data-stu-id="79925-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="79925-124">不過，您可以使用`Start`指定確切執行階段初始化的時間。</span><span class="sxs-lookup"><span data-stu-id="79925-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79925-125">需求</span><span class="sxs-lookup"><span data-stu-id="79925-125">Requirements</span></span>  
 <span data-ttu-id="79925-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79925-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79925-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="79925-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79925-128">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="79925-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79925-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79925-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79925-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79925-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="79925-131">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="79925-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
