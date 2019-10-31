---
title: ICLRMetaHost::EnumerateLoadedRuntimes 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: f89307ad7ed41f872ad66a99be03663ac1f30f13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140979"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="41c13-102">ICLRMetaHost::EnumerateLoadedRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="41c13-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="41c13-103">傳回列舉，其中包含在給定進程中載入之每個 common language runtime （CLR）版本的有效[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面指標。</span><span class="sxs-lookup"><span data-stu-id="41c13-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="41c13-104">這個方法會取代[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="41c13-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c13-105">語法</span><span class="sxs-lookup"><span data-stu-id="41c13-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41c13-106">參數</span><span class="sxs-lookup"><span data-stu-id="41c13-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="41c13-107">在要檢查載入的執行時間之進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="41c13-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="41c13-108">脫銷[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面的 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> 列舉，其對應于處理常式所載入的每個 CLR。</span><span class="sxs-lookup"><span data-stu-id="41c13-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41c13-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="41c13-109">Return Value</span></span>  
 <span data-ttu-id="41c13-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="41c13-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="41c13-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41c13-111">HRESULT</span></span>|<span data-ttu-id="41c13-112">描述</span><span class="sxs-lookup"><span data-stu-id="41c13-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41c13-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="41c13-113">S_OK</span></span>|<span data-ttu-id="41c13-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="41c13-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="41c13-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="41c13-115">E_POINTER</span></span>|<span data-ttu-id="41c13-116">`ppEnumerator` 為 null。</span><span class="sxs-lookup"><span data-stu-id="41c13-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41c13-117">備註</span><span class="sxs-lookup"><span data-stu-id="41c13-117">Remarks</span></span>  
 <span data-ttu-id="41c13-118">這個方法會列出所有載入的執行時間，即使它們是使用已被取代的函式（例如[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)）載入也是一樣。</span><span class="sxs-lookup"><span data-stu-id="41c13-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c13-119">需求</span><span class="sxs-lookup"><span data-stu-id="41c13-119">Requirements</span></span>  
 <span data-ttu-id="41c13-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41c13-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c13-121">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="41c13-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="41c13-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="41c13-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41c13-123">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c13-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c13-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="41c13-124">See also</span></span>

- [<span data-ttu-id="41c13-125">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="41c13-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="41c13-126">裝載</span><span class="sxs-lookup"><span data-stu-id="41c13-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
