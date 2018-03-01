---
title: "ICorDebugManagedCallback::LogSwitch 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: beb4dc25d634f64d8740005abf83e51ec1e3e731
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="f3e78-102">ICorDebugManagedCallback::LogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="f3e78-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="f3e78-103">告知偵錯工具中的通用語言執行平台 (CLR) managed 執行緒已呼叫方法<xref:System.Diagnostics.Switch>類別來建立、 修改或刪除偵錯/追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="f3e78-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e78-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3e78-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3e78-105">參數</span><span class="sxs-lookup"><span data-stu-id="f3e78-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="f3e78-106">[in]表示包含建立、 修改或刪除偵錯/追蹤切換的 managed 的執行緒的應用程式網域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="f3e78-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f3e78-107">[in]表示 managed 的執行緒的 ICorDebugThread 物件指標。</span><span class="sxs-lookup"><span data-stu-id="f3e78-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="f3e78-108">[in]值，指出已寫入事件記錄檔的描述訊息的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="f3e78-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="f3e78-109">[in]值為[LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)切換偵錯/追蹤列舉，指出作業執行。</span><span class="sxs-lookup"><span data-stu-id="f3e78-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="f3e78-110">[in]偵錯/追蹤參數的名稱指標。</span><span class="sxs-lookup"><span data-stu-id="f3e78-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="f3e78-111">[in]偵錯/追蹤參數，因為父系的名稱指標。</span><span class="sxs-lookup"><span data-stu-id="f3e78-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3e78-112">需求</span><span class="sxs-lookup"><span data-stu-id="f3e78-112">Requirements</span></span>  
 <span data-ttu-id="f3e78-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e78-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3e78-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3e78-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3e78-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3e78-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3e78-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3e78-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e78-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3e78-117">See Also</span></span>  
 [<span data-ttu-id="f3e78-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f3e78-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
