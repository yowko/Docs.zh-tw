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
ms.openlocfilehash: dd82709064fe7f7d912d93f4b3f0248769f02b9e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894891"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="f5c15-102">ICorDebugAssembly2::IsFullyTrusted 方法</span><span class="sxs-lookup"><span data-stu-id="f5c15-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="f5c15-103">取得值，指出執行時間安全性系統是否已授與元件完全信任。</span><span class="sxs-lookup"><span data-stu-id="f5c15-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c15-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5c15-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5c15-105">參數</span><span class="sxs-lookup"><span data-stu-id="f5c15-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="f5c15-106">脫銷`true`如果元件已被授與執行時間安全性系統的完全信任，則為，否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="f5c15-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5c15-107">備註</span><span class="sxs-lookup"><span data-stu-id="f5c15-107">Remarks</span></span>  
 <span data-ttu-id="f5c15-108">如果尚未解析元件的安全性原則（也就是尚未執行元件中的程式碼），這個方法會傳回 CORDBG_E_NOTREADY 的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="f5c15-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5c15-109">需求</span><span class="sxs-lookup"><span data-stu-id="f5c15-109">Requirements</span></span>  
 <span data-ttu-id="f5c15-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c15-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5c15-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5c15-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5c15-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5c15-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5c15-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5c15-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
