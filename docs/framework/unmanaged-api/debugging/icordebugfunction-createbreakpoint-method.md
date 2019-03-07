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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 695ce7f25813a191c74bec6563fc7f8ae8d1143d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496114"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="4fc9f-102">ICorDebugFunction::CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="4fc9f-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="4fc9f-103">此函式的開頭建立的中斷點。</span><span class="sxs-lookup"><span data-stu-id="4fc9f-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fc9f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fc9f-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fc9f-105">參數</span><span class="sxs-lookup"><span data-stu-id="4fc9f-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="4fc9f-106">[out]ICorDebugFunctionBreakpoint 物件，表示新的中斷點函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="4fc9f-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fc9f-107">需求</span><span class="sxs-lookup"><span data-stu-id="4fc9f-107">Requirements</span></span>  
 <span data-ttu-id="4fc9f-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fc9f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fc9f-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fc9f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fc9f-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fc9f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fc9f-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fc9f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
