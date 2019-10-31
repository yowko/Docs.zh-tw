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
ms.openlocfilehash: 46d045712e5d3f688ec35d039ccfecba0088037c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134698"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="fa74b-102">ICorDebugAppDomain::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="fa74b-102">ICorDebugAppDomain::GetProcess Method</span></span>
<span data-ttu-id="fa74b-103">取得包含應用程式域的進程。</span><span class="sxs-lookup"><span data-stu-id="fa74b-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa74b-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa74b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa74b-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa74b-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="fa74b-106">脫銷代表進程之 ICorDebugProcess 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="fa74b-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa74b-107">需求</span><span class="sxs-lookup"><span data-stu-id="fa74b-107">Requirements</span></span>  
 <span data-ttu-id="fa74b-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa74b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa74b-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa74b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa74b-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa74b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa74b-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa74b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
