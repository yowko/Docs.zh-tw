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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169789"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="36978-102">ICorDebug::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="36978-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="36978-103">取得指定的處理序 」 ICorDebugProcess 」 執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="36978-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36978-104">語法</span><span class="sxs-lookup"><span data-stu-id="36978-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36978-105">參數</span><span class="sxs-lookup"><span data-stu-id="36978-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="36978-106">[in]處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="36978-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="36978-107">[out]位址指標`ICorDebugProcess`指定的處理序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="36978-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36978-108">需求</span><span class="sxs-lookup"><span data-stu-id="36978-108">Requirements</span></span>  
 <span data-ttu-id="36978-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36978-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36978-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36978-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36978-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36978-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36978-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36978-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36978-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36978-113">See also</span></span>

- [<span data-ttu-id="36978-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="36978-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
