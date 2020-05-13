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
ms.openlocfilehash: 5d7e83c6aa494f2363698d0220bbfe724b54e612
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209431"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="6277a-102">ICorDebugFunction::CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="6277a-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="6277a-103">在此函式的開頭建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="6277a-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6277a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6277a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6277a-105">參數</span><span class="sxs-lookup"><span data-stu-id="6277a-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="6277a-106">脫銷ICorDebugFunctionBreakpoint 物件位址的指標，表示函數的新中斷點。</span><span class="sxs-lookup"><span data-stu-id="6277a-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6277a-107">需求</span><span class="sxs-lookup"><span data-stu-id="6277a-107">Requirements</span></span>  
 <span data-ttu-id="6277a-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6277a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6277a-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6277a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6277a-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6277a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6277a-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6277a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
