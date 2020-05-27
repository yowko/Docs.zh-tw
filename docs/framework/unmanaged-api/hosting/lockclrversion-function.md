---
title: LockClrVersion 函式
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
ms.openlocfilehash: 09bcebfdcfea3d5728d404cdb6b5fb170a5432c3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008491"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="013ae-102">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="013ae-102">LockClrVersion Function</span></span>
<span data-ttu-id="013ae-103">允許主機判斷在明確初始化 CLR 之前，將在進程中使用哪個版本的 common language runtime （CLR）。</span><span class="sxs-lookup"><span data-stu-id="013ae-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="013ae-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="013ae-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="013ae-105">語法</span><span class="sxs-lookup"><span data-stu-id="013ae-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="013ae-106">參數</span><span class="sxs-lookup"><span data-stu-id="013ae-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="013ae-107">在要在初始化時由 CLR 呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="013ae-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="013ae-108">在主機要呼叫的函式，以通知 CLR 初始化正在啟動。</span><span class="sxs-lookup"><span data-stu-id="013ae-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="013ae-109">在主機要呼叫的函式，以通知 CLR 初始化已完成。</span><span class="sxs-lookup"><span data-stu-id="013ae-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="013ae-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="013ae-110">Return Value</span></span>  
 <span data-ttu-id="013ae-111">這個方法會傳回標準 COM 錯誤碼（如 Winerror.h 中所定義），以及下列值。</span><span class="sxs-lookup"><span data-stu-id="013ae-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="013ae-112">傳回碼</span><span class="sxs-lookup"><span data-stu-id="013ae-112">Return code</span></span>|<span data-ttu-id="013ae-113">描述</span><span class="sxs-lookup"><span data-stu-id="013ae-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="013ae-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="013ae-114">S_OK</span></span>|<span data-ttu-id="013ae-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="013ae-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="013ae-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="013ae-116">E_INVALIDARG</span></span>|<span data-ttu-id="013ae-117">一或多個引數為 null。</span><span class="sxs-lookup"><span data-stu-id="013ae-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="013ae-118">備註</span><span class="sxs-lookup"><span data-stu-id="013ae-118">Remarks</span></span>  
 <span data-ttu-id="013ae-119">主機會在 `LockClrVersion` 初始化 CLR 之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="013ae-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="013ae-120">`LockClrVersion`採用三個參數，這些都是[FLockClrVersionCallback](flockclrversioncallback-function-pointer.md)類型的回呼。</span><span class="sxs-lookup"><span data-stu-id="013ae-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="013ae-121">此類型的定義如下。</span><span class="sxs-lookup"><span data-stu-id="013ae-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="013ae-122">初始化執行時間時，會發生下列步驟：</span><span class="sxs-lookup"><span data-stu-id="013ae-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="013ae-123">主機會呼叫[CorBindToRuntimeEx](corbindtoruntimeex-function.md)或其中一個其他執行時間初始化函數。</span><span class="sxs-lookup"><span data-stu-id="013ae-123">The host calls [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="013ae-124">或者，主機也可以使用 COM 物件啟用來初始化執行時間。</span><span class="sxs-lookup"><span data-stu-id="013ae-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="013ae-125">執行時間會呼叫參數所指定的函式 `hostCallback` 。</span><span class="sxs-lookup"><span data-stu-id="013ae-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="013ae-126">所指定的函式 `hostCallback` 會進行下列一連串的呼叫：</span><span class="sxs-lookup"><span data-stu-id="013ae-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="013ae-127">參數所指定的函式 `pBeginHostSetup` 。</span><span class="sxs-lookup"><span data-stu-id="013ae-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="013ae-128">`CorBindToRuntimeEx`（或另一個執行時間初始化函數）。</span><span class="sxs-lookup"><span data-stu-id="013ae-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="013ae-129">[ICLRRuntimeHost：： SetHostControl](iclrruntimehost-sethostcontrol-method.md)。</span><span class="sxs-lookup"><span data-stu-id="013ae-129">[ICLRRuntimeHost::SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="013ae-130">[ICLRRuntimeHost：： Start](iclrruntimehost-start-method.md)。</span><span class="sxs-lookup"><span data-stu-id="013ae-130">[ICLRRuntimeHost::Start](iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="013ae-131">參數所指定的函式 `pEndHostSetup` 。</span><span class="sxs-lookup"><span data-stu-id="013ae-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="013ae-132">所有從到的呼叫都 `pBeginHostSetup` `pEndHostSetup` 必須在具有相同邏輯堆疊的單一執行緒或光纖上發生。</span><span class="sxs-lookup"><span data-stu-id="013ae-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="013ae-133">這個執行緒可以與呼叫的執行緒不同 `hostCallback` 。</span><span class="sxs-lookup"><span data-stu-id="013ae-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="013ae-134">需求</span><span class="sxs-lookup"><span data-stu-id="013ae-134">Requirements</span></span>  
 <span data-ttu-id="013ae-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="013ae-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="013ae-136">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="013ae-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="013ae-137">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="013ae-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="013ae-138">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="013ae-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013ae-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="013ae-139">See also</span></span>

- [<span data-ttu-id="013ae-140">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="013ae-140">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
