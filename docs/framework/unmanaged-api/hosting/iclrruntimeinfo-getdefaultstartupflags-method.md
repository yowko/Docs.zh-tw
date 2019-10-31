---
title: ICLRRuntimeInfo::GetDefaultStartupFlags 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: 0ce822533b0699f3467dc08044aa4dab59285a77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120306"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="24838-102">ICLRRuntimeInfo::GetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="24838-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="24838-103">取得將用來啟動執行時間的啟動旗標和主機設定檔。</span><span class="sxs-lookup"><span data-stu-id="24838-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24838-104">語法</span><span class="sxs-lookup"><span data-stu-id="24838-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24838-105">參數</span><span class="sxs-lookup"><span data-stu-id="24838-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="24838-106">脫銷目前設定之主機啟動旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="24838-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="24838-107">脫銷目前主機設定檔的目錄路徑指標。</span><span class="sxs-lookup"><span data-stu-id="24838-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="24838-108">[in、out]輸入時，`pwzHostConfigFile`的大小，以避免緩衝區溢位。</span><span class="sxs-lookup"><span data-stu-id="24838-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="24838-109">如果 `pwzHostConfigFile` 為 null，此方法會傳回預先配置所需的 `pwzHostConfigFile` 大小。</span><span class="sxs-lookup"><span data-stu-id="24838-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24838-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="24838-110">Return Value</span></span>  
 <span data-ttu-id="24838-111">這個方法會傳回下列特定的 HRESULT，以及指出方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="24838-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="24838-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24838-112">HRESULT</span></span>|<span data-ttu-id="24838-113">描述</span><span class="sxs-lookup"><span data-stu-id="24838-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24838-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="24838-114">S_OK</span></span>|<span data-ttu-id="24838-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="24838-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24838-116">備註</span><span class="sxs-lookup"><span data-stu-id="24838-116">Remarks</span></span>  
 <span data-ttu-id="24838-117">這個方法會傳回預設旗標值（`STARTUP_CONCURRENT_GC` 和 `NULL`），或先前呼叫[ICLRRuntimeInfo：： SetDefaultStartupFlags 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)所提供的值，或者，如果系結至這個執行時間，則為任何 `CorBind*` 方法所設定的值。</span><span class="sxs-lookup"><span data-stu-id="24838-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24838-118">需求</span><span class="sxs-lookup"><span data-stu-id="24838-118">Requirements</span></span>  
 <span data-ttu-id="24838-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24838-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24838-120">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="24838-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="24838-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="24838-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24838-122">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24838-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24838-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="24838-123">See also</span></span>

- [<span data-ttu-id="24838-124">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="24838-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="24838-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="24838-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="24838-126">裝載</span><span class="sxs-lookup"><span data-stu-id="24838-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
