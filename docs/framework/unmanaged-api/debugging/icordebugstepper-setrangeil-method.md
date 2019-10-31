---
title: ICorDebugStepper::SetRangeIL 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: 88270cb73515cc1a671bfb3fb5c479697ad7b359
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137536"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="470bc-102">ICorDebugStepper::SetRangeIL 方法</span><span class="sxs-lookup"><span data-stu-id="470bc-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="470bc-103">設定值，指定是否呼叫[ICorDebugStepper：： StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)傳遞引數值（相對於原生程式碼）或相對於逐步執行之方法的 Microsoft 中繼語言（MSIL）程式碼。</span><span class="sxs-lookup"><span data-stu-id="470bc-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="470bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="470bc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="470bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="470bc-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="470bc-106">在設定為 `true`，指定範圍相對於 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="470bc-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="470bc-107">設定為 [`false`]，指定範圍相對於原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="470bc-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="470bc-108">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="470bc-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="470bc-109">需求</span><span class="sxs-lookup"><span data-stu-id="470bc-109">Requirements</span></span>  
 <span data-ttu-id="470bc-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="470bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="470bc-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="470bc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="470bc-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="470bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="470bc-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="470bc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
