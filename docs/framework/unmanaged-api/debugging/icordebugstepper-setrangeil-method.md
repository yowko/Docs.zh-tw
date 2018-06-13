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
ms.openlocfilehash: cb3c24b3a96a03359dc6983bcaac4a800613ff5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420527"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="cf64f-102">ICorDebugStepper::SetRangeIL 方法</span><span class="sxs-lookup"><span data-stu-id="cf64f-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="cf64f-103">設定值，指定是否要呼叫[icordebugstepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)傳遞值相對於原生程式碼，或相對於 Microsoft 中繼語言 (MSIL) 程式碼正在逐步執行方法的引數透過。</span><span class="sxs-lookup"><span data-stu-id="cf64f-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf64f-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf64f-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf64f-105">參數</span><span class="sxs-lookup"><span data-stu-id="cf64f-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="cf64f-106">[in]設定為`true`指定的範圍是相對於 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="cf64f-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="cf64f-107">設定為`false`指定的範圍是相對於原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="cf64f-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="cf64f-108">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="cf64f-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf64f-109">需求</span><span class="sxs-lookup"><span data-stu-id="cf64f-109">Requirements</span></span>  
 <span data-ttu-id="cf64f-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf64f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf64f-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf64f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf64f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf64f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf64f-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf64f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
