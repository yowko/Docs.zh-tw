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
ms.openlocfilehash: 9dcddb5766894a30f1ccb2552a09abe7153c6eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434948"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="900a3-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="900a3-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="900a3-103">呼叫指定類型的指定的方法中指定的 managed 組件。</span><span class="sxs-lookup"><span data-stu-id="900a3-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="900a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="900a3-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="900a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="900a3-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="900a3-106">[in]路徑<xref:System.Reflection.Assembly>定義<xref:System.Type>其方法是叫用。</span><span class="sxs-lookup"><span data-stu-id="900a3-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="900a3-107">[in]名稱<xref:System.Type>，定義要叫用方法。</span><span class="sxs-lookup"><span data-stu-id="900a3-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="900a3-108">[in]要叫用方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="900a3-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="900a3-109">[in]要傳遞至方法的字串參數。</span><span class="sxs-lookup"><span data-stu-id="900a3-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="900a3-110">[out]叫用方法所傳回的整數值。</span><span class="sxs-lookup"><span data-stu-id="900a3-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="900a3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="900a3-111">Return Value</span></span>  
  
|<span data-ttu-id="900a3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="900a3-112">HRESULT</span></span>|<span data-ttu-id="900a3-113">描述</span><span class="sxs-lookup"><span data-stu-id="900a3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="900a3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="900a3-114">S_OK</span></span>|<span data-ttu-id="900a3-115">`ExecuteInDefaultAppDomain` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="900a3-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="900a3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="900a3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="900a3-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="900a3-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="900a3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="900a3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="900a3-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="900a3-119">The call timed out.</span></span>|  
|<span data-ttu-id="900a3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="900a3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="900a3-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="900a3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="900a3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="900a3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="900a3-123">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="900a3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="900a3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="900a3-124">E_FAIL</span></span>|<span data-ttu-id="900a3-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="900a3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="900a3-126">如果方法會傳回 E_FAIL，CRL 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="900a3-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="900a3-127">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="900a3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="900a3-128">備註</span><span class="sxs-lookup"><span data-stu-id="900a3-128">Remarks</span></span>  
 <span data-ttu-id="900a3-129">叫用的方法必須具有下列簽章：</span><span class="sxs-lookup"><span data-stu-id="900a3-129">The invoked method must have the following signature:</span></span>  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="900a3-130">其中`pwzMethodName`代表叫用的方法名稱和`pwzArgument`代表做為參數傳遞至該方法的字串值。</span><span class="sxs-lookup"><span data-stu-id="900a3-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="900a3-131">如果 HRESULT 值設定為 S_OK，`pReturnValue`設為叫用方法所傳回的整數值。</span><span class="sxs-lookup"><span data-stu-id="900a3-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="900a3-132">否則，`pReturnValue`未設定。</span><span class="sxs-lookup"><span data-stu-id="900a3-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="900a3-133">需求</span><span class="sxs-lookup"><span data-stu-id="900a3-133">Requirements</span></span>  
 <span data-ttu-id="900a3-134">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="900a3-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="900a3-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="900a3-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="900a3-136">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="900a3-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="900a3-137">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="900a3-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="900a3-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="900a3-138">See Also</span></span>  
 [<span data-ttu-id="900a3-139">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="900a3-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
