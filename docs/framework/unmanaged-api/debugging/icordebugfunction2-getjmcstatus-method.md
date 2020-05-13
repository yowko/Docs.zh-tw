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
ms.openlocfilehash: 56dc5f87b32b3aaa0bfbb69541d5a01ae26606ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213227"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="3d7b6-102">ICorDebugFunction2::GetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="3d7b6-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="3d7b6-103">取得值，指出這個 ICorDebugFunction2 物件所代表的函式是否標示為使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d7b6-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d7b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d7b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d7b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="3d7b6-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="3d7b6-106">脫銷布林值的指標 `true` ，如果此函式標示為使用者程式碼，則為，否則值為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="3d7b6-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d7b6-107">備註</span><span class="sxs-lookup"><span data-stu-id="3d7b6-107">Remarks</span></span>  
 <span data-ttu-id="3d7b6-108">如果無法調試這個所表示的函式 `ICorDebugFunction2` ， `pbIsJustMyCode` 則一律為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="3d7b6-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d7b6-109">需求</span><span class="sxs-lookup"><span data-stu-id="3d7b6-109">Requirements</span></span>  
 <span data-ttu-id="3d7b6-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d7b6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d7b6-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d7b6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d7b6-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d7b6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d7b6-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d7b6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
