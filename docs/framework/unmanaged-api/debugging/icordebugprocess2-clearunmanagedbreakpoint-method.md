---
title: "ICorDebugProcess2::ClearUnmanagedBreakpoint 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ca1514eaa916f5e607e49b5a5713763f855d937
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="51b8f-102">ICorDebugProcess2::ClearUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="51b8f-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="51b8f-103">移除先前設定在指定的位址中斷點。</span><span class="sxs-lookup"><span data-stu-id="51b8f-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b8f-104">語法</span><span class="sxs-lookup"><span data-stu-id="51b8f-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51b8f-105">參數</span><span class="sxs-lookup"><span data-stu-id="51b8f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="51b8f-106">[in]A`CORDB_ADDRESS`值，指定 中斷點設定的位址。</span><span class="sxs-lookup"><span data-stu-id="51b8f-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51b8f-107">備註</span><span class="sxs-lookup"><span data-stu-id="51b8f-107">Remarks</span></span>  
 <span data-ttu-id="51b8f-108">指定的中斷點會先前已設定的之前呼叫[icordebugprocess2:: Setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)。</span><span class="sxs-lookup"><span data-stu-id="51b8f-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="51b8f-109">`ClearUnmanagedBreakpoint`正在偵錯處理序正在執行時，就可以呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="51b8f-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="51b8f-110">`ClearUnmanagedBreakpoint`如果偵錯工具是以僅限 managed 的模式，或如果沒有中斷點存在於指定的位址，方法會傳回失敗碼。</span><span class="sxs-lookup"><span data-stu-id="51b8f-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51b8f-111">需求</span><span class="sxs-lookup"><span data-stu-id="51b8f-111">Requirements</span></span>  
 <span data-ttu-id="51b8f-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51b8f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b8f-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51b8f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51b8f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51b8f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51b8f-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51b8f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
