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
ms.openlocfilehash: fb8b8f3e29c141e91587a4d0cdc81cdabccdbc9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178640"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="0873e-102">ICorDebugProcess2::SetUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="0873e-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="0873e-103">在指定的本機圖像偏移處設置非託管中斷點。</span><span class="sxs-lookup"><span data-stu-id="0873e-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0873e-104">語法</span><span class="sxs-lookup"><span data-stu-id="0873e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0873e-105">參數</span><span class="sxs-lookup"><span data-stu-id="0873e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="0873e-106">[在]`CORDB_ADDRESS`指定本機圖像偏移的物件。</span><span class="sxs-lookup"><span data-stu-id="0873e-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="0873e-107">[在]`buffer`陣列的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="0873e-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0873e-108">[出]包含由中斷點替換的運算碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="0873e-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="0873e-109">[出]指向陣列中返回的位元組數的`buffer`指標。</span><span class="sxs-lookup"><span data-stu-id="0873e-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0873e-110">備註</span><span class="sxs-lookup"><span data-stu-id="0873e-110">Remarks</span></span>  
 <span data-ttu-id="0873e-111">如果本機圖像偏移在通用語言運行時 （CLR） 內，則中斷點將被忽略。</span><span class="sxs-lookup"><span data-stu-id="0873e-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="0873e-112">這允許 CLR 避免調度帶外中斷點，當中斷點由調試器設置時。</span><span class="sxs-lookup"><span data-stu-id="0873e-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0873e-113">需求</span><span class="sxs-lookup"><span data-stu-id="0873e-113">Requirements</span></span>  
 <span data-ttu-id="0873e-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0873e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0873e-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0873e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0873e-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0873e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0873e-117">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0873e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
