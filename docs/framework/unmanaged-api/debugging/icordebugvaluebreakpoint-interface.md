---
title: ICorDebugValueBreakpoint Interface
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
ms.openlocfilehash: e1bb5a6fd0550f7c25d46fa31ca11a10cec54986
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791080"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="d0332-102">ICorDebugValueBreakpoint Interface</span><span class="sxs-lookup"><span data-stu-id="d0332-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="d0332-103">擴充 ICorDebugBreakpoint 介面，以提供特定值的存取權。</span><span class="sxs-lookup"><span data-stu-id="d0332-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0332-104">方法</span><span class="sxs-lookup"><span data-stu-id="d0332-104">Methods</span></span>  
  
|<span data-ttu-id="d0332-105">方法</span><span class="sxs-lookup"><span data-stu-id="d0332-105">Method</span></span>|<span data-ttu-id="d0332-106">描述</span><span class="sxs-lookup"><span data-stu-id="d0332-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0332-107">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="d0332-107">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="d0332-108">取得 ICorDebugValue 物件的介面指標，表示設定中斷點所在物件的值。</span><span class="sxs-lookup"><span data-stu-id="d0332-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0332-109">備註</span><span class="sxs-lookup"><span data-stu-id="d0332-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0332-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d0332-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0332-111">需求</span><span class="sxs-lookup"><span data-stu-id="d0332-111">Requirements</span></span>  
 <span data-ttu-id="d0332-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0332-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0332-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0332-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0332-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0332-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0332-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0332-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0332-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="d0332-116">See also</span></span>

- [<span data-ttu-id="d0332-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d0332-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
