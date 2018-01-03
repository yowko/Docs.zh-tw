---
title: "ICorDebugFunction::CreateBreakpoint 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.CreateBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0565f7ad5e57ad63607b1a28e3ecb26965afd974
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="57ffb-102">ICorDebugFunction::CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="57ffb-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="57ffb-103">此函式的開頭建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="57ffb-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ffb-104">語法</span><span class="sxs-lookup"><span data-stu-id="57ffb-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57ffb-105">參數</span><span class="sxs-lookup"><span data-stu-id="57ffb-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="57ffb-106">[out]ICorDebugFunctionBreakpoint 物件，表示新的中斷點函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="57ffb-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57ffb-107">需求</span><span class="sxs-lookup"><span data-stu-id="57ffb-107">Requirements</span></span>  
 <span data-ttu-id="57ffb-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57ffb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57ffb-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57ffb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57ffb-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57ffb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57ffb-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57ffb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
