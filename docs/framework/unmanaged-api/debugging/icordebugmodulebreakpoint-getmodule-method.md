---
title: ICorDebugModuleBreakpoint::GetModule 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type:
- apiref
ms.openlocfilehash: b6363ef901d5297862ca46e685bb783aaaeb4123
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709604"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="b6925-102">ICorDebugModuleBreakpoint::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="b6925-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>

<span data-ttu-id="b6925-103">取得 "ICorDebugModule" 的介面指標，該指標會參考設定此中斷點的模組。</span><span class="sxs-lookup"><span data-stu-id="b6925-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6925-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6925-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6925-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6925-105">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="b6925-106">擴展介面位址的指標 `ICorDebugModule` ，該介面參考中斷點設定所在的模組。</span><span class="sxs-lookup"><span data-stu-id="b6925-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6925-107">需求</span><span class="sxs-lookup"><span data-stu-id="b6925-107">Requirements</span></span>  

 <span data-ttu-id="b6925-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6925-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6925-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6925-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6925-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6925-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6925-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6925-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6925-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6925-112">See also</span></span>
