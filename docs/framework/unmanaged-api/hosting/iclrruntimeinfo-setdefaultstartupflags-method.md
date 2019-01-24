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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d021eb2d8da8c85fe538f0c73527876482429718
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656878"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="cf21d-102">ICLRRuntimeInfo::SetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="cf21d-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="cf21d-103">設定啟動旗標和將用來啟動執行階段主應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="cf21d-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="cf21d-104">這個方法會取代使用`startupFlags`中的參數[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)並[CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="cf21d-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf21d-105">語法</span><span class="sxs-lookup"><span data-stu-id="cf21d-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf21d-106">參數</span><span class="sxs-lookup"><span data-stu-id="cf21d-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="cf21d-107">[in]若要設定主應用程式啟動旗標。</span><span class="sxs-lookup"><span data-stu-id="cf21d-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="cf21d-108">使用相同的旗標做為與[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)並[CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="cf21d-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="cf21d-109">[in]若要設定主應用程式組態檔的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="cf21d-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf21d-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="cf21d-110">Return Value</span></span>  
 <span data-ttu-id="cf21d-111">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="cf21d-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cf21d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf21d-112">HRESULT</span></span>|<span data-ttu-id="cf21d-113">描述</span><span class="sxs-lookup"><span data-stu-id="cf21d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf21d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf21d-114">S_OK</span></span>|<span data-ttu-id="cf21d-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="cf21d-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf21d-116">備註</span><span class="sxs-lookup"><span data-stu-id="cf21d-116">Remarks</span></span>  
 <span data-ttu-id="cf21d-117">多執行緒的主機應該同步處理對此方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="cf21d-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="cf21d-118">執行緒 A 可能會呼叫，否則為`SetStartupFlags`方法，執行緒 B 完成呼叫之後`SetStartupFlags`和執行緒 B 開始執行階段之前。</span><span class="sxs-lookup"><span data-stu-id="cf21d-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf21d-119">需求</span><span class="sxs-lookup"><span data-stu-id="cf21d-119">Requirements</span></span>  
 <span data-ttu-id="cf21d-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf21d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf21d-121">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cf21d-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cf21d-122">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cf21d-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf21d-123">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf21d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf21d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf21d-124">See also</span></span>
- [<span data-ttu-id="cf21d-125">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="cf21d-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="cf21d-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="cf21d-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="cf21d-127">裝載</span><span class="sxs-lookup"><span data-stu-id="cf21d-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
