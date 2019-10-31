---
title: ICorDebugFunction::CreateBreakpoint 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type:
- apiref
ms.openlocfilehash: 64304b671532325bdc2f8841a2702d537d143330
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124044"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="5a883-102">ICorDebugFunction::CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="5a883-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="5a883-103">在此函式的開頭建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="5a883-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a883-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a883-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a883-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a883-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="5a883-106">脫銷ICorDebugFunctionBreakpoint 物件位址的指標，表示函數的新中斷點。</span><span class="sxs-lookup"><span data-stu-id="5a883-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a883-107">需求</span><span class="sxs-lookup"><span data-stu-id="5a883-107">Requirements</span></span>  
 <span data-ttu-id="5a883-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a883-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a883-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a883-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a883-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a883-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a883-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a883-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
