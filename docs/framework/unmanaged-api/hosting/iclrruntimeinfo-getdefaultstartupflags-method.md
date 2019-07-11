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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aeb4c9935d5e9e4063497dd56276edfe6e62752a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765595"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="9c663-102">ICLRRuntimeInfo::GetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="9c663-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="9c663-103">取得啟動旗標和將用來啟動執行階段的主機組態檔。</span><span class="sxs-lookup"><span data-stu-id="9c663-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c663-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c663-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c663-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c663-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="9c663-106">[out]目前所設定的主機啟動旗標指標。</span><span class="sxs-lookup"><span data-stu-id="9c663-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="9c663-107">[out]目前的主機組態檔的目錄路徑指標。</span><span class="sxs-lookup"><span data-stu-id="9c663-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="9c663-108">[in、 out]在輸入的大小`pwzHostConfigFile`，以避免緩衝區溢位。</span><span class="sxs-lookup"><span data-stu-id="9c663-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="9c663-109">如果`pwzHostConfigFile`是 null，此方法傳回的所需的大小`pwzHostConfigFile`的預先配置。</span><span class="sxs-lookup"><span data-stu-id="9c663-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c663-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="9c663-110">Return Value</span></span>  
 <span data-ttu-id="9c663-111">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9c663-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9c663-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c663-112">HRESULT</span></span>|<span data-ttu-id="9c663-113">說明</span><span class="sxs-lookup"><span data-stu-id="9c663-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c663-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c663-114">S_OK</span></span>|<span data-ttu-id="9c663-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="9c663-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c663-116">備註</span><span class="sxs-lookup"><span data-stu-id="9c663-116">Remarks</span></span>  
 <span data-ttu-id="9c663-117">這個方法會傳回預設的旗標值 (`STARTUP_CONCURRENT_GC`並`NULL`)，或由先前呼叫所提供的值[iclrruntimeinfo:: Setdefaultstartupflags 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)，或由任一設定的值`CorBind*`如果此執行階段繫結的方法。</span><span class="sxs-lookup"><span data-stu-id="9c663-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c663-118">需求</span><span class="sxs-lookup"><span data-stu-id="9c663-118">Requirements</span></span>  
 <span data-ttu-id="9c663-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c663-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c663-120">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9c663-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9c663-121">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9c663-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c663-122">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c663-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c663-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c663-123">See also</span></span>

- [<span data-ttu-id="9c663-124">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="9c663-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="9c663-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9c663-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="9c663-126">裝載</span><span class="sxs-lookup"><span data-stu-id="9c663-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
