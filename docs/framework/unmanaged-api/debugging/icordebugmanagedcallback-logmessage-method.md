---
title: ICorDebugManagedCallback::LogMessage 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14b10b94f66a6b5434befeac1cd9562cb8a0f27f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761565"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="b91b9-102">ICorDebugManagedCallback::LogMessage 方法</span><span class="sxs-lookup"><span data-stu-id="b91b9-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="b91b9-103">通用語言執行平台 (CLR) managed 執行緒已呼叫方法，偵錯工具會告知<xref:System.Diagnostics.EventLog>記錄事件的類別。</span><span class="sxs-lookup"><span data-stu-id="b91b9-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b91b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="b91b9-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b91b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="b91b9-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b91b9-106">[in]表示包含 managed 的執行緒記錄事件的應用程式網域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="b91b9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b91b9-107">[in]ICorDebugThread 物件，表示 managed 的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="b91b9-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="b91b9-108">[in]值為[LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)列舉，指出已寫入事件記錄檔的描述訊息的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="b91b9-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="b91b9-109">[in]追蹤參數的名稱指標。</span><span class="sxs-lookup"><span data-stu-id="b91b9-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="b91b9-110">[in]已寫入事件記錄檔訊息指標。</span><span class="sxs-lookup"><span data-stu-id="b91b9-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b91b9-111">需求</span><span class="sxs-lookup"><span data-stu-id="b91b9-111">Requirements</span></span>  
 <span data-ttu-id="b91b9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b91b9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b91b9-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b91b9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b91b9-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b91b9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b91b9-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b91b9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91b9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b91b9-116">See also</span></span>

- [<span data-ttu-id="b91b9-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b91b9-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
