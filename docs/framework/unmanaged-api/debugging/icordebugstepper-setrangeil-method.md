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
ms.openlocfilehash: 5a27f155021661022b27022bbb252e00dfa67255
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698776"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="c87ea-102">ICorDebugStepper::SetRangeIL 方法</span><span class="sxs-lookup"><span data-stu-id="c87ea-102">ICorDebugStepper::SetRangeIL Method</span></span>

<span data-ttu-id="c87ea-103">設定值，這個值會指定對 [ICorDebugStepper：： StepRange](icordebugstepper-steprange-method.md) 的呼叫是否會傳遞與機器碼相關的引數值，或相對於 Microsoft 中繼語言的引數值， (MSIL) 正在逐步執行之方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c87ea-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c87ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="c87ea-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c87ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="c87ea-105">Parameters</span></span>  

 `bIL`  
 <span data-ttu-id="c87ea-106">在設定為， `true` 以指定範圍相對於 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c87ea-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="c87ea-107">設定為， `false` 以指定範圍相對於原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="c87ea-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="c87ea-108">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="c87ea-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c87ea-109">需求</span><span class="sxs-lookup"><span data-stu-id="c87ea-109">Requirements</span></span>  

 <span data-ttu-id="c87ea-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c87ea-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c87ea-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c87ea-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c87ea-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c87ea-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c87ea-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c87ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
