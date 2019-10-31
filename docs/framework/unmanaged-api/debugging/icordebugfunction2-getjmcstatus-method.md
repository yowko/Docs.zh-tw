---
title: ICorDebugFunction2::GetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 360434fe6e08804d8c80c4ea36d585209cc6761a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137811"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="487db-102">ICorDebugFunction2::GetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="487db-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="487db-103">取得值，指出這個 ICorDebugFunction2 物件所代表的函式是否標示為使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="487db-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="487db-104">語法</span><span class="sxs-lookup"><span data-stu-id="487db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="487db-105">參數</span><span class="sxs-lookup"><span data-stu-id="487db-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="487db-106">脫銷布林值的指標，如果此函式標記為使用者程式碼，則為 `true`。否則，此值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="487db-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="487db-107">備註</span><span class="sxs-lookup"><span data-stu-id="487db-107">Remarks</span></span>  
 <span data-ttu-id="487db-108">如果無法調試此 `ICorDebugFunction2` 所代表的函式，`pbIsJustMyCode` 一律會 `false`。</span><span class="sxs-lookup"><span data-stu-id="487db-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="487db-109">需求</span><span class="sxs-lookup"><span data-stu-id="487db-109">Requirements</span></span>  
 <span data-ttu-id="487db-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="487db-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="487db-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="487db-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="487db-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="487db-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="487db-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="487db-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
