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
ms.openlocfilehash: 34590744407b25d7d53c06c452fff5bac2a95246
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136391"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="d3acf-102">ICLRRuntimeInfo::IsStarted 方法</span><span class="sxs-lookup"><span data-stu-id="d3acf-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="d3acf-103">指出執行時間是否已啟動（也就是是否已呼叫[ICLRRuntimeHost：： Start 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)且已成功）。</span><span class="sxs-lookup"><span data-stu-id="d3acf-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3acf-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3acf-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3acf-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3acf-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="d3acf-106">[out] `true` 如果已啟動此執行時間，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="d3acf-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="d3acf-107">脫銷傳回用來啟動執行時間的旗標。</span><span class="sxs-lookup"><span data-stu-id="d3acf-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3acf-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d3acf-108">Return Value</span></span>  
 <span data-ttu-id="d3acf-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3acf-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d3acf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3acf-110">HRESULT</span></span>|<span data-ttu-id="d3acf-111">描述</span><span class="sxs-lookup"><span data-stu-id="d3acf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3acf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3acf-112">S_OK</span></span>|<span data-ttu-id="d3acf-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="d3acf-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="d3acf-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d3acf-114">E_NOTIMPL</span></span>|<span data-ttu-id="d3acf-115">Common language runtime （CLR）版本早于 .NET Framework 4 中的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="d3acf-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3acf-116">備註</span><span class="sxs-lookup"><span data-stu-id="d3acf-116">Remarks</span></span>  
 <span data-ttu-id="d3acf-117">這個方法無法與 .NET Framework 4 中 CLR 版本之前的 CLR 版本搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d3acf-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3acf-118">需求</span><span class="sxs-lookup"><span data-stu-id="d3acf-118">Requirements</span></span>  
 <span data-ttu-id="d3acf-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3acf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3acf-120">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="d3acf-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d3acf-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d3acf-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3acf-122">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3acf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3acf-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="d3acf-123">See also</span></span>

- [<span data-ttu-id="d3acf-124">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="d3acf-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="d3acf-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d3acf-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d3acf-126">裝載</span><span class="sxs-lookup"><span data-stu-id="d3acf-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
