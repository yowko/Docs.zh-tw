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
ms.openlocfilehash: 4306c4ae44b0ae1ade2bf374981492fa1a4df76f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788373"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="8a142-102">ICorDebugManagedCallback::LogMessage 方法</span><span class="sxs-lookup"><span data-stu-id="8a142-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="8a142-103">通知偵錯工具，common language runtime （CLR） managed 執行緒已在 <xref:System.Diagnostics.EventLog> 類別中呼叫方法來記錄事件。</span><span class="sxs-lookup"><span data-stu-id="8a142-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a142-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a142-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a142-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a142-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8a142-106">在ICorDebugAppDomain 物件的指標，表示包含記錄事件之 managed 執行緒的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="8a142-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="8a142-107">在代表 managed 執行緒之 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="8a142-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="8a142-108">在[LoggingLevelEnum](logginglevelenum-enumeration.md)列舉的值，指出寫入事件記錄檔之描述性訊息的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="8a142-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="8a142-109">在追蹤參數名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="8a142-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="8a142-110">在寫入事件記錄檔之訊息的指標。</span><span class="sxs-lookup"><span data-stu-id="8a142-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a142-111">需求</span><span class="sxs-lookup"><span data-stu-id="8a142-111">Requirements</span></span>  
 <span data-ttu-id="8a142-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a142-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a142-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a142-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a142-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a142-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a142-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a142-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a142-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a142-116">See also</span></span>

- [<span data-ttu-id="8a142-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8a142-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
