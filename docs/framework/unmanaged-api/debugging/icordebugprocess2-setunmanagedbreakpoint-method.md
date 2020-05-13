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
ms.openlocfilehash: 6b9396d03892f29e3698af90856d0c0023dc628a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213461"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="ca197-102">ICorDebugProcess2::SetUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="ca197-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="ca197-103">在指定的原生映射位移處設定非受控中斷點。</span><span class="sxs-lookup"><span data-stu-id="ca197-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca197-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca197-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca197-105">參數</span><span class="sxs-lookup"><span data-stu-id="ca197-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ca197-106">在`CORDB_ADDRESS`指定原生影像位移的物件。</span><span class="sxs-lookup"><span data-stu-id="ca197-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="ca197-107">在陣列的大小（以位元組為單位） `buffer` 。</span><span class="sxs-lookup"><span data-stu-id="ca197-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="ca197-108">脫銷陣列，其中包含由中斷點取代的 opcode。</span><span class="sxs-lookup"><span data-stu-id="ca197-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="ca197-109">脫銷陣列中傳回之位元組數的指標 `buffer` 。</span><span class="sxs-lookup"><span data-stu-id="ca197-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca197-110">備註</span><span class="sxs-lookup"><span data-stu-id="ca197-110">Remarks</span></span>  
 <span data-ttu-id="ca197-111">如果原生映射位移是在 common language runtime （CLR）內，則會忽略中斷點。</span><span class="sxs-lookup"><span data-stu-id="ca197-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="ca197-112">當偵錯工具設定中斷點時，這可讓 CLR 避免分派頻外中斷點。</span><span class="sxs-lookup"><span data-stu-id="ca197-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca197-113">需求</span><span class="sxs-lookup"><span data-stu-id="ca197-113">Requirements</span></span>  
 <span data-ttu-id="ca197-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca197-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca197-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca197-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca197-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca197-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca197-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca197-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
