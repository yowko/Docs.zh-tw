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
ms.openlocfilehash: 61aece9dd506d6e4af8718e45cc772d120a7d579
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401657"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="db752-102">ICorDebugBreakpoint::IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="db752-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="db752-103">取得值，指出是否此`ICorDebugBreakpoint`為作用中。</span><span class="sxs-lookup"><span data-stu-id="db752-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db752-104">語法</span><span class="sxs-lookup"><span data-stu-id="db752-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db752-105">參數</span><span class="sxs-lookup"><span data-stu-id="db752-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="db752-106">[out]`true`此中斷點為作用中; 否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="db752-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db752-107">需求</span><span class="sxs-lookup"><span data-stu-id="db752-107">Requirements</span></span>  
 <span data-ttu-id="db752-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db752-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db752-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db752-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db752-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db752-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db752-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db752-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
