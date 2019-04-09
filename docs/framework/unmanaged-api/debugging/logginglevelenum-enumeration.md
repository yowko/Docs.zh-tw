---
title: LoggingLevelEnum 列舉
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe8e1355382273a681e927897f4a8ff5814b8de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086503"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="2a1f4-102">LoggingLevelEnum 列舉</span><span class="sxs-lookup"><span data-stu-id="2a1f4-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="2a1f4-103">指出當 Managed 執行緒記錄事件時，寫入至事件記錄檔之描述性訊息的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a1f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a1f4-104">Syntax</span></span>  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a><span data-ttu-id="2a1f4-105">成員</span><span class="sxs-lookup"><span data-stu-id="2a1f4-105">Members</span></span>  
  
|<span data-ttu-id="2a1f4-106">成員</span><span class="sxs-lookup"><span data-stu-id="2a1f4-106">Member</span></span>|<span data-ttu-id="2a1f4-107">描述</span><span class="sxs-lookup"><span data-stu-id="2a1f4-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="2a1f4-108">此訊息為 「 追蹤層級 0。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="2a1f4-109">此訊息為 「 追蹤層級 1。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="2a1f4-110">此訊息為 「 追蹤層級 2。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="2a1f4-111">此訊息為 「 追蹤層級 3。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="2a1f4-112">此訊息為 「 追蹤層級 4。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="2a1f4-113">為狀態層級 0 的訊息。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="2a1f4-114">為狀態層級 1 的訊息。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="2a1f4-115">此訊息為狀態層級 2。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="2a1f4-116">為狀態層級 3 的訊息。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="2a1f4-117">此訊息為狀態層級 4。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="2a1f4-118">訊息是警告層級。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="2a1f4-119">訊息是錯誤層級。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="2a1f4-120">此訊息為異常的層級。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a1f4-121">備註</span><span class="sxs-lookup"><span data-stu-id="2a1f4-121">Remarks</span></span>  
 <span data-ttu-id="2a1f4-122">Common language runtime (CLR) 呼叫[icordebugmanagedcallback:: Logmessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)方法來通知偵錯工具 managed 的執行緒已記錄事件。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="2a1f4-123">CLR 值傳遞給`LoggingLevelEnum`表示 managed 的執行緒寫入事件記錄檔訊息的嚴重性層級的列舉。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a1f4-124">需求</span><span class="sxs-lookup"><span data-stu-id="2a1f4-124">Requirements</span></span>  
 <span data-ttu-id="2a1f4-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a1f4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a1f4-126">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a1f4-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a1f4-127">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a1f4-127">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2a1f4-128">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="2a1f4-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2a1f4-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a1f4-129">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="2a1f4-130">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="2a1f4-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
