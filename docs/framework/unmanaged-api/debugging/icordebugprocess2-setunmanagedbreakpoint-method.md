---
title: ICorDebugProcess2::SetUnmanagedBreakpoint 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b374720bd7bdad48222da006b809702de6462a62
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472781"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="b2441-102">ICorDebugProcess2::SetUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="b2441-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="b2441-103">指定的原生映像的位移設定為未受管理的中斷點。</span><span class="sxs-lookup"><span data-stu-id="b2441-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2441-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2441-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2441-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2441-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="b2441-106">[in]A`CORDB_ADDRESS`物件，指定的原生映像的位移。</span><span class="sxs-lookup"><span data-stu-id="b2441-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="b2441-107">[in]大小，以位元組為單位的`buffer`陣列。</span><span class="sxs-lookup"><span data-stu-id="b2441-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b2441-108">[out]陣列，其中包含會取代中斷點的 opcode。</span><span class="sxs-lookup"><span data-stu-id="b2441-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="b2441-109">[out]中傳回的位元組數目的指標`buffer`陣列。</span><span class="sxs-lookup"><span data-stu-id="b2441-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2441-110">備註</span><span class="sxs-lookup"><span data-stu-id="b2441-110">Remarks</span></span>  
 <span data-ttu-id="b2441-111">如果原生映像位移為 common language runtime (CLR) 中，將會忽略中斷點。</span><span class="sxs-lookup"><span data-stu-id="b2441-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="b2441-112">這可讓 CLR 避免分派-頻中斷點，當偵錯工具設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="b2441-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2441-113">需求</span><span class="sxs-lookup"><span data-stu-id="b2441-113">Requirements</span></span>  
 <span data-ttu-id="b2441-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2441-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2441-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2441-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2441-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2441-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2441-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2441-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
