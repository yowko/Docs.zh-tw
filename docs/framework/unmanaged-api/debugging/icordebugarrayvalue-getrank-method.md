---
title: ICorDebugArrayValue::GetRank 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type:
- apiref
ms.openlocfilehash: e6401731844f2ce7a1d9fec1c94019f763870fe7
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894985"
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="ef01a-102">ICorDebugArrayValue::GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="ef01a-102">ICorDebugArrayValue::GetRank Method</span></span>
<span data-ttu-id="ef01a-103">取得陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="ef01a-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef01a-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef01a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef01a-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef01a-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="ef01a-106">脫銷這個`ICorDebugArrayValue`物件中維度數目的指標。</span><span class="sxs-lookup"><span data-stu-id="ef01a-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef01a-107">需求</span><span class="sxs-lookup"><span data-stu-id="ef01a-107">Requirements</span></span>  
 <span data-ttu-id="ef01a-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef01a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef01a-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef01a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef01a-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef01a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef01a-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef01a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
