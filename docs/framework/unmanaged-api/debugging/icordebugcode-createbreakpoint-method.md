---
title: ICorDebugCode::CreateBreakpoint 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: b02fb0a18bfbc2e93ec204706ca1f17dde5d8c8a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125705"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="009e3-102">ICorDebugCode::CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="009e3-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="009e3-103">在此程式碼區段中，于指定的位移處建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="009e3-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="009e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="009e3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="009e3-105">參數</span><span class="sxs-lookup"><span data-stu-id="009e3-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="009e3-106">在要在其上建立中斷點的位移。</span><span class="sxs-lookup"><span data-stu-id="009e3-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="009e3-107">脫銷代表中斷點之 "ICorDebugFunctionBreakpoint" 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="009e3-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="009e3-108">備註</span><span class="sxs-lookup"><span data-stu-id="009e3-108">Remarks</span></span>  
 <span data-ttu-id="009e3-109">在中斷點開始之前，必須先將它新增至處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="009e3-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="009e3-110">如果這段程式碼是 Microsoft 中繼語言（MSIL）程式碼，而且有即時（JIT）編譯的機器碼，則中斷點也會套用在 JIT 編譯的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="009e3-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="009e3-111">（如果稍後再以 JIT 編譯程式碼，也是如此）。</span><span class="sxs-lookup"><span data-stu-id="009e3-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="009e3-112">需求</span><span class="sxs-lookup"><span data-stu-id="009e3-112">Requirements</span></span>  
 <span data-ttu-id="009e3-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="009e3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="009e3-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="009e3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="009e3-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="009e3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="009e3-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="009e3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
