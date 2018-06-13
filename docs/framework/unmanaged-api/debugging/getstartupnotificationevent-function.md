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
ms.openlocfilehash: 3692471e0652a1a812b1d0cbed9e38cc32112ef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404306"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="a3c72-102">GetStartupNotificationEvent 函式</span><span class="sxs-lookup"><span data-stu-id="a3c72-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="a3c72-103">建立或開啟任何載入指定目標處理序的 Common Language Runtime (CLR) 將對其發出信號的事件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a3c72-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3c72-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3c72-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3c72-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3c72-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="a3c72-106">[in] 從其接收 CLR 啟動通知的目標處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="a3c72-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="a3c72-107">[out] 由 CLR 在啟動時通知的控制代碼指標。</span><span class="sxs-lookup"><span data-stu-id="a3c72-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3c72-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a3c72-108">Return Value</span></span>  
 <span data-ttu-id="a3c72-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3c72-109">S_OK</span></span>  
 <span data-ttu-id="a3c72-110">已成功取得啟動通知事件的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a3c72-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="a3c72-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a3c72-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="a3c72-112">`phStartupEvent` 為 null 或 `debuggeePID` 未參考目前正在執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="a3c72-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="a3c72-113">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="a3c72-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a3c72-114">無法取得啟動通知事件的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a3c72-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3c72-115">備註</span><span class="sxs-lookup"><span data-stu-id="a3c72-115">Remarks</span></span>  
 <span data-ttu-id="a3c72-116">在 Windows 作業系統上，`debuggeePID` 對應至 OS 處理識別碼。</span><span class="sxs-lookup"><span data-stu-id="a3c72-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="a3c72-117">在對事件發出信號的 CLR 執行任何 Managed 程式碼之前，會對事件發出信號。</span><span class="sxs-lookup"><span data-stu-id="a3c72-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3c72-118">需求</span><span class="sxs-lookup"><span data-stu-id="a3c72-118">Requirements</span></span>  
 <span data-ttu-id="a3c72-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3c72-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3c72-120">**標頭：** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="a3c72-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="a3c72-121">**程式庫：** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="a3c72-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="a3c72-122">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a3c72-122">**.NET Framework Versions:** 3.5 SP1</span></span>
