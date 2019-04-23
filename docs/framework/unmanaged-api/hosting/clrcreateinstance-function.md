---
title: CLRCreateInstance 函式
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3571e2698b980b12b89a5b689efb868a34a3ef71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167657"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="c9710-102">CLRCreateInstance 函式</span><span class="sxs-lookup"><span data-stu-id="c9710-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="c9710-103">提供三個介面之一：[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)， [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)，或[ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="c9710-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9710-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9710-104">Syntax</span></span>  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9710-105">參數</span><span class="sxs-lookup"><span data-stu-id="c9710-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="c9710-106">[in]其中三個類別識別碼：CLSID_CLRMetaHost、 CLSID_CLRMetaHostPolicy 或 CLSID_CLRDebugging。</span><span class="sxs-lookup"><span data-stu-id="c9710-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="c9710-107">[in]三個介面識別碼 (Iid) 其中一項：IID_ICLRMetaHost、 IID_ICLRMetaHostPolicy 或 IID_ICLRDebugging。</span><span class="sxs-lookup"><span data-stu-id="c9710-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="c9710-108">[out]其中的三個介面：[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)， [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)，或[ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="c9710-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9710-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c9710-109">Return Value</span></span>  
 <span data-ttu-id="c9710-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c9710-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c9710-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9710-111">HRESULT</span></span>|<span data-ttu-id="c9710-112">描述</span><span class="sxs-lookup"><span data-stu-id="c9710-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9710-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9710-113">S_OK</span></span>|<span data-ttu-id="c9710-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="c9710-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="c9710-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c9710-115">E_POINTER</span></span>|<span data-ttu-id="c9710-116">`ppInterface` 為 null。</span><span class="sxs-lookup"><span data-stu-id="c9710-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9710-117">備註</span><span class="sxs-lookup"><span data-stu-id="c9710-117">Remarks</span></span>  
 <span data-ttu-id="c9710-118">下表顯示支援的組合，如`clsid`和`riid`。</span><span class="sxs-lookup"><span data-stu-id="c9710-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="c9710-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="c9710-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="c9710-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="c9710-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="c9710-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="c9710-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="c9710-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="c9710-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="c9710-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="c9710-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="c9710-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="c9710-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="c9710-125">下列程式碼示範如何使用`CLRCreateInstance`取得所有的三個介面：</span><span class="sxs-lookup"><span data-stu-id="c9710-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c9710-126">需求</span><span class="sxs-lookup"><span data-stu-id="c9710-126">Requirements</span></span>  
 <span data-ttu-id="c9710-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9710-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9710-128">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c9710-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c9710-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c9710-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9710-130">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9710-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9710-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9710-131">See also</span></span>

- [<span data-ttu-id="c9710-132">裝載</span><span class="sxs-lookup"><span data-stu-id="c9710-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
