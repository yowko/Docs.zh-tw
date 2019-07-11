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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb8917fa401db9424cff168fe0b06ad84065827c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737934"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="35716-102">ICorDebugAppDomain::GetId 方法</span><span class="sxs-lookup"><span data-stu-id="35716-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="35716-103">取得應用程式定義域的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="35716-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35716-104">語法</span><span class="sxs-lookup"><span data-stu-id="35716-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35716-105">參數</span><span class="sxs-lookup"><span data-stu-id="35716-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="35716-106">[out]應用程式定義域的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="35716-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35716-107">備註</span><span class="sxs-lookup"><span data-stu-id="35716-107">Remarks</span></span>  
 <span data-ttu-id="35716-108">應用程式定義域的識別項是在包含的程序中唯一的。</span><span class="sxs-lookup"><span data-stu-id="35716-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35716-109">需求</span><span class="sxs-lookup"><span data-stu-id="35716-109">Requirements</span></span>  
 <span data-ttu-id="35716-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35716-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35716-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35716-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35716-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35716-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35716-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35716-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
