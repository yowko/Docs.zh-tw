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
ms.openlocfilehash: 13b4e00cf002abca625dbdda010f7d8994360687
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762535"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="ec412-102">ICLRRuntimeInfo::IsLoadable 方法</span><span class="sxs-lookup"><span data-stu-id="ec412-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="ec412-103">指出與這個介面相關聯的執行時間是否可以載入目前的進程中，並考慮可能已經載入進程的其他執行時間。</span><span class="sxs-lookup"><span data-stu-id="ec412-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec412-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec412-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec412-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec412-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="ec412-106">[out] `true`如果此執行時間可以載入至目前的進程，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ec412-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec412-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ec412-107">Return Value</span></span>  
 <span data-ttu-id="ec412-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ec412-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ec412-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec412-109">HRESULT</span></span>|<span data-ttu-id="ec412-110">Description</span><span class="sxs-lookup"><span data-stu-id="ec412-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec412-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec412-111">S_OK</span></span>|<span data-ttu-id="ec412-112">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="ec412-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="ec412-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ec412-113">E_POINTER</span></span>|<span data-ttu-id="ec412-114">`pbLoadable` 為 null。</span><span class="sxs-lookup"><span data-stu-id="ec412-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec412-115">備註</span><span class="sxs-lookup"><span data-stu-id="ec412-115">Remarks</span></span>  
 <span data-ttu-id="ec412-116">如果另一個執行時間已載入進程，而且可以載入與此介面相關聯的執行時間，以進行同進程並存執行，會傳回 `pbLoadable` `true` 。</span><span class="sxs-lookup"><span data-stu-id="ec412-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="ec412-117">如果這兩個執行時間無法並行在進程中執行，則會 `pbLoadable` 傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ec412-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="ec412-118">例如，common language runtime （CLR）第4版可以在 CLR 版本2.0 或 CLR 1.1 版的相同進程中並存執行。</span><span class="sxs-lookup"><span data-stu-id="ec412-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="ec412-119">不過，CLR 版本1.1 和 CLR 版本2.0 無法並存執行同進程。</span><span class="sxs-lookup"><span data-stu-id="ec412-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="ec412-120">如果未將執行時間載入進程中，這個方法一律會傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="ec412-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec412-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="ec412-121">Requirements</span></span>  
 <span data-ttu-id="ec412-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec412-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec412-123">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="ec412-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ec412-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ec412-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec412-125">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec412-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec412-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec412-126">See also</span></span>

- [<span data-ttu-id="ec412-127">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ec412-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ec412-128">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ec412-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ec412-129">裝載</span><span class="sxs-lookup"><span data-stu-id="ec412-129">Hosting</span></span>](index.md)
