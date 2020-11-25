---
title: ICLRRuntimeInfo::IsStarted 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
ms.openlocfilehash: 1dfeb6101a6b8e33ab2fe35f318087d7f1834b6a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714883"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="c466d-102">ICLRRuntimeInfo::IsStarted 方法</span><span class="sxs-lookup"><span data-stu-id="c466d-102">ICLRRuntimeInfo::IsStarted Method</span></span>

<span data-ttu-id="c466d-103">指出執行時間是否已啟動 (也就是是否已呼叫 [ICLRRuntimeHost：： Start 方法](iclrruntimehost-start-method.md) 且已成功) 。</span><span class="sxs-lookup"><span data-stu-id="c466d-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c466d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c466d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c466d-105">參數</span><span class="sxs-lookup"><span data-stu-id="c466d-105">Parameters</span></span>  

 `pbStarted`  
 <span data-ttu-id="c466d-106">[out] `true` 如果此執行時間已啟動，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="c466d-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="c466d-107">擴展傳回用來啟動執行時間的旗標。</span><span class="sxs-lookup"><span data-stu-id="c466d-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c466d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c466d-108">Return Value</span></span>  

 <span data-ttu-id="c466d-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c466d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c466d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c466d-110">HRESULT</span></span>|<span data-ttu-id="c466d-111">描述</span><span class="sxs-lookup"><span data-stu-id="c466d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c466d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c466d-112">S_OK</span></span>|<span data-ttu-id="c466d-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="c466d-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="c466d-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c466d-114">E_NOTIMPL</span></span>|<span data-ttu-id="c466d-115">Common language runtime (CLR) 版本早于 .NET Framework 4 中的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="c466d-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c466d-116">備註</span><span class="sxs-lookup"><span data-stu-id="c466d-116">Remarks</span></span>  

 <span data-ttu-id="c466d-117">這個方法不適用於 .NET Framework 4 的 CLR 版本之前的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="c466d-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c466d-118">需求</span><span class="sxs-lookup"><span data-stu-id="c466d-118">Requirements</span></span>  

 <span data-ttu-id="c466d-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c466d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c466d-120">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="c466d-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c466d-121">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c466d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c466d-122">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c466d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c466d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c466d-123">See also</span></span>

- [<span data-ttu-id="c466d-124">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c466d-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c466d-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="c466d-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="c466d-126">裝載</span><span class="sxs-lookup"><span data-stu-id="c466d-126">Hosting</span></span>](index.md)
