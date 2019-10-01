---
title: ICorDebugCode::GetFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 825840536968562a53d9e05b8a4628a1df79407d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700826"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="29309-102">ICorDebugCode::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="29309-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="29309-103">取得與這個 "ICorDebugCode" 相關聯的 "ICorDebugFunction"。</span><span class="sxs-lookup"><span data-stu-id="29309-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29309-104">語法</span><span class="sxs-lookup"><span data-stu-id="29309-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29309-105">參數</span><span class="sxs-lookup"><span data-stu-id="29309-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="29309-106">脫銷函式位址的指標。</span><span class="sxs-lookup"><span data-stu-id="29309-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29309-107">備註</span><span class="sxs-lookup"><span data-stu-id="29309-107">Remarks</span></span>  
 <span data-ttu-id="29309-108">`ICorDebugCode` 和 `ICorDebugFunction` 會維護一對一關聯性。</span><span class="sxs-lookup"><span data-stu-id="29309-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29309-109">需求</span><span class="sxs-lookup"><span data-stu-id="29309-109">Requirements</span></span>  
 <span data-ttu-id="29309-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29309-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29309-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29309-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29309-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29309-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29309-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29309-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
