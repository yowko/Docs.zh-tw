---
title: ICorDebugStepper::SetUnmappedStopMask 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: ff393b119c349e34898b781c3185cc82f2dba11f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137557"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="69409-102">ICorDebugStepper::SetUnmappedStopMask 方法</span><span class="sxs-lookup"><span data-stu-id="69409-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="69409-103">設定值，指定執行將暫停的未對應程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="69409-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69409-104">語法</span><span class="sxs-lookup"><span data-stu-id="69409-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69409-105">參數</span><span class="sxs-lookup"><span data-stu-id="69409-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="69409-106">在CorDebugUnmappedStop 列舉的值，指定偵錯工具將在其中停止執行的未對應程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="69409-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="69409-107">預設值為 STOP_OTHER_UNMAPPED。</span><span class="sxs-lookup"><span data-stu-id="69409-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="69409-108">STOP_UNMANAGED 值只適用于 interop 調試。</span><span class="sxs-lookup"><span data-stu-id="69409-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69409-109">備註</span><span class="sxs-lookup"><span data-stu-id="69409-109">Remarks</span></span>  
 <span data-ttu-id="69409-110">當偵錯工具發現沒有對應到 Microsoft 中繼語言（MSIL）的即時（JIT）編譯時，如果指定該類型之未對應程式碼的旗標已設定，就會停止執行。否則，逐步執行會以透明方式繼續進行。</span><span class="sxs-lookup"><span data-stu-id="69409-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="69409-111">如果偵錯工具未使用分檔器來輸入方法，則不一定會跳過未對應的程式碼。</span><span class="sxs-lookup"><span data-stu-id="69409-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69409-112">需求</span><span class="sxs-lookup"><span data-stu-id="69409-112">Requirements</span></span>  
 <span data-ttu-id="69409-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69409-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69409-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69409-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69409-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69409-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69409-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69409-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
