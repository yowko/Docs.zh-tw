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
ms.openlocfilehash: 85a7adddf395e07297c8fb6ceab4aa81e0aaf012
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762197"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="4af70-102">ICLRRuntimeInfo::IsStarted 方法</span><span class="sxs-lookup"><span data-stu-id="4af70-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="4af70-103">指出執行時間是否已啟動（也就是是否已呼叫[ICLRRuntimeHost：： Start 方法](iclrruntimehost-start-method.md)且已成功）。</span><span class="sxs-lookup"><span data-stu-id="4af70-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af70-104">語法</span><span class="sxs-lookup"><span data-stu-id="4af70-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4af70-105">參數</span><span class="sxs-lookup"><span data-stu-id="4af70-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="4af70-106">[out] `true`如果此執行時間已啟動，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="4af70-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="4af70-107">脫銷傳回用來啟動執行時間的旗標。</span><span class="sxs-lookup"><span data-stu-id="4af70-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4af70-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="4af70-108">Return Value</span></span>  
 <span data-ttu-id="4af70-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="4af70-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4af70-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4af70-110">HRESULT</span></span>|<span data-ttu-id="4af70-111">Description</span><span class="sxs-lookup"><span data-stu-id="4af70-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4af70-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4af70-112">S_OK</span></span>|<span data-ttu-id="4af70-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="4af70-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="4af70-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4af70-114">E_NOTIMPL</span></span>|<span data-ttu-id="4af70-115">Common language runtime （CLR）版本早于 .NET Framework 4 中的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="4af70-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4af70-116">備註</span><span class="sxs-lookup"><span data-stu-id="4af70-116">Remarks</span></span>  
 <span data-ttu-id="4af70-117">這個方法無法與 .NET Framework 4 中 CLR 版本之前的 CLR 版本搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4af70-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4af70-118">規格需求</span><span class="sxs-lookup"><span data-stu-id="4af70-118">Requirements</span></span>  
 <span data-ttu-id="4af70-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4af70-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4af70-120">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="4af70-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4af70-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4af70-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4af70-122">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4af70-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af70-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4af70-123">See also</span></span>

- [<span data-ttu-id="4af70-124">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4af70-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="4af70-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4af70-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="4af70-126">裝載</span><span class="sxs-lookup"><span data-stu-id="4af70-126">Hosting</span></span>](index.md)
