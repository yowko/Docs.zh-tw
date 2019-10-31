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
ms.openlocfilehash: 3611684a17d51fc4fdba31dd4049540039b43e8b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110512"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="a092e-102">ICorDebugAppDomain::EnumerateBreakpoints 方法</span><span class="sxs-lookup"><span data-stu-id="a092e-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="a092e-103">取得應用程式域中所有使用中中斷點的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a092e-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a092e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a092e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a092e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a092e-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="a092e-106">脫銷ICorDebugBreakpointEnum 物件位址的指標，這是應用程式域中所有作用中中斷點的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a092e-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a092e-107">備註</span><span class="sxs-lookup"><span data-stu-id="a092e-107">Remarks</span></span>  
 <span data-ttu-id="a092e-108">列舉值包含所有類型的中斷點，包括函式中斷點和資料中斷點。</span><span class="sxs-lookup"><span data-stu-id="a092e-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a092e-109">需求</span><span class="sxs-lookup"><span data-stu-id="a092e-109">Requirements</span></span>  
 <span data-ttu-id="a092e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a092e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a092e-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a092e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a092e-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a092e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a092e-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a092e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
