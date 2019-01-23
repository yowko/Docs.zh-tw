---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae7bbc41d0e2cca1cf25a5ec34535b20fc9163d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498251"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="38062-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="38062-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="38062-103">指定 managed 組件中會呼叫指定之型別的指定的方法。</span><span class="sxs-lookup"><span data-stu-id="38062-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38062-104">語法</span><span class="sxs-lookup"><span data-stu-id="38062-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38062-105">參數</span><span class="sxs-lookup"><span data-stu-id="38062-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="38062-106">[in]通往<xref:System.Reflection.Assembly>定義<xref:System.Type>其方法是叫用。</span><span class="sxs-lookup"><span data-stu-id="38062-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="38062-107">[in]名稱<xref:System.Type>定義叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="38062-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="38062-108">[in]若要叫用方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="38062-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="38062-109">[in]要傳遞至方法的字串參數。</span><span class="sxs-lookup"><span data-stu-id="38062-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="38062-110">[out]叫用方法所傳回的整數值。</span><span class="sxs-lookup"><span data-stu-id="38062-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38062-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="38062-111">Return Value</span></span>  
  
|<span data-ttu-id="38062-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38062-112">HRESULT</span></span>|<span data-ttu-id="38062-113">描述</span><span class="sxs-lookup"><span data-stu-id="38062-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38062-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="38062-114">S_OK</span></span>|<span data-ttu-id="38062-115">`ExecuteInDefaultAppDomain` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="38062-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="38062-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38062-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38062-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="38062-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38062-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38062-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38062-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="38062-119">The call timed out.</span></span>|  
|<span data-ttu-id="38062-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38062-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38062-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="38062-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38062-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38062-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38062-123">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="38062-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38062-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38062-124">E_FAIL</span></span>|<span data-ttu-id="38062-125">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="38062-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38062-126">如果方法會傳回 E_FAIL，CRL 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="38062-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="38062-127">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="38062-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38062-128">備註</span><span class="sxs-lookup"><span data-stu-id="38062-128">Remarks</span></span>  
 <span data-ttu-id="38062-129">叫用的方法必須具有下列簽章：</span><span class="sxs-lookup"><span data-stu-id="38062-129">The invoked method must have the following signature:</span></span>  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="38062-130">何處`pwzMethodName`表示叫用的方法，名稱和`pwzArgument`表示的字串值做為參數傳遞至該方法。</span><span class="sxs-lookup"><span data-stu-id="38062-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="38062-131">如果 HRESULT 值設定為 S_OK，`pReturnValue`設為 已叫用方法所傳回的整數值。</span><span class="sxs-lookup"><span data-stu-id="38062-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="38062-132">否則，`pReturnValue`未設定。</span><span class="sxs-lookup"><span data-stu-id="38062-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38062-133">需求</span><span class="sxs-lookup"><span data-stu-id="38062-133">Requirements</span></span>  
 <span data-ttu-id="38062-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38062-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38062-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38062-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38062-136">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="38062-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38062-137">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38062-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38062-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38062-138">See also</span></span>
- [<span data-ttu-id="38062-139">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="38062-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
