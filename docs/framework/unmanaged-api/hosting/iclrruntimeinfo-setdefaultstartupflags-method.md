---
title: ICLRRuntimeInfo::SetDefaultStartupFlags 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: 36851ac4573d0d65caffaa3f82a1f6fc8440a2d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092746"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="c31e5-102">ICLRRuntimeInfo::SetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="c31e5-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="c31e5-103">設定將用來啟動執行時間的啟動旗標和主機設定檔。</span><span class="sxs-lookup"><span data-stu-id="c31e5-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="c31e5-104">這個方法會取代[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)和[CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)函式中的 `startupFlags` 參數用法。</span><span class="sxs-lookup"><span data-stu-id="c31e5-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c31e5-105">語法</span><span class="sxs-lookup"><span data-stu-id="c31e5-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c31e5-106">參數</span><span class="sxs-lookup"><span data-stu-id="c31e5-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="c31e5-107">在要設定的主機啟動旗標。</span><span class="sxs-lookup"><span data-stu-id="c31e5-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="c31e5-108">使用與[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)和[CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)函數相同的旗標。</span><span class="sxs-lookup"><span data-stu-id="c31e5-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="c31e5-109">在要設定的主機設定檔的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="c31e5-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c31e5-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="c31e5-110">Return Value</span></span>  
 <span data-ttu-id="c31e5-111">這個方法會傳回下列特定的 HRESULT，以及指出方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c31e5-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c31e5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c31e5-112">HRESULT</span></span>|<span data-ttu-id="c31e5-113">描述</span><span class="sxs-lookup"><span data-stu-id="c31e5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c31e5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c31e5-114">S_OK</span></span>|<span data-ttu-id="c31e5-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="c31e5-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c31e5-116">備註</span><span class="sxs-lookup"><span data-stu-id="c31e5-116">Remarks</span></span>  
 <span data-ttu-id="c31e5-117">多執行緒主機應該同步處理這個方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="c31e5-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="c31e5-118">否則，執行緒 A 可能會線上程 B 完成呼叫 `SetStartupFlags` 以及執行緒 B 啟動執行時間之前，呼叫 `SetStartupFlags` 方法。</span><span class="sxs-lookup"><span data-stu-id="c31e5-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c31e5-119">需求</span><span class="sxs-lookup"><span data-stu-id="c31e5-119">Requirements</span></span>  
 <span data-ttu-id="c31e5-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c31e5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c31e5-121">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="c31e5-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c31e5-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c31e5-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c31e5-123">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c31e5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c31e5-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="c31e5-124">See also</span></span>

- [<span data-ttu-id="c31e5-125">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c31e5-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c31e5-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="c31e5-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="c31e5-127">裝載</span><span class="sxs-lookup"><span data-stu-id="c31e5-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
