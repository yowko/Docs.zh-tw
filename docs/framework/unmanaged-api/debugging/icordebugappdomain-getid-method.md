---
title: ICorDebugAppDomain::GetId 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
ms.openlocfilehash: 63346c679efc083dea9ab0eaa4f983a5308695f8
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895245"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="2e74f-102">ICorDebugAppDomain::GetId 方法</span><span class="sxs-lookup"><span data-stu-id="2e74f-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="2e74f-103">取得應用程式域的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="2e74f-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e74f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e74f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e74f-105">參數</span><span class="sxs-lookup"><span data-stu-id="2e74f-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="2e74f-106">脫銷應用程式域的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="2e74f-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e74f-107">備註</span><span class="sxs-lookup"><span data-stu-id="2e74f-107">Remarks</span></span>  
 <span data-ttu-id="2e74f-108">應用程式域的識別碼在包含的進程內是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2e74f-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e74f-109">需求</span><span class="sxs-lookup"><span data-stu-id="2e74f-109">Requirements</span></span>  
 <span data-ttu-id="2e74f-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2e74f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e74f-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e74f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e74f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e74f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e74f-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e74f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
