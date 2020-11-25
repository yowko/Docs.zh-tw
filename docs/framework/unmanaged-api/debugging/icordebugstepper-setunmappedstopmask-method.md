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
ms.openlocfilehash: 50fad8b38a6b33d0ddbb2f0f20676296c3d66737
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698724"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="98524-102">ICorDebugStepper::SetUnmappedStopMask 方法</span><span class="sxs-lookup"><span data-stu-id="98524-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>

<span data-ttu-id="98524-103">設定值，這個值會指定要在其中停止執行的未對應程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="98524-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98524-104">語法</span><span class="sxs-lookup"><span data-stu-id="98524-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98524-105">參數</span><span class="sxs-lookup"><span data-stu-id="98524-105">Parameters</span></span>  

 `mask`  
 <span data-ttu-id="98524-106">在CorDebugUnmappedStop 列舉的值，這個值會指定偵錯工具將在其中停止執行的未對應程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="98524-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="98524-107">預設值為 STOP_OTHER_UNMAPPED。</span><span class="sxs-lookup"><span data-stu-id="98524-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="98524-108">值 STOP_UNMANAGED 僅適用于 interop 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="98524-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98524-109">備註</span><span class="sxs-lookup"><span data-stu-id="98524-109">Remarks</span></span>  

 <span data-ttu-id="98524-110">當偵錯工具找不到與 Microsoft 中繼語言 (MSIL) 對應的即時 (JIT) 編譯時，如果已設定未對應程式碼類型的旗標，則會中止執行;否則，會以透明的方式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="98524-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="98524-111">如果偵錯工具未使用分檔器來輸入方法，則不一定不會跳過未對應的程式碼。</span><span class="sxs-lookup"><span data-stu-id="98524-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98524-112">需求</span><span class="sxs-lookup"><span data-stu-id="98524-112">Requirements</span></span>  

 <span data-ttu-id="98524-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98524-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98524-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98524-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98524-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98524-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98524-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98524-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
