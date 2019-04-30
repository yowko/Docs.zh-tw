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
ms.openlocfilehash: b0aefc19ca0c255c9c8ea40fcc12fc5cba1b00f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996251"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="6060c-102">ICorDebugAppDomain::GetId 方法</span><span class="sxs-lookup"><span data-stu-id="6060c-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="6060c-103">取得應用程式定義域的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="6060c-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6060c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6060c-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6060c-105">參數</span><span class="sxs-lookup"><span data-stu-id="6060c-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="6060c-106">[out]應用程式定義域的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="6060c-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6060c-107">備註</span><span class="sxs-lookup"><span data-stu-id="6060c-107">Remarks</span></span>  
 <span data-ttu-id="6060c-108">應用程式定義域的識別項是在包含的程序中唯一的。</span><span class="sxs-lookup"><span data-stu-id="6060c-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6060c-109">需求</span><span class="sxs-lookup"><span data-stu-id="6060c-109">Requirements</span></span>  
 <span data-ttu-id="6060c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6060c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6060c-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6060c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6060c-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6060c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6060c-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6060c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
