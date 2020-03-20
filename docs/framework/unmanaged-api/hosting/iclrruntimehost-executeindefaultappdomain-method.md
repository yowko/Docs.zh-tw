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
ms.openlocfilehash: 1a1bc7609042422de876fe167a9e61655aaf62b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176405"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="7072d-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="7072d-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="7072d-103">調用指定託管程式集中指定類型的指定方法。</span><span class="sxs-lookup"><span data-stu-id="7072d-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7072d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7072d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7072d-105">參數</span><span class="sxs-lookup"><span data-stu-id="7072d-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="7072d-106">[在]定義要調用其<xref:System.Reflection.Assembly>方法的 的<xref:System.Type>的 路徑。</span><span class="sxs-lookup"><span data-stu-id="7072d-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="7072d-107">[在]定義要調用的方法<xref:System.Type>的名稱。</span><span class="sxs-lookup"><span data-stu-id="7072d-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="7072d-108">[在]要調用的方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="7072d-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="7072d-109">[在]要傳遞給方法的字串參數。</span><span class="sxs-lookup"><span data-stu-id="7072d-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="7072d-110">[出]被呼叫者法返回的整數值。</span><span class="sxs-lookup"><span data-stu-id="7072d-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7072d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="7072d-111">Return Value</span></span>  
  
|<span data-ttu-id="7072d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7072d-112">HRESULT</span></span>|<span data-ttu-id="7072d-113">描述</span><span class="sxs-lookup"><span data-stu-id="7072d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7072d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7072d-114">S_OK</span></span>|<span data-ttu-id="7072d-115">`ExecuteInDefaultAppDomain`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="7072d-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="7072d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7072d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7072d-117">公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="7072d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7072d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7072d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7072d-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="7072d-119">The call timed out.</span></span>|  
|<span data-ttu-id="7072d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7072d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7072d-121">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="7072d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7072d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7072d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7072d-123">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="7072d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7072d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7072d-124">E_FAIL</span></span>|<span data-ttu-id="7072d-125">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="7072d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7072d-126">如果方法返回E_FAIL，則 CRL 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="7072d-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="7072d-127">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7072d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7072d-128">備註</span><span class="sxs-lookup"><span data-stu-id="7072d-128">Remarks</span></span>  
 <span data-ttu-id="7072d-129">調用的方法必須具有以下簽名：</span><span class="sxs-lookup"><span data-stu-id="7072d-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="7072d-130">表示`pwzMethodName`被呼叫者法的名稱，並`pwzArgument`表示作為該方法的參數傳遞的字串值。</span><span class="sxs-lookup"><span data-stu-id="7072d-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="7072d-131">如果 HRESULT 值設置為S_OK，`pReturnValue`則設置為被呼叫者法返回的整數值。</span><span class="sxs-lookup"><span data-stu-id="7072d-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="7072d-132">否則，`pReturnValue`未設置。</span><span class="sxs-lookup"><span data-stu-id="7072d-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7072d-133">需求</span><span class="sxs-lookup"><span data-stu-id="7072d-133">Requirements</span></span>  
 <span data-ttu-id="7072d-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7072d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7072d-135">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7072d-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7072d-136">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="7072d-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7072d-137">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7072d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7072d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7072d-138">See also</span></span>

- [<span data-ttu-id="7072d-139">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="7072d-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
