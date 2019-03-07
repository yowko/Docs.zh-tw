---
title: ICorDebugBreakpoint::IsActive 方法
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5df5bed730211676acc4770c91cc6551bde0179b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57464720"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="93870-102">ICorDebugBreakpoint::IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="93870-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="93870-103">取得值，指出是否此`ICorDebugBreakpoint`作用中。</span><span class="sxs-lookup"><span data-stu-id="93870-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93870-104">語法</span><span class="sxs-lookup"><span data-stu-id="93870-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93870-105">參數</span><span class="sxs-lookup"><span data-stu-id="93870-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="93870-106">[out]`true`作用中; 否則即為此中斷點是否`false`。</span><span class="sxs-lookup"><span data-stu-id="93870-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93870-107">需求</span><span class="sxs-lookup"><span data-stu-id="93870-107">Requirements</span></span>  
 <span data-ttu-id="93870-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93870-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93870-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93870-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93870-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93870-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93870-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93870-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
