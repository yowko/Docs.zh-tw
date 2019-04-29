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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd3b977a894f8cb1fc9a866f5a43265d917db513
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645561"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="320e3-102">ICorDebugAssembly2::IsFullyTrusted 方法</span><span class="sxs-lookup"><span data-stu-id="320e3-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="320e3-103">取得值，指出是否將組件是否已授與完全信任執行階段安全性系統。</span><span class="sxs-lookup"><span data-stu-id="320e3-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="320e3-104">Syntax</span></span>  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="320e3-105">參數</span><span class="sxs-lookup"><span data-stu-id="320e3-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="320e3-106">[out]`true`如果組件是否已授與完全信任執行階段安全性系統中; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="320e3-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="320e3-107">備註</span><span class="sxs-lookup"><span data-stu-id="320e3-107">Remarks</span></span>  
 <span data-ttu-id="320e3-108">這個方法會傳回 HRESULT 的 CORDBG_E_NOTREADY 如果組件的安全性原則有尚未解決，亦即，如果組件中的任何程式碼尚未執行。</span><span class="sxs-lookup"><span data-stu-id="320e3-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="320e3-109">需求</span><span class="sxs-lookup"><span data-stu-id="320e3-109">Requirements</span></span>  
 <span data-ttu-id="320e3-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="320e3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="320e3-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="320e3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="320e3-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="320e3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="320e3-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="320e3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
