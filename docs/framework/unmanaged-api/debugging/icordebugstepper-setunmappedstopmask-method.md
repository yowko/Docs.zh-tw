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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da799b0d4f4e5e4b281445baa35d95f992ba0b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987450"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="c3abf-102">ICorDebugStepper::SetUnmappedStopMask 方法</span><span class="sxs-lookup"><span data-stu-id="c3abf-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="c3abf-103">設定值，這個值會指定未對應的程式碼執行將會暫止的類型。</span><span class="sxs-lookup"><span data-stu-id="c3abf-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3abf-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3abf-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3abf-105">參數</span><span class="sxs-lookup"><span data-stu-id="c3abf-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="c3abf-106">[in]CorDebugUnmappedStop 列舉，指定未對應的程式碼中偵錯工具將會暫止執行的類型值。</span><span class="sxs-lookup"><span data-stu-id="c3abf-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="c3abf-107">預設值是 STOP_OTHER_UNMAPPED。</span><span class="sxs-lookup"><span data-stu-id="c3abf-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="c3abf-108">值 STOP_UNMANAGED 只適用於 interop 偵錯。</span><span class="sxs-lookup"><span data-stu-id="c3abf-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3abf-109">備註</span><span class="sxs-lookup"><span data-stu-id="c3abf-109">Remarks</span></span>  
 <span data-ttu-id="c3abf-110">如果您已設定旗標，指定該類型的未對應的程式碼; 時偵錯工具會尋找在 just-in-time (JIT) 編譯成 Microsoft intermediate language (MSIL) 沒有對應的對應，請它先終止執行否則，繼續逐步執行以透明的方式。</span><span class="sxs-lookup"><span data-stu-id="c3abf-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="c3abf-111">如果偵錯工具不使用步進輸入方法，則它不一定不進入未對應的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c3abf-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3abf-112">需求</span><span class="sxs-lookup"><span data-stu-id="c3abf-112">Requirements</span></span>  
 <span data-ttu-id="c3abf-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3abf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3abf-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3abf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3abf-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3abf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3abf-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3abf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
