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
ms.openlocfilehash: 90ac981f9b5ee71ca59f76823e7b796471571e4e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895193"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="7fe31-102">ICorDebugAppDomain::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="7fe31-102">ICorDebugAppDomain::GetProcess Method</span></span>
<span data-ttu-id="7fe31-103">取得包含應用程式域的進程。</span><span class="sxs-lookup"><span data-stu-id="7fe31-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe31-104">語法</span><span class="sxs-lookup"><span data-stu-id="7fe31-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fe31-105">參數</span><span class="sxs-lookup"><span data-stu-id="7fe31-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="7fe31-106">脫銷代表進程之 ICorDebugProcess 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="7fe31-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fe31-107">需求</span><span class="sxs-lookup"><span data-stu-id="7fe31-107">Requirements</span></span>  
 <span data-ttu-id="7fe31-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe31-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fe31-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fe31-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fe31-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fe31-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fe31-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fe31-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
