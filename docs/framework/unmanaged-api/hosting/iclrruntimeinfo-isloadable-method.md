---
title: ICLRRuntimeInfo::IsLoadable 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52257b30b8172b80f968df25115956b6995c1552
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101584"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="fca96-102">ICLRRuntimeInfo::IsLoadable 方法</span><span class="sxs-lookup"><span data-stu-id="fca96-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="fca96-103">指出此介面相關聯的執行階段是否可以載入到目前的程序，並考慮其他可能會載入到處理序的執行階段。</span><span class="sxs-lookup"><span data-stu-id="fca96-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fca96-104">語法</span><span class="sxs-lookup"><span data-stu-id="fca96-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fca96-105">參數</span><span class="sxs-lookup"><span data-stu-id="fca96-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="fca96-106">[out]`true`如果此執行階段無法載入目前的處理序，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="fca96-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fca96-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fca96-107">Return Value</span></span>  
 <span data-ttu-id="fca96-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="fca96-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fca96-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fca96-109">HRESULT</span></span>|<span data-ttu-id="fca96-110">描述</span><span class="sxs-lookup"><span data-stu-id="fca96-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fca96-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fca96-111">S_OK</span></span>|<span data-ttu-id="fca96-112">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="fca96-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="fca96-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="fca96-113">E_POINTER</span></span>|<span data-ttu-id="fca96-114">`pbLoadable` 為 null。</span><span class="sxs-lookup"><span data-stu-id="fca96-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fca96-115">備註</span><span class="sxs-lookup"><span data-stu-id="fca96-115">Remarks</span></span>  
 <span data-ttu-id="fca96-116">如果另一個執行階段已載入處理序，並且此介面相關聯的執行階段可以載入內含式並排顯示執行中，`pbLoadable`傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="fca96-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="fca96-117">如果兩個執行階段無法執行並排顯示同處理序，`pbLoadable`傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="fca96-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="fca96-118">例如，在相同的程序，與 CLR 2.0 版中並行或 CLR 1.1 版，可以執行 common language runtime (CLR) 第 4 版。</span><span class="sxs-lookup"><span data-stu-id="fca96-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="fca96-119">不過，CLR 1.1 版和 CLR 2.0 版才能執行並排顯示同處理序。</span><span class="sxs-lookup"><span data-stu-id="fca96-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="fca96-120">如果沒有執行階段載入處理序，此方法一律會傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="fca96-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fca96-121">需求</span><span class="sxs-lookup"><span data-stu-id="fca96-121">Requirements</span></span>  
 <span data-ttu-id="fca96-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fca96-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fca96-123">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fca96-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fca96-124">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fca96-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fca96-125">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fca96-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca96-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fca96-126">See also</span></span>

- [<span data-ttu-id="fca96-127">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="fca96-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="fca96-128">裝載介面</span><span class="sxs-lookup"><span data-stu-id="fca96-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="fca96-129">裝載</span><span class="sxs-lookup"><span data-stu-id="fca96-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
