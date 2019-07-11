---
title: ICorDebugChain::IsManaged 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e14ff1cd85810a0b2f9e14c3ab4c8d12d883d17
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745628"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="d8566-102">ICorDebugChain::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="d8566-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="d8566-103">取得值，指出這個鏈結是否正在執行的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8566-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8566-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8566-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8566-105">參數</span><span class="sxs-lookup"><span data-stu-id="d8566-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="d8566-106">[out]`true`如果這個鏈結執行 managed 程式碼; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="d8566-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8566-107">需求</span><span class="sxs-lookup"><span data-stu-id="d8566-107">Requirements</span></span>  
 <span data-ttu-id="d8566-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8566-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8566-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8566-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8566-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8566-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8566-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8566-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
