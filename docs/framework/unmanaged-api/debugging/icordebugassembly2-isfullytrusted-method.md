---
title: ICorDebugAssembly2::IsFullyTrusted 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: 8a2a6be0db76f5ee2c7fa67c2038e0a5c845bd0f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719706"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="58188-102">ICorDebugAssembly2::IsFullyTrusted 方法</span><span class="sxs-lookup"><span data-stu-id="58188-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>

<span data-ttu-id="58188-103">取得值，這個值會指出是否已將執行時間安全性系統授與元件完全信任。</span><span class="sxs-lookup"><span data-stu-id="58188-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58188-104">語法</span><span class="sxs-lookup"><span data-stu-id="58188-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58188-105">參數</span><span class="sxs-lookup"><span data-stu-id="58188-105">Parameters</span></span>  

 `pbFullyTrusted`  
 <span data-ttu-id="58188-106">[out] `true` 如果元件已被執行時間安全性系統授與完全信任，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="58188-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58188-107">備註</span><span class="sxs-lookup"><span data-stu-id="58188-107">Remarks</span></span>  

 <span data-ttu-id="58188-108">如果尚未解析元件的安全性原則，則這個方法會傳回 CORDBG_E_NOTREADY 的 HRESULT，也就是如果元件中沒有任何程式碼已經執行。</span><span class="sxs-lookup"><span data-stu-id="58188-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58188-109">需求</span><span class="sxs-lookup"><span data-stu-id="58188-109">Requirements</span></span>  

 <span data-ttu-id="58188-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58188-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58188-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58188-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58188-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58188-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58188-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58188-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
