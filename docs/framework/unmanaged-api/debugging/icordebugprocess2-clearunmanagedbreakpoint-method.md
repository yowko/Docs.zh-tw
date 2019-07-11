---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fb566ff2e5e2b0bcb096cead243ed65a904a914
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736984"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="1f26a-102">ICorDebugProcess2::ClearUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="1f26a-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="1f26a-103">移除先前設定中斷點，在指定的位址。</span><span class="sxs-lookup"><span data-stu-id="1f26a-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f26a-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f26a-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f26a-105">參數</span><span class="sxs-lookup"><span data-stu-id="1f26a-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="1f26a-106">[in]A`CORDB_ADDRESS`值，指定已設定中斷點所在的位址。</span><span class="sxs-lookup"><span data-stu-id="1f26a-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f26a-107">備註</span><span class="sxs-lookup"><span data-stu-id="1f26a-107">Remarks</span></span>  
 <span data-ttu-id="1f26a-108">指定的中斷點會之前尚未設定先前呼叫所[ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)。</span><span class="sxs-lookup"><span data-stu-id="1f26a-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="1f26a-109">`ClearUnmanagedBreakpoint`執行處理序偵錯時，就可以呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="1f26a-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="1f26a-110">`ClearUnmanagedBreakpoint`方法會傳回失敗碼，如果偵錯工具是以僅限受控的模式，或如果沒有中斷點已有指定的位址。</span><span class="sxs-lookup"><span data-stu-id="1f26a-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f26a-111">需求</span><span class="sxs-lookup"><span data-stu-id="1f26a-111">Requirements</span></span>  
 <span data-ttu-id="1f26a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f26a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f26a-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f26a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f26a-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f26a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f26a-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f26a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
