---
title: ICLRRuntimeInfo::GetProcAddress 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a95b6b7e20bbcd86dedf187c932f2cf74d37cdab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199176"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="4e30a-102">ICLRRuntimeInfo::GetProcAddress 方法</span><span class="sxs-lookup"><span data-stu-id="4e30a-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="4e30a-103">取得指定的函式匯出從 common language runtime (CLR) 與此介面相關聯的位址。</span><span class="sxs-lookup"><span data-stu-id="4e30a-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="4e30a-104">這個方法會取代[GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="4e30a-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e30a-105">語法</span><span class="sxs-lookup"><span data-stu-id="4e30a-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e30a-106">參數</span><span class="sxs-lookup"><span data-stu-id="4e30a-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="4e30a-107">[in]匯出的函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e30a-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="4e30a-108">[out]匯出的函式的位址。</span><span class="sxs-lookup"><span data-stu-id="4e30a-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e30a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="4e30a-109">Return Value</span></span>  
 <span data-ttu-id="4e30a-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="4e30a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4e30a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4e30a-111">HRESULT</span></span>|<span data-ttu-id="4e30a-112">描述</span><span class="sxs-lookup"><span data-stu-id="4e30a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4e30a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4e30a-113">S_OK</span></span>|<span data-ttu-id="4e30a-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="4e30a-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="4e30a-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4e30a-115">E_POINTER</span></span>|`pszProcName` <span data-ttu-id="4e30a-116">或`ppProc`為 null。</span><span class="sxs-lookup"><span data-stu-id="4e30a-116">or `ppProc` is null.</span></span>|  
|<span data-ttu-id="4e30a-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="4e30a-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="4e30a-118">指定的函式不是匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="4e30a-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e30a-119">備註</span><span class="sxs-lookup"><span data-stu-id="4e30a-119">Remarks</span></span>  
 <span data-ttu-id="4e30a-120">這個方法會導致 CLR 載入，但未初始化。</span><span class="sxs-lookup"><span data-stu-id="4e30a-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e30a-121">需求</span><span class="sxs-lookup"><span data-stu-id="4e30a-121">Requirements</span></span>  
 <span data-ttu-id="4e30a-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e30a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e30a-123">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4e30a-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4e30a-124">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4e30a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4e30a-125">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="4e30a-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e30a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e30a-126">See also</span></span>

- [<span data-ttu-id="4e30a-127">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4e30a-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="4e30a-128">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4e30a-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4e30a-129">裝載</span><span class="sxs-lookup"><span data-stu-id="4e30a-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
