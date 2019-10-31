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
ms.openlocfilehash: 8377ead42c752d8ebe9813d9e00662b94339f8a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137249"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="fa477-102">ICorDebugProcess2::ClearUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="fa477-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="fa477-103">移除先前在指定位址上設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="fa477-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa477-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa477-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa477-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa477-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="fa477-106">在`CORDB_ADDRESS` 值，指定設定中斷點所在的位址。</span><span class="sxs-lookup"><span data-stu-id="fa477-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa477-107">備註</span><span class="sxs-lookup"><span data-stu-id="fa477-107">Remarks</span></span>  
 <span data-ttu-id="fa477-108">先前呼叫[ICorDebugProcess2：： SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)之前已設定指定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="fa477-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="fa477-109">當正在進行調試的進程正在執行時，可以呼叫 `ClearUnmanagedBreakpoint` 方法。</span><span class="sxs-lookup"><span data-stu-id="fa477-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="fa477-110">如果偵錯工具是以僅限 managed 模式連接，或如果指定的位址沒有中斷點存在，則 `ClearUnmanagedBreakpoint` 方法會傳回失敗碼。</span><span class="sxs-lookup"><span data-stu-id="fa477-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa477-111">需求</span><span class="sxs-lookup"><span data-stu-id="fa477-111">Requirements</span></span>  
 <span data-ttu-id="fa477-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa477-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa477-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa477-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa477-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa477-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa477-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa477-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
