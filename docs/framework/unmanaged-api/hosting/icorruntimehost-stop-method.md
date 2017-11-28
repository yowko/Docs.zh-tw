---
title: "ICorRuntimeHost::Stop 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f6bf66065293107efae7f401a584b7342f29125
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="30d6e-102">ICorRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="30d6e-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="30d6e-103">停止執行目前處理序的執行階段中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="30d6e-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30d6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="30d6e-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="30d6e-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="30d6e-105">Return Value</span></span>  
  
|<span data-ttu-id="30d6e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30d6e-106">HRESULT</span></span>|<span data-ttu-id="30d6e-107">描述</span><span class="sxs-lookup"><span data-stu-id="30d6e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30d6e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="30d6e-108">S_OK</span></span>|<span data-ttu-id="30d6e-109">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="30d6e-109">The operation was successful.</span></span>|  
|<span data-ttu-id="30d6e-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="30d6e-110">S_FALSE</span></span>|<span data-ttu-id="30d6e-111">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="30d6e-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="30d6e-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30d6e-112">E_FAIL</span></span>|<span data-ttu-id="30d6e-113">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="30d6e-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="30d6e-114">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="30d6e-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="30d6e-115">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="30d6e-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="30d6e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30d6e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30d6e-117">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="30d6e-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30d6e-118">備註</span><span class="sxs-lookup"><span data-stu-id="30d6e-118">Remarks</span></span>  
 <span data-ttu-id="30d6e-119">通常不需要呼叫`Stop`方法，因為程式碼停止執行處理序結束時。</span><span class="sxs-lookup"><span data-stu-id="30d6e-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30d6e-120">若要在呼叫之後`Stop`，無法重新初始化 CLR 到相同的程序。</span><span class="sxs-lookup"><span data-stu-id="30d6e-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30d6e-121">需求</span><span class="sxs-lookup"><span data-stu-id="30d6e-121">Requirements</span></span>  
 <span data-ttu-id="30d6e-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30d6e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30d6e-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="30d6e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30d6e-124">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="30d6e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30d6e-125">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="30d6e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30d6e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30d6e-126">See Also</span></span>  
 [<span data-ttu-id="30d6e-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="30d6e-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
