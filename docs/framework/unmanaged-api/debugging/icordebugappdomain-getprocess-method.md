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
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489345"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="bca45-102">ICorDebugAppDomain::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="bca45-102">ICorDebugAppDomain::GetProcess Method</span></span>
<span data-ttu-id="bca45-103">取得包含應用程式定義域的處理序。</span><span class="sxs-lookup"><span data-stu-id="bca45-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca45-104">語法</span><span class="sxs-lookup"><span data-stu-id="bca45-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bca45-105">參數</span><span class="sxs-lookup"><span data-stu-id="bca45-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="bca45-106">[out]ICorDebugProcess 物件，表示處理程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="bca45-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca45-107">需求</span><span class="sxs-lookup"><span data-stu-id="bca45-107">Requirements</span></span>  
 <span data-ttu-id="bca45-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bca45-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca45-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bca45-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bca45-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bca45-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bca45-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca45-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
