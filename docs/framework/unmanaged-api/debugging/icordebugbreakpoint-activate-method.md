---
title: ICorDebugBreakpoint::Activate 方法
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ac37df58762dac4e3a6161361cafd8ea87e2657
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491356"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="a3afd-102">ICorDebugBreakpoint::Activate 方法</span><span class="sxs-lookup"><span data-stu-id="a3afd-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="a3afd-103">設定作用中的狀態，這個`ICorDebugBreakpoint`。</span><span class="sxs-lookup"><span data-stu-id="a3afd-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3afd-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3afd-104">Syntax</span></span>  
  
```  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3afd-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3afd-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="a3afd-106">[in]將此值設定為`true`來指定狀態為作用中; 否則，請將此值設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="a3afd-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3afd-107">需求</span><span class="sxs-lookup"><span data-stu-id="a3afd-107">Requirements</span></span>  
 <span data-ttu-id="a3afd-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3afd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3afd-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3afd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3afd-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3afd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3afd-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3afd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
