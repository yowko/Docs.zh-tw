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
ms.openlocfilehash: 070c52258b66dcc352f2beef81b9a0694b8301ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703282"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="2c05f-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="2c05f-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="2c05f-103">在指定的 managed 元件中，呼叫指定之類型的指定方法。</span><span class="sxs-lookup"><span data-stu-id="2c05f-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c05f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c05f-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c05f-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c05f-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="2c05f-106">在的路徑， <xref:System.Reflection.Assembly> 定義 <xref:System.Type> 要叫用其方法的。</span><span class="sxs-lookup"><span data-stu-id="2c05f-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="2c05f-107">在的名稱 <xref:System.Type> ，定義要叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="2c05f-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="2c05f-108">在要叫用之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="2c05f-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="2c05f-109">在要傳遞至方法的字串參數。</span><span class="sxs-lookup"><span data-stu-id="2c05f-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="2c05f-110">脫銷叫用的方法所傳回的整數值。</span><span class="sxs-lookup"><span data-stu-id="2c05f-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c05f-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="2c05f-111">Return Value</span></span>  
  
|<span data-ttu-id="2c05f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c05f-112">HRESULT</span></span>|<span data-ttu-id="2c05f-113">說明</span><span class="sxs-lookup"><span data-stu-id="2c05f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c05f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c05f-114">S_OK</span></span>|<span data-ttu-id="2c05f-115">`ExecuteInDefaultAppDomain`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2c05f-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="2c05f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c05f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c05f-117">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2c05f-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c05f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c05f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c05f-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="2c05f-119">The call timed out.</span></span>|  
|<span data-ttu-id="2c05f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c05f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c05f-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2c05f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c05f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c05f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c05f-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="2c05f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2c05f-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c05f-124">E_FAIL</span></span>|<span data-ttu-id="2c05f-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2c05f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c05f-126">如果方法傳回 E_FAIL，該 CRL 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="2c05f-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="2c05f-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2c05f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c05f-128">備註</span><span class="sxs-lookup"><span data-stu-id="2c05f-128">Remarks</span></span>  
 <span data-ttu-id="2c05f-129">叫用的方法必須具有下列簽章：</span><span class="sxs-lookup"><span data-stu-id="2c05f-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="2c05f-130">其中 `pwzMethodName` 代表已叫用方法的名稱，而 `pwzArgument` 代表當做參數傳遞至該方法的字串值。</span><span class="sxs-lookup"><span data-stu-id="2c05f-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="2c05f-131">如果 HRESULT 值設定為 S_OK， `pReturnValue` 會設定為叫用方法所傳回的整數值。</span><span class="sxs-lookup"><span data-stu-id="2c05f-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="2c05f-132">否則， `pReturnValue` 就不會設定。</span><span class="sxs-lookup"><span data-stu-id="2c05f-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c05f-133">需求</span><span class="sxs-lookup"><span data-stu-id="2c05f-133">Requirements</span></span>  
 <span data-ttu-id="2c05f-134">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c05f-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c05f-135">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2c05f-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c05f-136">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2c05f-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c05f-137">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c05f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c05f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c05f-138">See also</span></span>

- [<span data-ttu-id="2c05f-139">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="2c05f-139">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
