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
ms.openlocfilehash: e8e50a018016b885a3513cbd885b8e5115f18113
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432917"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="06fb9-102">ICLRRuntimeInfo::GetProcAddress 方法</span><span class="sxs-lookup"><span data-stu-id="06fb9-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="06fb9-103">取得指定的函式匯出從 common language runtime (CLR) 此介面相關聯的位址。</span><span class="sxs-lookup"><span data-stu-id="06fb9-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="06fb9-104">這個方法會取代[GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="06fb9-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06fb9-105">語法</span><span class="sxs-lookup"><span data-stu-id="06fb9-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06fb9-106">參數</span><span class="sxs-lookup"><span data-stu-id="06fb9-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="06fb9-107">[in]匯出的函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="06fb9-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="06fb9-108">[out]匯出的函式的位址。</span><span class="sxs-lookup"><span data-stu-id="06fb9-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06fb9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="06fb9-109">Return Value</span></span>  
 <span data-ttu-id="06fb9-110">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="06fb9-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="06fb9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06fb9-111">HRESULT</span></span>|<span data-ttu-id="06fb9-112">描述</span><span class="sxs-lookup"><span data-stu-id="06fb9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06fb9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="06fb9-113">S_OK</span></span>|<span data-ttu-id="06fb9-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="06fb9-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="06fb9-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="06fb9-115">E_POINTER</span></span>|<span data-ttu-id="06fb9-116">`pszProcName` 或 `ppProc` 為 null。</span><span class="sxs-lookup"><span data-stu-id="06fb9-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="06fb9-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="06fb9-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="06fb9-118">指定的函式不是匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="06fb9-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06fb9-119">備註</span><span class="sxs-lookup"><span data-stu-id="06fb9-119">Remarks</span></span>  
 <span data-ttu-id="06fb9-120">這個方法會導致 CLR 載入，但未初始化。</span><span class="sxs-lookup"><span data-stu-id="06fb9-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06fb9-121">需求</span><span class="sxs-lookup"><span data-stu-id="06fb9-121">Requirements</span></span>  
 <span data-ttu-id="06fb9-122">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06fb9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06fb9-123">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="06fb9-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="06fb9-124">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="06fb9-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06fb9-125">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06fb9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06fb9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06fb9-126">See Also</span></span>  
 [<span data-ttu-id="06fb9-127">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="06fb9-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="06fb9-128">裝載介面</span><span class="sxs-lookup"><span data-stu-id="06fb9-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="06fb9-129">裝載</span><span class="sxs-lookup"><span data-stu-id="06fb9-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
