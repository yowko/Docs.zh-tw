---
title: ICLRRuntimeInfo::IsStarted 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45b1ef75227932449b68366345ded33a2cd96490
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479671"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="691d2-102">ICLRRuntimeInfo::IsStarted 方法</span><span class="sxs-lookup"><span data-stu-id="691d2-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="691d2-103">指出是否已啟動執行階段 (亦即是否[iclrruntimehost:: Start 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)被呼叫，且已成功)。</span><span class="sxs-lookup"><span data-stu-id="691d2-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="691d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="691d2-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="691d2-105">參數</span><span class="sxs-lookup"><span data-stu-id="691d2-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="691d2-106">[out]`true`此執行階段是否已啟動，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="691d2-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="691d2-107">[out]傳回用來啟動執行階段旗標。</span><span class="sxs-lookup"><span data-stu-id="691d2-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="691d2-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="691d2-108">Return Value</span></span>  
 <span data-ttu-id="691d2-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="691d2-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="691d2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="691d2-110">HRESULT</span></span>|<span data-ttu-id="691d2-111">描述</span><span class="sxs-lookup"><span data-stu-id="691d2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="691d2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="691d2-112">S_OK</span></span>|<span data-ttu-id="691d2-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="691d2-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="691d2-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="691d2-114">E_NOTIMPL</span></span>|<span data-ttu-id="691d2-115">Common language runtime (CLR) 版本中的 CLR 版本低於[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="691d2-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="691d2-116">備註</span><span class="sxs-lookup"><span data-stu-id="691d2-116">Remarks</span></span>  
 <span data-ttu-id="691d2-117">這個方法不適用於 CLR 版本早於中的 CLR 版本[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="691d2-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="691d2-118">需求</span><span class="sxs-lookup"><span data-stu-id="691d2-118">Requirements</span></span>  
 <span data-ttu-id="691d2-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="691d2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="691d2-120">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="691d2-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="691d2-121">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="691d2-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="691d2-122">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="691d2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691d2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="691d2-123">See also</span></span>
- [<span data-ttu-id="691d2-124">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="691d2-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="691d2-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="691d2-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="691d2-126">裝載</span><span class="sxs-lookup"><span data-stu-id="691d2-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
