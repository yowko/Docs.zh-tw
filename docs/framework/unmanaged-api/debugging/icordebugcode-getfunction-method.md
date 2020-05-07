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
ms.openlocfilehash: 9f785eafa8925324e3bd269ca08a3b1367b74c44
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893581"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="a807d-102">ICorDebugCode::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="a807d-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="a807d-103">取得與這個 "ICorDebugCode" 相關聯的 "ICorDebugFunction"。</span><span class="sxs-lookup"><span data-stu-id="a807d-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a807d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a807d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a807d-105">參數</span><span class="sxs-lookup"><span data-stu-id="a807d-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="a807d-106">脫銷函式位址的指標。</span><span class="sxs-lookup"><span data-stu-id="a807d-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a807d-107">備註</span><span class="sxs-lookup"><span data-stu-id="a807d-107">Remarks</span></span>  
 <span data-ttu-id="a807d-108">`ICorDebugCode`和`ICorDebugFunction`會維護一對一關聯性。</span><span class="sxs-lookup"><span data-stu-id="a807d-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a807d-109">需求</span><span class="sxs-lookup"><span data-stu-id="a807d-109">Requirements</span></span>  
 <span data-ttu-id="a807d-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a807d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a807d-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a807d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a807d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a807d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a807d-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a807d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
