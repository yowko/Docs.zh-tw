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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aea8cb4c180477fdd763a8af2f251db2d37d066
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436633"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="aa51c-102">ICorRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="aa51c-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="aa51c-103">停止執行目前處理序的執行階段中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="aa51c-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa51c-104">語法</span><span class="sxs-lookup"><span data-stu-id="aa51c-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="aa51c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="aa51c-105">Return Value</span></span>  
  
|<span data-ttu-id="aa51c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa51c-106">HRESULT</span></span>|<span data-ttu-id="aa51c-107">描述</span><span class="sxs-lookup"><span data-stu-id="aa51c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa51c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa51c-108">S_OK</span></span>|<span data-ttu-id="aa51c-109">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="aa51c-109">The operation was successful.</span></span>|  
|<span data-ttu-id="aa51c-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="aa51c-110">S_FALSE</span></span>|<span data-ttu-id="aa51c-111">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="aa51c-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="aa51c-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa51c-112">E_FAIL</span></span>|<span data-ttu-id="aa51c-113">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="aa51c-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="aa51c-114">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="aa51c-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="aa51c-115">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="aa51c-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aa51c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa51c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa51c-117">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="aa51c-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa51c-118">備註</span><span class="sxs-lookup"><span data-stu-id="aa51c-118">Remarks</span></span>  
 <span data-ttu-id="aa51c-119">通常不需要呼叫`Stop`方法，因為程式碼停止執行處理序結束時。</span><span class="sxs-lookup"><span data-stu-id="aa51c-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa51c-120">若要在呼叫之後`Stop`，無法重新初始化 CLR 到相同的程序。</span><span class="sxs-lookup"><span data-stu-id="aa51c-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa51c-121">需求</span><span class="sxs-lookup"><span data-stu-id="aa51c-121">Requirements</span></span>  
 <span data-ttu-id="aa51c-122">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aa51c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa51c-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aa51c-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa51c-124">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="aa51c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa51c-125">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="aa51c-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa51c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa51c-126">See Also</span></span>  
 [<span data-ttu-id="aa51c-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="aa51c-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
