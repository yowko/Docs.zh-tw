---
title: "ICorDebugStepper::SetUnmappedStopMask 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fffd523caef6bba1b495f9b8a257f57bd8955af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="4431b-102">ICorDebugStepper::SetUnmappedStopMask 方法</span><span class="sxs-lookup"><span data-stu-id="4431b-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="4431b-103">設定值，指定執行將會暫止的未對應程式碼的類型。</span><span class="sxs-lookup"><span data-stu-id="4431b-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4431b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4431b-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4431b-105">參數</span><span class="sxs-lookup"><span data-stu-id="4431b-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="4431b-106">[in]指定類型的未對應的程式碼中偵錯工具將會暫止執行 CorDebugUnmappedStop 列舉值。</span><span class="sxs-lookup"><span data-stu-id="4431b-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="4431b-107">預設值是 STOP_OTHER_UNMAPPED。</span><span class="sxs-lookup"><span data-stu-id="4431b-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="4431b-108">值 STOP_UNMANAGED 只適用於 interop 偵錯。</span><span class="sxs-lookup"><span data-stu-id="4431b-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4431b-109">備註</span><span class="sxs-lookup"><span data-stu-id="4431b-109">Remarks</span></span>  
 <span data-ttu-id="4431b-110">當偵錯工具找到在 just-in-time (JIT) 編譯成 Microsoft intermediate language (MSIL) 沒有對應的對應時，它會中止執行如果已設定旗標，指定該類型的未對應的程式碼;否則，以透明的方式逐步執行會繼續。</span><span class="sxs-lookup"><span data-stu-id="4431b-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="4431b-111">如果偵錯工具不會使用 stepper 輸入方法，然後它不一定不進入未對應的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4431b-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4431b-112">需求</span><span class="sxs-lookup"><span data-stu-id="4431b-112">Requirements</span></span>  
 <span data-ttu-id="4431b-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4431b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4431b-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4431b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4431b-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4431b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4431b-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4431b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
