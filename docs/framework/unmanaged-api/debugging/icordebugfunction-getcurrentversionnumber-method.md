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
ms.openlocfilehash: 61b2de0595ac9330d9bb4e8e2dcbe4591928eb91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413876"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="dc55d-102">ICorDebugFunction::GetCurrentVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="dc55d-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="dc55d-103">取得最新的編輯此 ICorDebugFunction 物件所代表的函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="dc55d-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc55d-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc55d-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc55d-105">參數</span><span class="sxs-lookup"><span data-stu-id="dc55d-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="dc55d-106">[out]指標是最新的編輯，此函式的版本號碼的整數值。</span><span class="sxs-lookup"><span data-stu-id="dc55d-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc55d-107">備註</span><span class="sxs-lookup"><span data-stu-id="dc55d-107">Remarks</span></span>  
 <span data-ttu-id="dc55d-108">此函式的最新編輯的版本號碼可能大於函式本身的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="dc55d-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="dc55d-109">使用[icordebugfunction2:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)方法或[icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)方法來擷取函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="dc55d-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc55d-110">需求</span><span class="sxs-lookup"><span data-stu-id="dc55d-110">Requirements</span></span>  
 <span data-ttu-id="dc55d-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc55d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc55d-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc55d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc55d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc55d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc55d-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc55d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
