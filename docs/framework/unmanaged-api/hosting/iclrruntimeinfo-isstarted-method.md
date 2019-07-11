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
ms.openlocfilehash: 5b064f0b1cec07f29058300041711285bde66697
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748410"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="39032-102">ICLRRuntimeInfo::IsStarted 方法</span><span class="sxs-lookup"><span data-stu-id="39032-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="39032-103">指出是否已啟動執行階段 (亦即是否[iclrruntimehost:: Start 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)被呼叫，且已成功)。</span><span class="sxs-lookup"><span data-stu-id="39032-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39032-104">語法</span><span class="sxs-lookup"><span data-stu-id="39032-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39032-105">參數</span><span class="sxs-lookup"><span data-stu-id="39032-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="39032-106">[out]`true`此執行階段是否已啟動，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="39032-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="39032-107">[out]傳回用來啟動執行階段旗標。</span><span class="sxs-lookup"><span data-stu-id="39032-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39032-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="39032-108">Return Value</span></span>  
 <span data-ttu-id="39032-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="39032-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="39032-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="39032-110">HRESULT</span></span>|<span data-ttu-id="39032-111">描述</span><span class="sxs-lookup"><span data-stu-id="39032-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="39032-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="39032-112">S_OK</span></span>|<span data-ttu-id="39032-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="39032-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="39032-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="39032-114">E_NOTIMPL</span></span>|<span data-ttu-id="39032-115">Common language runtime (CLR) 版本低於.NET Framework 4 中的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="39032-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39032-116">備註</span><span class="sxs-lookup"><span data-stu-id="39032-116">Remarks</span></span>  
 <span data-ttu-id="39032-117">這個方法不適用於 CLR 版本早於.NET Framework 4 中的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="39032-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39032-118">需求</span><span class="sxs-lookup"><span data-stu-id="39032-118">Requirements</span></span>  
 <span data-ttu-id="39032-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39032-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39032-120">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="39032-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="39032-121">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="39032-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39032-122">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39032-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39032-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39032-123">See also</span></span>

- [<span data-ttu-id="39032-124">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="39032-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="39032-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="39032-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="39032-126">裝載</span><span class="sxs-lookup"><span data-stu-id="39032-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
