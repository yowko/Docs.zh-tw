---
title: ICLRRuntimeHost::GetCLRControl 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
ms.openlocfilehash: 68bcdc33e34075cc5876ee721ef57282cdaa6e86
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703693"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="2b3c5-102">ICLRRuntimeHost::GetCLRControl 方法</span><span class="sxs-lookup"><span data-stu-id="2b3c5-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="2b3c5-103">取得[ICLRControl 介面](iclrcontrol-interface.md)類型的介面指標，可供裝載用來自訂 common language RUNTIME （CLR）的各個層面。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-103">Gets an interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b3c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b3c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b3c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b3c5-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="2b3c5-106">脫銷[ICLRControl 介面](iclrcontrol-interface.md)類型的介面指標，可讓主機設定 CLR 的其他層面。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-106">[out] An interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b3c5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2b3c5-107">Return Value</span></span>  
  
|<span data-ttu-id="2b3c5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b3c5-108">HRESULT</span></span>|<span data-ttu-id="2b3c5-109">說明</span><span class="sxs-lookup"><span data-stu-id="2b3c5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b3c5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b3c5-110">S_OK</span></span>|<span data-ttu-id="2b3c5-111">`GetCLRControl`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="2b3c5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2b3c5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2b3c5-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2b3c5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2b3c5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2b3c5-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-115">The call timed out.</span></span>|  
|<span data-ttu-id="2b3c5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2b3c5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2b3c5-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2b3c5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2b3c5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2b3c5-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2b3c5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b3c5-120">E_FAIL</span></span>|<span data-ttu-id="2b3c5-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2b3c5-122">如果方法傳回 E_FAIL，就無法在進程內使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2b3c5-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2b3c5-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="2b3c5-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="2b3c5-125">CLR 已經啟動。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b3c5-126">備註</span><span class="sxs-lookup"><span data-stu-id="2b3c5-126">Remarks</span></span>  
 <span data-ttu-id="2b3c5-127">`ICLRControl`提供[GetCLRManager 方法](iclrcontrol-getclrmanager-method.md)方法，可讓主機取得其中一個管理員類型的介面指標。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-127">`ICLRControl` provides the [GetCLRManager Method](iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b3c5-128">需求</span><span class="sxs-lookup"><span data-stu-id="2b3c5-128">Requirements</span></span>  
 <span data-ttu-id="2b3c5-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b3c5-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b3c5-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2b3c5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b3c5-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2b3c5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b3c5-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b3c5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b3c5-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b3c5-133">See also</span></span>

- [<span data-ttu-id="2b3c5-134">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="2b3c5-134">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="2b3c5-135">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="2b3c5-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
