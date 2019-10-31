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
ms.openlocfilehash: ffab2762fd86e95c3272ca456039028e0897bc41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137172"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="8efe7-102">ICorDebugProcess2::SetUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="8efe7-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="8efe7-103">在指定的原生映射位移處設定非受控中斷點。</span><span class="sxs-lookup"><span data-stu-id="8efe7-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8efe7-104">語法</span><span class="sxs-lookup"><span data-stu-id="8efe7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8efe7-105">參數</span><span class="sxs-lookup"><span data-stu-id="8efe7-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="8efe7-106">在指定原生影像位移的 `CORDB_ADDRESS` 物件。</span><span class="sxs-lookup"><span data-stu-id="8efe7-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="8efe7-107">在`buffer` 陣列的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8efe7-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="8efe7-108">脫銷陣列，其中包含由中斷點取代的 opcode。</span><span class="sxs-lookup"><span data-stu-id="8efe7-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="8efe7-109">脫銷`buffer` 陣列中傳回之位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="8efe7-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8efe7-110">備註</span><span class="sxs-lookup"><span data-stu-id="8efe7-110">Remarks</span></span>  
 <span data-ttu-id="8efe7-111">如果原生映射位移是在 common language runtime （CLR）內，則會忽略中斷點。</span><span class="sxs-lookup"><span data-stu-id="8efe7-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="8efe7-112">當偵錯工具設定中斷點時，這可讓 CLR 避免分派頻外中斷點。</span><span class="sxs-lookup"><span data-stu-id="8efe7-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8efe7-113">需求</span><span class="sxs-lookup"><span data-stu-id="8efe7-113">Requirements</span></span>  
 <span data-ttu-id="8efe7-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8efe7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8efe7-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8efe7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8efe7-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8efe7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8efe7-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8efe7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
