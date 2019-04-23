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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193573"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="54d49-102">ICorDebugManagedCallback3::CustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="54d49-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="54d49-103">表示已引發自訂的偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="54d49-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54d49-104">語法</span><span class="sxs-lookup"><span data-stu-id="54d49-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54d49-105">參數</span><span class="sxs-lookup"><span data-stu-id="54d49-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="54d49-106">[in]引發通知的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="54d49-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="54d49-107">[in]指標，包含引發通知之執行緒的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="54d49-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54d49-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="54d49-108">Return Value</span></span>  
 <span data-ttu-id="54d49-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="54d49-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="54d49-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54d49-110">HRESULT</span></span>|<span data-ttu-id="54d49-111">描述</span><span class="sxs-lookup"><span data-stu-id="54d49-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54d49-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="54d49-112">S_OK</span></span>|<span data-ttu-id="54d49-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="54d49-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="54d49-114">例外狀況</span><span class="sxs-lookup"><span data-stu-id="54d49-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54d49-115">備註</span><span class="sxs-lookup"><span data-stu-id="54d49-115">Remarks</span></span>  
 <span data-ttu-id="54d49-116">後續呼叫[ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)方法會擷取已傳遞給執行緒物件<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="54d49-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="54d49-117">執行緒物件的型別必須先前已啟用藉由呼叫[ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="54d49-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="54d49-118">偵錯工具可以讀取的 thread 物件，欄位的類型特有的參數，而且可以將回應儲存到欄位。</span><span class="sxs-lookup"><span data-stu-id="54d49-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="54d49-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面會施加任何原則類型的通知或其內容，並通知的語意完全是偵錯工具、 應用程式和.NET Framework 之間的合約。</span><span class="sxs-lookup"><span data-stu-id="54d49-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54d49-120">需求</span><span class="sxs-lookup"><span data-stu-id="54d49-120">Requirements</span></span>  
 <span data-ttu-id="54d49-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54d49-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54d49-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54d49-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54d49-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54d49-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54d49-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54d49-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d49-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54d49-125">See also</span></span>

- [<span data-ttu-id="54d49-126">ICorDebugManagedCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="54d49-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="54d49-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="54d49-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="54d49-128">偵錯</span><span class="sxs-lookup"><span data-stu-id="54d49-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
