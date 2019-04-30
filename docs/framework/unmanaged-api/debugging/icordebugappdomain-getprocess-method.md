---
title: ICorDebugAppDomain::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetProcess method [.NET Framework debugging]
ms.assetid: 9d0b9628-a91c-40d0-b9bc-00b34a396b8f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b05c35c810630897e4a7bd28e1cbe8cedefefb1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996199"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="1e75e-102">ICorDebugAppDomain::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="1e75e-102">ICorDebugAppDomain::GetProcess Method</span></span>
<span data-ttu-id="1e75e-103">取得包含應用程式定義域的處理序。</span><span class="sxs-lookup"><span data-stu-id="1e75e-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e75e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1e75e-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e75e-105">參數</span><span class="sxs-lookup"><span data-stu-id="1e75e-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="1e75e-106">[out]ICorDebugProcess 物件，表示處理程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="1e75e-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e75e-107">需求</span><span class="sxs-lookup"><span data-stu-id="1e75e-107">Requirements</span></span>  
 <span data-ttu-id="1e75e-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e75e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e75e-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e75e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e75e-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e75e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e75e-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e75e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
