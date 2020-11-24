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
ms.openlocfilehash: 99972c5840645c95b7b349daf2d8ea7173d0cc03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674719"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="443a9-102">ICorDebugCode::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="443a9-102">ICorDebugCode::GetFunction Method</span></span>

<span data-ttu-id="443a9-103">取得與此 "ICorDebugCode" 相關聯的 "ICorDebugFunction"。</span><span class="sxs-lookup"><span data-stu-id="443a9-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="443a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="443a9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="443a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="443a9-105">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="443a9-106">擴展函數位址的指標。</span><span class="sxs-lookup"><span data-stu-id="443a9-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="443a9-107">備註</span><span class="sxs-lookup"><span data-stu-id="443a9-107">Remarks</span></span>  

 <span data-ttu-id="443a9-108">`ICorDebugCode` 並 `ICorDebugFunction` 維護一對一的關聯性。</span><span class="sxs-lookup"><span data-stu-id="443a9-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="443a9-109">需求</span><span class="sxs-lookup"><span data-stu-id="443a9-109">Requirements</span></span>  

 <span data-ttu-id="443a9-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="443a9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="443a9-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="443a9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="443a9-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="443a9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="443a9-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="443a9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
