---
title: ICorRuntimeHost::Stop 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
ms.openlocfilehash: 4117c1297f02032fda80520a7709833217ec94b1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762691"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="f494e-102">ICorRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="f494e-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="f494e-103">在執行時間中停止執行目前進程的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f494e-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f494e-104">語法</span><span class="sxs-lookup"><span data-stu-id="f494e-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f494e-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="f494e-105">Return Value</span></span>  
  
|<span data-ttu-id="f494e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f494e-106">HRESULT</span></span>|<span data-ttu-id="f494e-107">Description</span><span class="sxs-lookup"><span data-stu-id="f494e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f494e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f494e-108">S_OK</span></span>|<span data-ttu-id="f494e-109">作業成功。</span><span class="sxs-lookup"><span data-stu-id="f494e-109">The operation was successful.</span></span>|  
|<span data-ttu-id="f494e-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f494e-110">S_FALSE</span></span>|<span data-ttu-id="f494e-111">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="f494e-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="f494e-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f494e-112">E_FAIL</span></span>|<span data-ttu-id="f494e-113">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f494e-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="f494e-114">如果方法傳回 E_FAIL，則 common language runtime （CLR）就無法在進程中使用。</span><span class="sxs-lookup"><span data-stu-id="f494e-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="f494e-115">後續對任何裝載 Api 的呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f494e-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f494e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f494e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f494e-117">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f494e-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f494e-118">備註</span><span class="sxs-lookup"><span data-stu-id="f494e-118">Remarks</span></span>  
 <span data-ttu-id="f494e-119">通常不需要呼叫 `Stop` 方法，因為程式碼會在進程結束時停止執行。</span><span class="sxs-lookup"><span data-stu-id="f494e-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f494e-120">呼叫之後 `Stop` ，無法將 CLR 重新初始化為相同的進程。</span><span class="sxs-lookup"><span data-stu-id="f494e-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f494e-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="f494e-121">Requirements</span></span>  
 <span data-ttu-id="f494e-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f494e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f494e-123">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="f494e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f494e-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f494e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f494e-125">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="f494e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f494e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f494e-126">See also</span></span>

- [<span data-ttu-id="f494e-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="f494e-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
