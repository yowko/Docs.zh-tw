---
title: ICorDebugValueBreakpoint 介面
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4c291c12de9cb95416e12e1a5fca273c542df36
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966356"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="0ae15-102">ICorDebugValueBreakpoint 介面</span><span class="sxs-lookup"><span data-stu-id="0ae15-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="0ae15-103">擴充 ICorDebugBreakpoint 介面，以提供特定值的存取權。</span><span class="sxs-lookup"><span data-stu-id="0ae15-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ae15-104">方法</span><span class="sxs-lookup"><span data-stu-id="0ae15-104">Methods</span></span>  
  
|<span data-ttu-id="0ae15-105">方法</span><span class="sxs-lookup"><span data-stu-id="0ae15-105">Method</span></span>|<span data-ttu-id="0ae15-106">描述</span><span class="sxs-lookup"><span data-stu-id="0ae15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ae15-107">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="0ae15-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="0ae15-108">ICorDebugValue 物件，表示在其中設定中斷點之物件的值取得的介面指標。</span><span class="sxs-lookup"><span data-stu-id="0ae15-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ae15-109">備註</span><span class="sxs-lookup"><span data-stu-id="0ae15-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ae15-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0ae15-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ae15-111">需求</span><span class="sxs-lookup"><span data-stu-id="0ae15-111">Requirements</span></span>  
 <span data-ttu-id="0ae15-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae15-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ae15-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ae15-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ae15-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ae15-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ae15-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ae15-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae15-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ae15-116">See also</span></span>
- [<span data-ttu-id="0ae15-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0ae15-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
