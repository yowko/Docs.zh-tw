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
ms.openlocfilehash: a599e754202309a2b61d1761150f3f570fd0dc76
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120416"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="a31cd-102">ICLRRuntimeHost::Start 方法</span><span class="sxs-lookup"><span data-stu-id="a31cd-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="a31cd-103">將 common language runtime （CLR）初始化為進程。</span><span class="sxs-lookup"><span data-stu-id="a31cd-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a31cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="a31cd-104">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a31cd-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a31cd-105">Return Value</span></span>  
  
|<span data-ttu-id="a31cd-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a31cd-106">HRESULT</span></span>|<span data-ttu-id="a31cd-107">描述</span><span class="sxs-lookup"><span data-stu-id="a31cd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a31cd-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a31cd-108">S_OK</span></span>|<span data-ttu-id="a31cd-109">已成功傳回 `Start`。</span><span class="sxs-lookup"><span data-stu-id="a31cd-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="a31cd-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a31cd-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a31cd-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a31cd-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a31cd-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a31cd-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a31cd-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="a31cd-113">The call timed out.</span></span>|  
|<span data-ttu-id="a31cd-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a31cd-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a31cd-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a31cd-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a31cd-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a31cd-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a31cd-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="a31cd-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a31cd-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a31cd-118">E_FAIL</span></span>|<span data-ttu-id="a31cd-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a31cd-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a31cd-120">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="a31cd-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a31cd-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a31cd-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a31cd-122">備註</span><span class="sxs-lookup"><span data-stu-id="a31cd-122">Remarks</span></span>  
 <span data-ttu-id="a31cd-123">在許多情況下，不需要呼叫 `Start`，因為執行時間會在第一次要求執行 managed 程式碼時自動初始化。</span><span class="sxs-lookup"><span data-stu-id="a31cd-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="a31cd-124">不過，您可以使用 `Start` 來指定執行時間應該初始化的確切時機。</span><span class="sxs-lookup"><span data-stu-id="a31cd-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a31cd-125">需求</span><span class="sxs-lookup"><span data-stu-id="a31cd-125">Requirements</span></span>  
 <span data-ttu-id="a31cd-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a31cd-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a31cd-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a31cd-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a31cd-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a31cd-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a31cd-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a31cd-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31cd-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="a31cd-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="a31cd-131">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="a31cd-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
