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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9b4ee64022374cb4e1950acceb3f32925b736bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994280"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="43326-102">ICorDebugStepper::SetRangeIL 方法</span><span class="sxs-lookup"><span data-stu-id="43326-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="43326-103">設定值，這個值，指定是否呼叫[icordebugstepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)值相對於原生程式碼，或相對於 Microsoft intermediate language (MSIL) 程式碼正在逐步執行方法的引數傳遞透過。</span><span class="sxs-lookup"><span data-stu-id="43326-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43326-104">語法</span><span class="sxs-lookup"><span data-stu-id="43326-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43326-105">參數</span><span class="sxs-lookup"><span data-stu-id="43326-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="43326-106">[in]若要設定`true`以指定的範圍相對於 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="43326-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="43326-107">若要設定`false`以指定的範圍相對於原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="43326-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="43326-108">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="43326-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43326-109">需求</span><span class="sxs-lookup"><span data-stu-id="43326-109">Requirements</span></span>  
 <span data-ttu-id="43326-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43326-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43326-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43326-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43326-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43326-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43326-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43326-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
