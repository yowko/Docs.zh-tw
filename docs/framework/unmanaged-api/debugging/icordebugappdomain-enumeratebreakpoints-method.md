---
title: ICorDebugAppDomain::EnumerateBreakpoints 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a683f1531ed28fbd8ef085414bb7cb365762ffde
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738049"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="87a40-102">ICorDebugAppDomain::EnumerateBreakpoints 方法</span><span class="sxs-lookup"><span data-stu-id="87a40-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="87a40-103">取得應用程式定義域中所有使用中的中斷點列舉值。</span><span class="sxs-lookup"><span data-stu-id="87a40-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87a40-104">語法</span><span class="sxs-lookup"><span data-stu-id="87a40-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87a40-105">參數</span><span class="sxs-lookup"><span data-stu-id="87a40-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="87a40-106">[out]ICorDebugBreakpointEnum 物件，應用程式定義域中的所有作用中的中斷點的列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="87a40-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87a40-107">備註</span><span class="sxs-lookup"><span data-stu-id="87a40-107">Remarks</span></span>  
 <span data-ttu-id="87a40-108">列舉值會包含所有類型的中斷點，包括函式中斷點和資料中斷點。</span><span class="sxs-lookup"><span data-stu-id="87a40-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87a40-109">需求</span><span class="sxs-lookup"><span data-stu-id="87a40-109">Requirements</span></span>  
 <span data-ttu-id="87a40-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87a40-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87a40-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87a40-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87a40-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87a40-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87a40-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87a40-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
