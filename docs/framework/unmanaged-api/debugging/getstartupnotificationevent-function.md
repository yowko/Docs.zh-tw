---
title: GetStartupNotificationEvent 函式
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ed1db49be78d7d16648a9ef9735e79ef1b3ab98
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487323"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="bb7dc-102">GetStartupNotificationEvent 函式</span><span class="sxs-lookup"><span data-stu-id="bb7dc-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="bb7dc-103">建立或開啟任何載入指定目標處理序的 Common Language Runtime (CLR) 將對其發出信號的事件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="bb7dc-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb7dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb7dc-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb7dc-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb7dc-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="bb7dc-106">[in] 從其接收 CLR 啟動通知的目標處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="bb7dc-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="bb7dc-107">[out] 由 CLR 在啟動時通知的控制代碼指標。</span><span class="sxs-lookup"><span data-stu-id="bb7dc-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb7dc-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="bb7dc-108">Return Value</span></span>  
 <span data-ttu-id="bb7dc-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb7dc-109">S_OK</span></span>  
 <span data-ttu-id="bb7dc-110">已成功取得啟動通知事件的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="bb7dc-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="bb7dc-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bb7dc-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="bb7dc-112">`phStartupEvent` 為 null 或 `debuggeePID` 未參考目前正在執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="bb7dc-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="bb7dc-113">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="bb7dc-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="bb7dc-114">無法取得啟動通知事件的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="bb7dc-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb7dc-115">備註</span><span class="sxs-lookup"><span data-stu-id="bb7dc-115">Remarks</span></span>  
 <span data-ttu-id="bb7dc-116">在 Windows 作業系統上，`debuggeePID` 對應至 OS 處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="bb7dc-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="bb7dc-117">在對事件發出信號的 CLR 執行任何 Managed 程式碼之前，會對事件發出信號。</span><span class="sxs-lookup"><span data-stu-id="bb7dc-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb7dc-118">需求</span><span class="sxs-lookup"><span data-stu-id="bb7dc-118">Requirements</span></span>  
 <span data-ttu-id="bb7dc-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb7dc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb7dc-120">**標頭：** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="bb7dc-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="bb7dc-121">**程式庫：** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="bb7dc-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="bb7dc-122">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="bb7dc-122">**.NET Framework Versions:** 3.5 SP1</span></span>
