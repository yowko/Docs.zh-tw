---
title: "ICorDebugManagedCallback::LogMessage 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LogMessage
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d62204e8fb2e1fabae4183bbcf7b4d42b832d2b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="42328-102">ICorDebugManagedCallback::LogMessage 方法</span><span class="sxs-lookup"><span data-stu-id="42328-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="42328-103">告知偵錯工具中的通用語言執行平台 (CLR) managed 執行緒已呼叫方法<xref:System.Diagnostics.EventLog>記錄事件的類別。</span><span class="sxs-lookup"><span data-stu-id="42328-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42328-104">語法</span><span class="sxs-lookup"><span data-stu-id="42328-104">Syntax</span></span>  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42328-105">參數</span><span class="sxs-lookup"><span data-stu-id="42328-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="42328-106">[in]表示包含 managed 的執行緒記錄事件的應用程式網域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="42328-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="42328-107">[in]表示 managed 的執行緒的 ICorDebugThread 物件指標。</span><span class="sxs-lookup"><span data-stu-id="42328-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="42328-108">[in]值為[LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)列舉，指出已寫入事件記錄檔的描述訊息的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="42328-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="42328-109">[in]追蹤參數的名稱指標。</span><span class="sxs-lookup"><span data-stu-id="42328-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="42328-110">[in]指標，寫入事件記錄檔訊息。</span><span class="sxs-lookup"><span data-stu-id="42328-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42328-111">需求</span><span class="sxs-lookup"><span data-stu-id="42328-111">Requirements</span></span>  
 <span data-ttu-id="42328-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42328-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42328-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42328-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42328-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42328-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42328-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42328-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42328-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="42328-116">See Also</span></span>  
 [<span data-ttu-id="42328-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="42328-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
