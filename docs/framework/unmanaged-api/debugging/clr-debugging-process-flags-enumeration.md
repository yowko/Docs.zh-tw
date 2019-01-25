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
ms.openlocfilehash: 609bb050bb9c5addb5250f65a059a70d3ce32428
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662240"
---
# <a name="clrdebuggingprocessflags-enumeration"></a><span data-ttu-id="b9c34-102">CLR_DEBUGGING_PROCESS_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="b9c34-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="b9c34-103">提供值，可供[iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b9c34-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c34-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9c34-104">Syntax</span></span>  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="b9c34-105">成員</span><span class="sxs-lookup"><span data-stu-id="b9c34-105">Members</span></span>  
  
|<span data-ttu-id="b9c34-106">成員</span><span class="sxs-lookup"><span data-stu-id="b9c34-106">Member</span></span>|<span data-ttu-id="b9c34-107">描述</span><span class="sxs-lookup"><span data-stu-id="b9c34-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="b9c34-108">此執行階段發生的非 catch up managed 偵錯工具事件時傳送。</span><span class="sxs-lookup"><span data-stu-id="b9c34-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="b9c34-109">請參閱 < 備註 > 一節追補和非 catch 向上事件之間的差異。</span><span class="sxs-lookup"><span data-stu-id="b9c34-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="b9c34-110">管理已暫止的事件是<xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>要求。</span><span class="sxs-lookup"><span data-stu-id="b9c34-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9c34-111">備註</span><span class="sxs-lookup"><span data-stu-id="b9c34-111">Remarks</span></span>  
 <span data-ttu-id="b9c34-112">更新事件包含程序、 應用程式定義域、 組件、 模組和偵錯工具帶到目前的狀態之後它已附加至處理序, 的執行緒建立通知。</span><span class="sxs-lookup"><span data-stu-id="b9c34-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="b9c34-113">非 catch 總事件，由`CLR_DEBUGGING_MANAGED_EVENT_PENDING`旗標，包括所有其他偵錯工具事件，例如例外狀況和 managed 偵錯助理 (MDA) 通知。</span><span class="sxs-lookup"><span data-stu-id="b9c34-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="b9c34-114">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`旗標可讓執行階段終止的例外狀況和附加 managed 偵錯工具，可取消的要求之間不同。</span><span class="sxs-lookup"><span data-stu-id="b9c34-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9c34-115">需求</span><span class="sxs-lookup"><span data-stu-id="b9c34-115">Requirements</span></span>  
 <span data-ttu-id="b9c34-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9c34-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9c34-117">**標頭：** Metahost.idl Metahost.h</span><span class="sxs-lookup"><span data-stu-id="b9c34-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="b9c34-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9c34-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9c34-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9c34-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c34-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9c34-120">See also</span></span>
- [<span data-ttu-id="b9c34-121">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="b9c34-121">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="b9c34-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="b9c34-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
