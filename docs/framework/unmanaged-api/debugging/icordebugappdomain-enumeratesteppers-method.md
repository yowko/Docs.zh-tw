---
title: ICorDebugAppDomain::EnumerateSteppers 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d326c801ed17fa6fe79f9e464e64844d0016e572
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785148"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="30ef0-102">ICorDebugAppDomain::EnumerateSteppers 方法</span><span class="sxs-lookup"><span data-stu-id="30ef0-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="30ef0-103">應用程式定義域中取得所有作用中的 steppers 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="30ef0-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30ef0-104">語法</span><span class="sxs-lookup"><span data-stu-id="30ef0-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30ef0-105">參數</span><span class="sxs-lookup"><span data-stu-id="30ef0-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="30ef0-106">[out]ICorDebugStepperEnum 物件，應用程式定義域中的所有作用中 steppers 的列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="30ef0-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30ef0-107">需求</span><span class="sxs-lookup"><span data-stu-id="30ef0-107">Requirements</span></span>  
 <span data-ttu-id="30ef0-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30ef0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30ef0-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30ef0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30ef0-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30ef0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30ef0-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30ef0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
