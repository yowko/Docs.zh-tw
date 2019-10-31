---
title: ICorDebugManagedCallback::LogSwitch 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: a72eabb1b405c67f5603164e56a589a237603d2f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130686"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="791bb-102">ICorDebugManagedCallback::LogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="791bb-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="791bb-103">通知偵錯工具，common language runtime （CLR） managed 執行緒已在 <xref:System.Diagnostics.Switch> 類別中呼叫方法，以建立、修改或刪除偵錯工具/追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="791bb-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="791bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="791bb-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="791bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="791bb-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="791bb-106">在ICorDebugAppDomain 物件的指標，表示包含建立、修改或刪除偵錯工具/追蹤參數之 managed 執行緒的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="791bb-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="791bb-107">在代表 managed 執行緒之 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="791bb-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="791bb-108">在值，指出寫入事件記錄檔之描述性訊息的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="791bb-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="791bb-109">在[LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)列舉的值，表示在偵錯工具/追蹤參數上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="791bb-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="791bb-110">在調試/追蹤參數名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="791bb-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="791bb-111">在調試層和追蹤參數之父系名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="791bb-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="791bb-112">需求</span><span class="sxs-lookup"><span data-stu-id="791bb-112">Requirements</span></span>  
 <span data-ttu-id="791bb-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="791bb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="791bb-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="791bb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="791bb-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="791bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="791bb-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="791bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="791bb-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="791bb-117">See also</span></span>

- [<span data-ttu-id="791bb-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="791bb-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
