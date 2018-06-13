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
ms.openlocfilehash: df2747b7cce112e61c6fb99cdb91dc0d56047b9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432556"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="ffe88-102">ICLRRuntimeHost::Start 方法</span><span class="sxs-lookup"><span data-stu-id="ffe88-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="ffe88-103">初始化 common language runtime (CLR) 程序。</span><span class="sxs-lookup"><span data-stu-id="ffe88-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe88-104">語法</span><span class="sxs-lookup"><span data-stu-id="ffe88-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ffe88-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="ffe88-105">Return Value</span></span>  
  
|<span data-ttu-id="ffe88-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffe88-106">HRESULT</span></span>|<span data-ttu-id="ffe88-107">描述</span><span class="sxs-lookup"><span data-stu-id="ffe88-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffe88-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffe88-108">S_OK</span></span>|<span data-ttu-id="ffe88-109">`Start` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="ffe88-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="ffe88-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ffe88-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ffe88-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ffe88-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ffe88-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ffe88-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ffe88-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="ffe88-113">The call timed out.</span></span>|  
|<span data-ttu-id="ffe88-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ffe88-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ffe88-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ffe88-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ffe88-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ffe88-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ffe88-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="ffe88-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ffe88-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ffe88-118">E_FAIL</span></span>|<span data-ttu-id="ffe88-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="ffe88-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ffe88-120">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="ffe88-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ffe88-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ffe88-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffe88-122">備註</span><span class="sxs-lookup"><span data-stu-id="ffe88-122">Remarks</span></span>  
 <span data-ttu-id="ffe88-123">在許多情況下則不需要呼叫`Start`，因為執行階段會初始化其本身會自動在執行 managed 程式碼的第一個要求時。</span><span class="sxs-lookup"><span data-stu-id="ffe88-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="ffe88-124">不過，您可以使用`Start`指定完全執行階段初始化的時間。</span><span class="sxs-lookup"><span data-stu-id="ffe88-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffe88-125">需求</span><span class="sxs-lookup"><span data-stu-id="ffe88-125">Requirements</span></span>  
 <span data-ttu-id="ffe88-126">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ffe88-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffe88-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ffe88-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffe88-128">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ffe88-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffe88-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffe88-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe88-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffe88-130">See Also</span></span>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="ffe88-131">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="ffe88-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
