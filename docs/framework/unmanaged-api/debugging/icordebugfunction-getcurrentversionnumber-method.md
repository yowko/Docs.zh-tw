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
ms.openlocfilehash: be66e0e2c9aff788d1003878891b8d64d6353500
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754705"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="071e4-102">ICorDebugFunction::GetCurrentVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="071e4-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="071e4-103">取得最新的編輯這個 ICorDebugFunction 物件所表示的函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="071e4-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="071e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="071e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="071e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="071e4-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="071e4-106">[out]是最新的編輯，此函式的版本號碼的整數指標。</span><span class="sxs-lookup"><span data-stu-id="071e4-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="071e4-107">備註</span><span class="sxs-lookup"><span data-stu-id="071e4-107">Remarks</span></span>  
 <span data-ttu-id="071e4-108">最新的編輯，此函式的版本號碼可能大於函式本身的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="071e4-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="071e4-109">使用任何一種[ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)方法或[icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)方法來擷取函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="071e4-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="071e4-110">需求</span><span class="sxs-lookup"><span data-stu-id="071e4-110">Requirements</span></span>  
 <span data-ttu-id="071e4-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="071e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="071e4-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="071e4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="071e4-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="071e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="071e4-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="071e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
