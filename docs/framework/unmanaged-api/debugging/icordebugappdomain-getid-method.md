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
ms.openlocfilehash: 8122f1b5017faac3425d59d12d77f84180134d65
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401625"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="1556d-102">ICorDebugAppDomain::GetId 方法</span><span class="sxs-lookup"><span data-stu-id="1556d-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="1556d-103">取得應用程式定義域的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1556d-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1556d-104">語法</span><span class="sxs-lookup"><span data-stu-id="1556d-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1556d-105">參數</span><span class="sxs-lookup"><span data-stu-id="1556d-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="1556d-106">[out]應用程式定義域的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1556d-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1556d-107">備註</span><span class="sxs-lookup"><span data-stu-id="1556d-107">Remarks</span></span>  
 <span data-ttu-id="1556d-108">應用程式定義域的識別項是包含處理序中唯一的。</span><span class="sxs-lookup"><span data-stu-id="1556d-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1556d-109">需求</span><span class="sxs-lookup"><span data-stu-id="1556d-109">Requirements</span></span>  
 <span data-ttu-id="1556d-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1556d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1556d-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1556d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1556d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1556d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1556d-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1556d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
