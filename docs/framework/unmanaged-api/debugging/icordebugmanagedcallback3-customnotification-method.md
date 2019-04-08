---
title: ICorDebugManagedCallback3::CustomNotification 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b086c27d73324b4d834c9afa9e7aea20bf6d9148
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193573"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="d42cc-102">ICorDebugManagedCallback3::CustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="d42cc-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="d42cc-103">表示已引發自訂的偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="d42cc-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d42cc-104">語法</span><span class="sxs-lookup"><span data-stu-id="d42cc-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d42cc-105">參數</span><span class="sxs-lookup"><span data-stu-id="d42cc-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="d42cc-106">[in]引發通知的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="d42cc-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="d42cc-107">[in]指標，包含引發通知之執行緒的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="d42cc-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d42cc-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d42cc-108">Return Value</span></span>  
 <span data-ttu-id="d42cc-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d42cc-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d42cc-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d42cc-110">HRESULT</span></span>|<span data-ttu-id="d42cc-111">描述</span><span class="sxs-lookup"><span data-stu-id="d42cc-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d42cc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d42cc-112">S_OK</span></span>|<span data-ttu-id="d42cc-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="d42cc-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d42cc-114">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d42cc-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d42cc-115">備註</span><span class="sxs-lookup"><span data-stu-id="d42cc-115">Remarks</span></span>  
 <span data-ttu-id="d42cc-116">後續呼叫[ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)方法會擷取已傳遞給執行緒物件<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="d42cc-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d42cc-117">執行緒物件的型別必須先前已啟用藉由呼叫[ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d42cc-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="d42cc-118">偵錯工具可以讀取的 thread 物件，欄位的類型特有的參數，而且可以將回應儲存到欄位。</span><span class="sxs-lookup"><span data-stu-id="d42cc-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="d42cc-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面會施加任何原則類型的通知或其內容，並通知的語意完全是偵錯工具、 應用程式和.NET Framework 之間的合約。</span><span class="sxs-lookup"><span data-stu-id="d42cc-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d42cc-120">需求</span><span class="sxs-lookup"><span data-stu-id="d42cc-120">Requirements</span></span>  
 <span data-ttu-id="d42cc-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d42cc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d42cc-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d42cc-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d42cc-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d42cc-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d42cc-124">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d42cc-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d42cc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d42cc-125">See also</span></span>

- [<span data-ttu-id="d42cc-126">ICorDebugManagedCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="d42cc-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="d42cc-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d42cc-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d42cc-128">偵錯</span><span class="sxs-lookup"><span data-stu-id="d42cc-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
