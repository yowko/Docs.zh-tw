---
title: ICLRRuntimeInfo::LoadLibrary 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7dbcbf1b66793a67c815b420e6d5fe221febe719
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716878"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="7bccb-102">ICLRRuntimeInfo::LoadLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="7bccb-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="7bccb-103">從 common language runtime (CLR) 所表示載入的.NET Framework 程式庫[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="7bccb-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="7bccb-104">這個方法會取代[LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="7bccb-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bccb-105">語法</span><span class="sxs-lookup"><span data-stu-id="7bccb-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bccb-106">參數</span><span class="sxs-lookup"><span data-stu-id="7bccb-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="7bccb-107">[in]要載入之組件名稱。</span><span class="sxs-lookup"><span data-stu-id="7bccb-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="7bccb-108">[out]載入的組件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="7bccb-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bccb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7bccb-109">Return Value</span></span>  
 <span data-ttu-id="7bccb-110">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7bccb-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7bccb-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bccb-111">HRESULT</span></span>|<span data-ttu-id="7bccb-112">描述</span><span class="sxs-lookup"><span data-stu-id="7bccb-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bccb-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bccb-113">S_OK</span></span>|<span data-ttu-id="7bccb-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="7bccb-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7bccb-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7bccb-115">E_POINTER</span></span>|<span data-ttu-id="7bccb-116">`pwzDllName` 或 `phndModule` 為 null。</span><span class="sxs-lookup"><span data-stu-id="7bccb-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="7bccb-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7bccb-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7bccb-118">沒有足夠的記憶體是可用來處理要求。</span><span class="sxs-lookup"><span data-stu-id="7bccb-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bccb-119">備註</span><span class="sxs-lookup"><span data-stu-id="7bccb-119">Remarks</span></span>  
 <span data-ttu-id="7bccb-120">這個方法只會載入 Dll 包含在.NET Framework 可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="7bccb-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="7bccb-121">它無法載入使用者產生的組件。</span><span class="sxs-lookup"><span data-stu-id="7bccb-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bccb-122">需求</span><span class="sxs-lookup"><span data-stu-id="7bccb-122">Requirements</span></span>  
 <span data-ttu-id="7bccb-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bccb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bccb-124">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7bccb-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7bccb-125">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7bccb-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bccb-126">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bccb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bccb-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bccb-127">See also</span></span>
- [<span data-ttu-id="7bccb-128">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="7bccb-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7bccb-129">裝載介面</span><span class="sxs-lookup"><span data-stu-id="7bccb-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7bccb-130">裝載</span><span class="sxs-lookup"><span data-stu-id="7bccb-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
