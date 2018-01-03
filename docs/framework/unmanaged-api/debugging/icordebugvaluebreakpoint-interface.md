---
title: ICorDebugValueBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueBreakpoint
helpviewer_keywords: ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92de5aa960c9ded27aef09d2c795437e9c599835
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluebreakpoint-interface1"></a><span data-ttu-id="41e94-102">ICorDebugValueBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="41e94-102">ICorDebugValueBreakpoint Interface1</span></span>
<span data-ttu-id="41e94-103">擴充 ICorDebugBreakpoint 介面，以提供特定值的存取權。</span><span class="sxs-lookup"><span data-stu-id="41e94-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41e94-104">方法</span><span class="sxs-lookup"><span data-stu-id="41e94-104">Methods</span></span>  
  
|<span data-ttu-id="41e94-105">方法</span><span class="sxs-lookup"><span data-stu-id="41e94-105">Method</span></span>|<span data-ttu-id="41e94-106">描述</span><span class="sxs-lookup"><span data-stu-id="41e94-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41e94-107">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="41e94-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="41e94-108">ICorDebugValue 物件，表示設定中斷點之物件的值取得的介面指標。</span><span class="sxs-lookup"><span data-stu-id="41e94-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41e94-109">備註</span><span class="sxs-lookup"><span data-stu-id="41e94-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41e94-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="41e94-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e94-111">需求</span><span class="sxs-lookup"><span data-stu-id="41e94-111">Requirements</span></span>  
 <span data-ttu-id="41e94-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41e94-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e94-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41e94-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41e94-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41e94-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41e94-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41e94-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e94-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="41e94-116">See Also</span></span>  
 [<span data-ttu-id="41e94-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="41e94-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
