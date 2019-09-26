---
title: CLR_DEBUGGING_PROCESS_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 292f6953fad0d65b368642543af107c73ec42ab5
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274105"
---
# <a name="clr_debugging_process_flags-enumeration"></a><span data-ttu-id="2afe1-102">CLR_DEBUGGING_PROCESS_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="2afe1-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="2afe1-103">提供[ICLRDebugging：： OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md)方法所使用的值。</span><span class="sxs-lookup"><span data-stu-id="2afe1-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2afe1-104">語法</span><span class="sxs-lookup"><span data-stu-id="2afe1-104">Syntax</span></span>  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="2afe1-105">成員</span><span class="sxs-lookup"><span data-stu-id="2afe1-105">Members</span></span>  
  
|<span data-ttu-id="2afe1-106">成員</span><span class="sxs-lookup"><span data-stu-id="2afe1-106">Member</span></span>|<span data-ttu-id="2afe1-107">描述</span><span class="sxs-lookup"><span data-stu-id="2afe1-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="2afe1-108">這個執行時間有一個要傳送的非 catch managed 偵錯工具事件。</span><span class="sxs-lookup"><span data-stu-id="2afe1-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="2afe1-109">請參閱備註一節，以瞭解追趕和非 catch 事件之間的區別。</span><span class="sxs-lookup"><span data-stu-id="2afe1-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="2afe1-110">暫止的 managed 事件是<xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>要求。</span><span class="sxs-lookup"><span data-stu-id="2afe1-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2afe1-111">備註</span><span class="sxs-lookup"><span data-stu-id="2afe1-111">Remarks</span></span>  
 <span data-ttu-id="2afe1-112">捕捉事件包括進程、應用程式域、元件、模組，以及執行緒建立通知，可讓偵錯工具在附加至進程之後回到目前狀態。</span><span class="sxs-lookup"><span data-stu-id="2afe1-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="2afe1-113">非捕捉事件（由`CLR_DEBUGGING_MANAGED_EVENT_PENDING`旗標指示）包含所有其他偵錯工具事件，例如例外狀況和 managed 偵錯工具（MDA）通知。</span><span class="sxs-lookup"><span data-stu-id="2afe1-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="2afe1-114">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`旗標可讓執行時間區別終止的例外狀況和要求，以附加可取消的 managed 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="2afe1-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2afe1-115">需求</span><span class="sxs-lookup"><span data-stu-id="2afe1-115">Requirements</span></span>  
 <span data-ttu-id="2afe1-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2afe1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2afe1-117">**標頭：** Metahost .idl，Metahost。h</span><span class="sxs-lookup"><span data-stu-id="2afe1-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="2afe1-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2afe1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2afe1-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2afe1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2afe1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2afe1-120">See also</span></span>

- [<span data-ttu-id="2afe1-121">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="2afe1-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="2afe1-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="2afe1-122">Debugging</span></span>](index.md)
