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
ms.openlocfilehash: 8513787f48ae89632816face386bbcda20555dac
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703880"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="ebac4-102">ICLRRuntimeInfo::GetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="ebac4-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="ebac4-103">取得將用來啟動執行時間的啟動旗標和主機設定檔。</span><span class="sxs-lookup"><span data-stu-id="ebac4-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebac4-104">語法</span><span class="sxs-lookup"><span data-stu-id="ebac4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebac4-105">參數</span><span class="sxs-lookup"><span data-stu-id="ebac4-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="ebac4-106">脫銷目前設定之主機啟動旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="ebac4-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="ebac4-107">脫銷目前主機設定檔的目錄路徑指標。</span><span class="sxs-lookup"><span data-stu-id="ebac4-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="ebac4-108">[in、out]在輸入時，為的大小 `pwzHostConfigFile` ，以避免緩衝區溢位。</span><span class="sxs-lookup"><span data-stu-id="ebac4-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="ebac4-109">如果 `pwzHostConfigFile` 為 null，則方法會針對預先配置傳回所需的大小 `pwzHostConfigFile` 。</span><span class="sxs-lookup"><span data-stu-id="ebac4-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebac4-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="ebac4-110">Return Value</span></span>  
 <span data-ttu-id="ebac4-111">這個方法會傳回下列特定的 HRESULT，以及指出方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ebac4-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ebac4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ebac4-112">HRESULT</span></span>|<span data-ttu-id="ebac4-113">說明</span><span class="sxs-lookup"><span data-stu-id="ebac4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ebac4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ebac4-114">S_OK</span></span>|<span data-ttu-id="ebac4-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="ebac4-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebac4-116">備註</span><span class="sxs-lookup"><span data-stu-id="ebac4-116">Remarks</span></span>  
 <span data-ttu-id="ebac4-117">這個方法會傳回預設旗標值（ `STARTUP_CONCURRENT_GC` 和 `NULL` ），或是先前呼叫[ICLRRuntimeInfo：： SetDefaultStartupFlags 方法](iclrruntimeinfo-setdefaultstartupflags-method.md)所提供的值，或者，如果系結至此執行時間，則為任何方法所設定的值 `CorBind*` 。</span><span class="sxs-lookup"><span data-stu-id="ebac4-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebac4-118">需求</span><span class="sxs-lookup"><span data-stu-id="ebac4-118">Requirements</span></span>  
 <span data-ttu-id="ebac4-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ebac4-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebac4-120">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="ebac4-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ebac4-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ebac4-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebac4-122">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebac4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebac4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebac4-123">See also</span></span>

- [<span data-ttu-id="ebac4-124">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ebac4-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ebac4-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ebac4-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ebac4-126">裝載</span><span class="sxs-lookup"><span data-stu-id="ebac4-126">Hosting</span></span>](index.md)
