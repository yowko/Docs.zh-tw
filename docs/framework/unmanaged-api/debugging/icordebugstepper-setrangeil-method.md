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
ms.openlocfilehash: b3153a88867d249aad8365bb774348fb8c9d57d5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791757"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="ed08c-102">ICorDebugStepper::SetRangeIL 方法</span><span class="sxs-lookup"><span data-stu-id="ed08c-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="ed08c-103">設定值，指定是否呼叫[ICorDebugStepper：： StepRange](icordebugstepper-steprange-method.md)傳遞引數值（相對於原生程式碼）或相對於逐步執行之方法的 Microsoft 中繼語言（MSIL）程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed08c-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed08c-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed08c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed08c-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed08c-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="ed08c-106">在設定為 `true`，指定範圍相對於 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed08c-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="ed08c-107">設定為 [`false`]，指定範圍相對於原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed08c-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="ed08c-108">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="ed08c-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed08c-109">需求</span><span class="sxs-lookup"><span data-stu-id="ed08c-109">Requirements</span></span>  
 <span data-ttu-id="ed08c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed08c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed08c-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed08c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed08c-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed08c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed08c-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed08c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
