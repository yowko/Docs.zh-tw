---
title: ICorDebug::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcb869bed71be05e0450580b50dfa9f2a0fca525
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996290"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="2513a-102">ICorDebug::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="2513a-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="2513a-103">取得指定的處理序 」 ICorDebugProcess 」 執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="2513a-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2513a-104">語法</span><span class="sxs-lookup"><span data-stu-id="2513a-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2513a-105">參數</span><span class="sxs-lookup"><span data-stu-id="2513a-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="2513a-106">[in]處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="2513a-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="2513a-107">[out]位址指標`ICorDebugProcess`指定的處理序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2513a-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2513a-108">需求</span><span class="sxs-lookup"><span data-stu-id="2513a-108">Requirements</span></span>  
 <span data-ttu-id="2513a-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2513a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2513a-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2513a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2513a-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2513a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2513a-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2513a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2513a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2513a-113">See also</span></span>

- [<span data-ttu-id="2513a-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="2513a-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
