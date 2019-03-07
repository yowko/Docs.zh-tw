---
title: ICorDebugFunction::GetCurrentVersionNumber 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea615eacb30fd4e7a0fd7d730094c2ab4f9dc285
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478475"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="3d502-102">ICorDebugFunction::GetCurrentVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="3d502-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="3d502-103">取得最新的編輯這個 ICorDebugFunction 物件所表示的函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="3d502-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d502-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d502-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d502-105">參數</span><span class="sxs-lookup"><span data-stu-id="3d502-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="3d502-106">[out]是最新的編輯，此函式的版本號碼的整數指標。</span><span class="sxs-lookup"><span data-stu-id="3d502-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d502-107">備註</span><span class="sxs-lookup"><span data-stu-id="3d502-107">Remarks</span></span>  
 <span data-ttu-id="3d502-108">最新的編輯，此函式的版本號碼可能大於函式本身的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="3d502-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="3d502-109">使用任何一種[ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)方法或[icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)方法來擷取函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="3d502-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d502-110">需求</span><span class="sxs-lookup"><span data-stu-id="3d502-110">Requirements</span></span>  
 <span data-ttu-id="3d502-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d502-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d502-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d502-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d502-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d502-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d502-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d502-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
