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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988724"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="b239c-102">ICorDebugFunction::GetCurrentVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="b239c-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="b239c-103">取得最新的編輯這個 ICorDebugFunction 物件所表示的函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b239c-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b239c-104">語法</span><span class="sxs-lookup"><span data-stu-id="b239c-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b239c-105">參數</span><span class="sxs-lookup"><span data-stu-id="b239c-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="b239c-106">[out]是最新的編輯，此函式的版本號碼的整數指標。</span><span class="sxs-lookup"><span data-stu-id="b239c-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b239c-107">備註</span><span class="sxs-lookup"><span data-stu-id="b239c-107">Remarks</span></span>  
 <span data-ttu-id="b239c-108">最新的編輯，此函式的版本號碼可能大於函式本身的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b239c-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="b239c-109">使用任何一種[ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)方法或[icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)方法來擷取函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b239c-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b239c-110">需求</span><span class="sxs-lookup"><span data-stu-id="b239c-110">Requirements</span></span>  
 <span data-ttu-id="b239c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b239c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b239c-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b239c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b239c-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b239c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b239c-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b239c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
